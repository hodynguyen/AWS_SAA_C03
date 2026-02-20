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
