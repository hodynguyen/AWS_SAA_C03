[Vietnamese Below](#vietnamese-version)

# Decoupling Applications: SQS, SNS, Kinesis, Active MQ

## 1. Introduction to Messaging

When applications need to communicate with each other, there are two main patterns:

### Synchronous Communication
*   Application A **directly calls** Application B and **waits** for a response.
*   Problem: If Application B is overwhelmed or goes down, Application A is also affected.
*   Example: Web server directly calling a database or another API.

### Asynchronous / Event-Based Communication
*   Application A sends a **message** to a **middleware** (queue/topic), and Application B processes it independently.
*   Applications are **decoupled** — they don't know about each other.
*   If one component fails, others continue working.

### AWS Messaging Services
*   **SQS** — Queue model (producer sends, consumer polls).
*   **SNS** — Pub/Sub model (publisher sends, subscribers receive).
*   **Kinesis** — Real-time streaming model (producers stream, consumers process in real-time).

### Why Decouple?
*   **Scalability**: Scale each component independently.
*   **Reliability**: If one part fails, the rest keeps working.
*   **Flexibility**: Change or replace components without affecting others.

## 2. Amazon SQS - Standard Queues

Amazon SQS (Simple Queue Service) is a **fully managed message queue** service. It's one of the oldest AWS services.

### How It Works
*   **Producers** send messages to the queue.
*   **Consumers** poll the queue, process messages, then **delete** them.
*   Messages are **persisted** in the queue until processed or expired.
*   Multiple producers and multiple consumers can work with the same queue.

### Standard Queue Characteristics
*   **Unlimited throughput**: No limit on number of messages per second.
*   **Unlimited messages**: No limit on number of messages in queue.
*   **Default retention**: **4 days** (max **14 days**).
*   **Low latency**: < 10ms on publish and receive.
*   **Max message size**: **256KB** per message.
*   **Delivery**: **At-least-once** delivery (messages can be delivered more than once).
*   **Ordering**: **Best-effort ordering** (no guarantee of order).

### Producing Messages
*   Messages sent using the **SendMessage API** (SDK).
*   Message body: up to **256KB** (string).
*   Can include **message attributes** (metadata) and **delay** settings.
*   Producer gets back: message ID, MD5 hash of body.

### Consuming Messages
*   Consumers (EC2 instances, Lambda, on-premises servers, etc.) **poll** the queue.
*   Can receive up to **10 messages** at a time.
*   After processing, consumer **deletes** the message using the **DeleteMessage API**.
*   If not deleted within the **Visibility Timeout**, the message becomes visible again for other consumers.

### Message Visibility Timeout
*   After a consumer polls a message, it becomes **invisible** to other consumers for the **Visibility Timeout** period.
*   **Default**: **30 seconds**. Configurable: 0 seconds to **12 hours**.
*   If processing takes longer than the timeout → message becomes visible again → **processed twice** (duplicate).
*   Consumer can call **ChangeMessageVisibility API** to extend the timeout while still processing.
*   **Too high**: If consumer crashes, it takes a long time for the message to be reprocessed.
*   **Too low**: Risk of duplicate processing.

### Long Polling
*   When a consumer polls and the queue is empty, it can **wait** for messages to arrive instead of returning immediately.
*   **Reduces API calls** (saves cost) and **decreases latency**.
*   Wait time: **1 to 20 seconds** (20s preferred).
*   Enabled at **queue level** or at **API level** (`WaitTimeSeconds`).
*   **Long Polling > Short Polling** (always prefer Long Polling in exams).

### SQS + Auto Scaling Group (ASG)
*   Common architecture pattern:
    1.  Producers send messages to SQS queue.
    2.  EC2 instances in an ASG consume messages.
    3.  CloudWatch monitors **ApproximateNumberOfMessages** (queue length).
    4.  CloudWatch Alarm triggers ASG to **scale out/in** based on queue depth.
*   **Use Case**: Decouple frontend from backend processing. Frontend sends to SQS, backend ASG scales based on load.

### Exam Tips
*   SQS Standard = **unlimited throughput**, **at-least-once delivery**, **best-effort ordering**.
*   Max message size = **256KB**, retention = **4-14 days**.
*   **Visibility Timeout**: Default 30s, use ChangeMessageVisibility API to extend.
*   **Long Polling**: Always preferred, 1-20s wait, reduces API calls.
*   SQS + ASG pattern: Scale consumers based on **queue depth** (ApproximateNumberOfMessages).

## 3. SQS - FIFO Queues

FIFO = **First In First Out** — messages are processed in the **exact order** they were sent.

### Key Characteristics
*   **Ordering**: **Guaranteed order** of messages (FIFO).
*   **Delivery**: **Exactly-once** delivery (no duplicates).
*   **Throughput**: Limited — **300 msg/s** without batching, **3000 msg/s** with batching.
*   **Queue name**: Must end with `.fifo` suffix (e.g., `my-queue.fifo`).

### Deduplication
*   Prevents sending the **same message twice** within a **5-minute deduplication interval**.
*   Two methods:
    *   **Content-based**: SHA-256 hash of message body.
    *   **Message Deduplication ID**: Explicitly provide a deduplication ID.

### Message Grouping
*   Messages with the same **MessageGroupID** are processed in order **within that group**.
*   Each Group ID can have a **different consumer** — enables parallel processing while maintaining order per group.
*   If you specify only **one GroupID**, all messages are consumed in strict order by one consumer.
*   If you specify **different GroupIDs**, you get parallel consumption across groups (ordering only within each group).

### Standard vs FIFO Comparison

| Feature | Standard | FIFO |
|---|---|---|
| **Throughput** | Unlimited | 300/3000 msg/s |
| **Ordering** | Best-effort | Guaranteed (FIFO) |
| **Delivery** | At-least-once | Exactly-once |
| **Deduplication** | No | Yes (5-min window) |
| **Queue name** | Any | Must end with `.fifo` |

### Exam Tips
*   Need **ordering** → **SQS FIFO**.
*   Need **exactly-once** → **SQS FIFO**.
*   FIFO throughput is **limited** (300/3000 msg/s).
*   **MessageGroupID** = ordering within a group + parallel processing across groups.

## 4. Amazon SNS (Simple Notification Service)

Amazon SNS is a **fully managed Pub/Sub messaging service**. One message is sent to a **topic**, and all **subscribers** receive it.

### How It Works
*   **Publisher** sends a message to an **SNS Topic**.
*   All **subscribers** to that topic receive the message.
*   Up to **12,500,000 subscriptions** per topic.
*   Up to **100,000 topics**.

### Subscribers
*   **SQS** queues (most common).
*   **Lambda** functions.
*   **Kinesis Data Firehose**.
*   **HTTP/HTTPS** endpoints.
*   **Emails**, **SMS**, **Mobile push notifications**.

### How to Publish
*   **Topic Publish** (SDK): Create a topic, create subscriptions, publish to topic.
*   **Direct Publish** (mobile SDK): Publish directly to a platform endpoint (mobile push).

### SNS + SQS Fan Out Pattern
*   **Problem**: You need to send the same message to **multiple SQS queues**.
*   **Solution**: Push once to SNS topic, and have **multiple SQS queues subscribe** to the topic.
*   **Benefits**:
    *   Fully decoupled, no data loss.
    *   Add more SQS subscribers over time.
    *   SQS allows data persistence, delayed processing, retries.
*   **Requirement**: SQS queue **Access Policy** must allow SNS to write to it.
*   **Use Cases**:
    *   S3 Event → SNS → multiple SQS (only one S3 event rule per prefix).
    *   SNS → SQS → different processing pipelines.

### SNS - Message Filtering
*   **JSON policy** attached to SNS subscriptions to **filter** which messages a subscriber receives.
*   Without filtering, subscribers receive **all messages**.
*   Example: Order topic → Filter "placed" to SQS-A, filter "cancelled" to SQS-B.

### SNS - FIFO Topics
*   Similar to SQS FIFO: **ordering** by Message Group ID, **deduplication**.
*   **Subscribers can only be SQS FIFO queues**.
*   Throughput same as SQS FIFO (limited).

### Exam Tips
*   SNS = **Pub/Sub**, one message to many receivers.
*   **Fan Out**: SNS + SQS = send to multiple queues at once.
*   **Message Filtering**: JSON filter policy on subscriptions.
*   SNS FIFO → only SQS FIFO subscribers.
*   S3 events can only have **one rule per event type/prefix** → use **Fan Out** to send to multiple destinations.

## 5. Amazon Kinesis

Amazon Kinesis makes it easy to **collect, process, and analyze real-time streaming data** at any scale.

### Kinesis Services

#### A. Kinesis Data Streams
*   **Capture and store** streaming data for real-time processing.
*   Made up of **Shards** (each shard = 1MB/s in, 2MB/s out).
*   **Producers**: Applications, SDK, Kinesis Agent, IoT devices.
*   **Consumers**: EC2, Lambda, Kinesis Data Firehose, Kinesis Data Analytics.
*   **Retention**: **1 day** (default) to **365 days**.
*   Data can be **replayed** (re-processed) — data is not deleted after consumption.
*   Data is **immutable** — once inserted, cannot be deleted.
*   **Ordering**: Messages with the same **Partition Key** go to the same shard (ordering per shard).
*   **Provisioned mode**: Choose number of shards, pay per shard/hour.
*   **On-demand mode**: Auto-scales, pay per stream/hour + data in/out.

#### B. Kinesis Data Firehose
*   **Load streaming data** into destinations (fully managed, serverless, auto-scaling).
*   **Near real-time** (60-second buffer or 1MB buffer).
*   Destinations:
    *   **AWS**: S3, Redshift (via S3 COPY), OpenSearch.
    *   **3rd party**: Splunk, Datadog, New Relic, MongoDB.
    *   **Custom HTTP endpoint**.
*   Can **transform data** using Lambda before delivery.
*   Supports **data format conversion** (e.g., JSON → Parquet).
*   **No data storage** — no replay capability.

#### C. Kinesis Data Analytics
*   Analyze streaming data in real-time using **SQL** or **Apache Flink**.
*   Sources: Kinesis Data Streams, Kinesis Data Firehose.
*   Fully managed, auto-scaling.
*   Use Cases: Time-series analytics, real-time dashboards, real-time metrics.

### SQS vs SNS vs Kinesis

| Feature | SQS | SNS | Kinesis Data Streams |
|---|---|---|---|
| **Model** | Queue (pull) | Pub/Sub (push) | Stream (pull) |
| **Consumers** | Pull messages | Push to subscribers | Pull from shards |
| **Persistence** | Until consumed/expired | No persistence | 1-365 days |
| **Replay** | No | No | **Yes** |
| **Ordering** | FIFO only | FIFO only | Per shard (Partition Key) |
| **Throughput** | Unlimited (Standard) | Depends on subscribers | Per shard (1MB/s in) |
| **Use Case** | Decouple apps, async processing | Fan out notifications | Real-time streaming, analytics |

### Exam Tips
*   **Kinesis Data Streams** = real-time data streaming with **retention and replay**.
*   **Kinesis Data Firehose** = **near real-time delivery** to S3/Redshift/OpenSearch (no replay).
*   **Kinesis Data Analytics** = SQL/Flink on streaming data.
*   Data Streams: ordering per shard via **Partition Key**.
*   If you see "real-time" + "replay" + "streaming" → **Kinesis Data Streams**.
*   If you see "load streaming data to S3" → **Kinesis Data Firehose**.

---

<a id="vietnamese-version"></a>

# Decoupling Applications: SQS, SNS, Kinesis, Active MQ

## 1. Giới thiệu về Messaging

Khi các ứng dụng cần giao tiếp với nhau, có hai mô hình chính:

### Giao tiếp đồng bộ (Synchronous)
*   Ứng dụng A **gọi trực tiếp** ứng dụng B và **chờ** phản hồi.
*   Vấn đề: Nếu ứng dụng B quá tải hoặc sập, ứng dụng A cũng bị ảnh hưởng.
*   Ví dụ: Web server gọi trực tiếp database hoặc API khác.

### Giao tiếp bất đồng bộ / Event-Based (Asynchronous)
*   Ứng dụng A gửi **message** vào **middleware** (queue/topic), ứng dụng B xử lý độc lập.
*   Các ứng dụng được **tách rời (decoupled)** — không biết về nhau.
*   Nếu một thành phần lỗi, các thành phần khác vẫn hoạt động.

### Các dịch vụ Messaging của AWS
*   **SQS** — Mô hình Queue (producer gửi, consumer lấy).
*   **SNS** — Mô hình Pub/Sub (publisher gửi, subscribers nhận).
*   **Kinesis** — Mô hình Streaming thời gian thực (producers stream, consumers xử lý real-time).

### Tại sao cần Decouple?
*   **Khả năng mở rộng**: Scale từng thành phần độc lập.
*   **Độ tin cậy**: Nếu một phần lỗi, phần còn lại vẫn hoạt động.
*   **Linh hoạt**: Thay đổi hoặc thay thế thành phần mà không ảnh hưởng phần khác.

## 2. Amazon SQS - Standard Queues

Amazon SQS (Simple Queue Service) là dịch vụ **hàng đợi message được quản lý hoàn toàn**. Là một trong những dịch vụ lâu đời nhất của AWS.

### Cách hoạt động
*   **Producers** gửi messages vào queue.
*   **Consumers** poll queue, xử lý messages, rồi **xóa** chúng.
*   Messages được **lưu trữ** trong queue cho đến khi xử lý xong hoặc hết hạn.
*   Nhiều producers và nhiều consumers có thể làm việc với cùng queue.

### Đặc điểm Standard Queue
*   **Throughput không giới hạn**: Không limit số messages/giây.
*   **Số lượng message không giới hạn**: Không limit số messages trong queue.
*   **Retention mặc định**: **4 ngày** (tối đa **14 ngày**).
*   **Độ trễ thấp**: < 10ms khi publish và receive.
*   **Kích thước message tối đa**: **256KB**.
*   **Phân phối**: **At-least-once** (messages có thể được gửi nhiều lần).
*   **Thứ tự**: **Best-effort ordering** (không đảm bảo thứ tự).

### Gửi Messages (Producing)
*   Gửi qua **SendMessage API** (SDK).
*   Message body: tối đa **256KB** (string).
*   Có thể gửi kèm **message attributes** (metadata) và cài đặt **delay**.

### Nhận Messages (Consuming)
*   Consumers (EC2, Lambda, servers on-prem, v.v.) **poll** queue.
*   Nhận tối đa **10 messages** một lần.
*   Sau khi xử lý, consumer **xóa** message bằng **DeleteMessage API**.
*   Nếu không xóa trong **Visibility Timeout**, message xuất hiện lại cho consumers khác.

### Message Visibility Timeout
*   Sau khi consumer poll message, nó trở nên **vô hình** với consumers khác trong thời gian **Visibility Timeout**.
*   **Mặc định**: **30 giây**. Cấu hình: 0 giây đến **12 giờ**.
*   Nếu xử lý lâu hơn timeout → message xuất hiện lại → **xử lý trùng** (duplicate).
*   Consumer có thể gọi **ChangeMessageVisibility API** để gia hạn timeout.
*   **Quá cao**: Nếu consumer crash, phải chờ lâu.
*   **Quá thấp**: Rủi ro xử lý trùng.

### Long Polling
*   Khi consumer poll và queue trống, có thể **chờ** messages đến thay vì trả về ngay.
*   **Giảm API calls** (tiết kiệm chi phí) và **giảm độ trễ**.
*   Thời gian chờ: **1 đến 20 giây** (20s là tốt nhất).
*   Bật tại **queue level** hoặc **API level** (`WaitTimeSeconds`).
*   **Long Polling > Short Polling** (luôn chọn Long Polling trong thi).

### SQS + Auto Scaling Group (ASG)
*   Pattern kiến trúc phổ biến:
    1.  Producers gửi messages vào SQS queue.
    2.  EC2 instances trong ASG consume messages.
    3.  CloudWatch giám sát **ApproximateNumberOfMessages** (độ dài queue).
    4.  CloudWatch Alarm trigger ASG **scale out/in** dựa trên queue depth.
*   **Use Case**: Tách rời frontend và backend. Frontend gửi vào SQS, backend ASG scale theo tải.

### Exam Tips
*   SQS Standard = **throughput không giới hạn**, **at-least-once**, **best-effort ordering**.
*   Kích thước message = **256KB**, retention = **4-14 ngày**.
*   **Visibility Timeout**: Mặc định 30s, dùng ChangeMessageVisibility API để gia hạn.
*   **Long Polling**: Luôn ưu tiên, 1-20s chờ, giảm API calls.
*   SQS + ASG: Scale consumers dựa trên **queue depth** (ApproximateNumberOfMessages).

## 3. SQS - FIFO Queues

FIFO = **First In First Out** — messages được xử lý theo **đúng thứ tự** gửi.

### Đặc điểm chính
*   **Thứ tự**: **Đảm bảo thứ tự** messages (FIFO).
*   **Phân phối**: **Exactly-once** (không trùng lặp).
*   **Throughput**: Giới hạn — **300 msg/s** không batch, **3000 msg/s** có batch.
*   **Tên queue**: Phải kết thúc bằng `.fifo` (ví dụ: `my-queue.fifo`).

### Deduplication (Chống trùng lặp)
*   Ngăn gửi **cùng message hai lần** trong khoảng **5 phút**.
*   Hai cách:
    *   **Content-based**: SHA-256 hash của message body.
    *   **Message Deduplication ID**: Cung cấp deduplication ID rõ ràng.

### Message Grouping (Phân nhóm)
*   Messages có cùng **MessageGroupID** được xử lý theo thứ tự **trong nhóm đó**.
*   Mỗi Group ID có thể có **consumer khác nhau** — cho phép xử lý song song với thứ tự trong nhóm.
*   Nếu chỉ dùng **một GroupID**, tất cả messages được một consumer xử lý tuần tự.
*   Nếu dùng **nhiều GroupIDs**, có thể xử lý song song giữa các nhóm.

### Standard vs FIFO

| Đặc điểm | Standard | FIFO |
|---|---|---|
| **Throughput** | Không giới hạn | 300/3000 msg/s |
| **Thứ tự** | Best-effort | Đảm bảo (FIFO) |
| **Phân phối** | At-least-once | Exactly-once |
| **Chống trùng** | Không | Có (5 phút) |
| **Tên queue** | Bất kỳ | Phải kết thúc `.fifo` |

### Exam Tips
*   Cần **thứ tự** → **SQS FIFO**.
*   Cần **exactly-once** → **SQS FIFO**.
*   FIFO throughput **giới hạn** (300/3000 msg/s).
*   **MessageGroupID** = thứ tự trong nhóm + xử lý song song giữa các nhóm.

## 4. Amazon SNS (Simple Notification Service)

Amazon SNS là dịch vụ **Pub/Sub messaging được quản lý hoàn toàn**. Một message gửi đến **topic**, tất cả **subscribers** đều nhận được.

### Cách hoạt động
*   **Publisher** gửi message đến **SNS Topic**.
*   Tất cả **subscribers** của topic đều nhận message.
*   Lên đến **12,500,000 subscriptions** mỗi topic.
*   Lên đến **100,000 topics**.

### Subscribers
*   **SQS** queues (phổ biến nhất).
*   **Lambda** functions.
*   **Kinesis Data Firehose**.
*   **HTTP/HTTPS** endpoints.
*   **Email**, **SMS**, **Mobile push notifications**.

### Cách Publish
*   **Topic Publish** (SDK): Tạo topic, tạo subscriptions, publish lên topic.
*   **Direct Publish** (mobile SDK): Publish trực tiếp đến platform endpoint (mobile push).

### SNS + SQS Fan Out Pattern
*   **Vấn đề**: Cần gửi cùng message đến **nhiều SQS queues**.
*   **Giải pháp**: Push một lần vào SNS topic, **nhiều SQS queues subscribe** topic đó.
*   **Lợi ích**:
    *   Hoàn toàn decoupled, không mất dữ liệu.
    *   Thêm SQS subscribers bất cứ lúc nào.
    *   SQS cho phép lưu trữ, xử lý trễ, retry.
*   **Yêu cầu**: SQS queue **Access Policy** phải cho phép SNS ghi vào.
*   **Use Cases**:
    *   S3 Event → SNS → nhiều SQS (chỉ 1 S3 event rule mỗi prefix).
    *   SNS → SQS → các pipeline xử lý khác nhau.

### SNS - Message Filtering (Lọc messages)
*   **JSON policy** gắn vào SNS subscriptions để **lọc** messages nào subscriber nhận.
*   Không có filter, subscribers nhận **tất cả messages**.
*   Ví dụ: Order topic → Filter "placed" vào SQS-A, filter "cancelled" vào SQS-B.

### SNS - FIFO Topics
*   Giống SQS FIFO: **thứ tự** theo Message Group ID, **deduplication**.
*   **Subscribers chỉ có thể là SQS FIFO queues**.
*   Throughput giống SQS FIFO (giới hạn).

### Exam Tips
*   SNS = **Pub/Sub**, một message đến nhiều receivers.
*   **Fan Out**: SNS + SQS = gửi đến nhiều queues cùng lúc.
*   **Message Filtering**: JSON filter policy trên subscriptions.
*   SNS FIFO → chỉ SQS FIFO subscribers.
*   S3 events chỉ có **một rule per event type/prefix** → dùng **Fan Out** để gửi nhiều đích.

## 5. Amazon Kinesis

Amazon Kinesis giúp **thu thập, xử lý, và phân tích dữ liệu streaming thời gian thực** ở mọi quy mô.

### Các dịch vụ Kinesis

#### A. Kinesis Data Streams
*   **Thu thập và lưu trữ** dữ liệu streaming để xử lý real-time.
*   Gồm các **Shards** (mỗi shard = 1MB/s vào, 2MB/s ra).
*   **Producers**: Ứng dụng, SDK, Kinesis Agent, thiết bị IoT.
*   **Consumers**: EC2, Lambda, Kinesis Data Firehose, Kinesis Data Analytics.
*   **Retention**: **1 ngày** (mặc định) đến **365 ngày**.
*   Dữ liệu có thể **replay** (xử lý lại) — dữ liệu không bị xóa sau khi consume.
*   Dữ liệu là **immutable** — khi đã ghi vào, không thể xóa.
*   **Thứ tự**: Messages có cùng **Partition Key** vào cùng shard (thứ tự theo shard).
*   **Provisioned mode**: Chọn số shards, trả theo shard/giờ.
*   **On-demand mode**: Tự động scale, trả theo stream/giờ + data in/out.

#### B. Kinesis Data Firehose
*   **Tải dữ liệu streaming** vào các đích (fully managed, serverless, tự động scale).
*   **Gần thời gian thực** (buffer 60 giây hoặc 1MB).
*   Đích:
    *   **AWS**: S3, Redshift (qua S3 COPY), OpenSearch.
    *   **Bên thứ 3**: Splunk, Datadog, New Relic, MongoDB.
    *   **HTTP endpoint tùy chỉnh**.
*   Có thể **biến đổi dữ liệu** bằng Lambda trước khi gửi.
*   Hỗ trợ **chuyển đổi format** (ví dụ: JSON → Parquet).
*   **Không lưu dữ liệu** — không replay được.

#### C. Kinesis Data Analytics
*   Phân tích dữ liệu streaming real-time bằng **SQL** hoặc **Apache Flink**.
*   Nguồn: Kinesis Data Streams, Kinesis Data Firehose.
*   Fully managed, tự động scale.
*   Use Cases: Phân tích chuỗi thời gian, dashboard real-time, metrics real-time.

### SQS vs SNS vs Kinesis

| Đặc điểm | SQS | SNS | Kinesis Data Streams |
|---|---|---|---|
| **Mô hình** | Queue (pull) | Pub/Sub (push) | Stream (pull) |
| **Consumers** | Pull messages | Push đến subscribers | Pull từ shards |
| **Lưu trữ** | Cho đến khi consumed/hết hạn | Không lưu | 1-365 ngày |
| **Replay** | Không | Không | **Có** |
| **Thứ tự** | Chỉ FIFO | Chỉ FIFO | Theo shard (Partition Key) |
| **Throughput** | Không giới hạn (Standard) | Theo subscribers | Theo shard (1MB/s vào) |
| **Use Case** | Decouple apps, xử lý bất đồng bộ | Fan out notifications | Streaming real-time, analytics |

### Exam Tips
*   **Kinesis Data Streams** = streaming real-time với **retention và replay**.
*   **Kinesis Data Firehose** = **gần real-time** đến S3/Redshift/OpenSearch (không replay).
*   **Kinesis Data Analytics** = SQL/Flink trên dữ liệu streaming.
*   Data Streams: thứ tự theo shard qua **Partition Key**.
*   Thấy "real-time" + "replay" + "streaming" → **Kinesis Data Streams**.
*   Thấy "load streaming data to S3" → **Kinesis Data Firehose**.
