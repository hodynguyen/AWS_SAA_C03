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
