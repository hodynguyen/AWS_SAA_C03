[Vietnamese Below](#vietnamese-version)

# Advanced Amazon S3

## 1. S3 Lifecycle Rules (Data Lifecycle)

Lifecycle Rules help you **automate** moving data between Storage Classes or deleting old data to **save costs**.

2 Main Actions:

**1. Transition Actions:**
*   Move objects to a cheaper storage class after a certain period.
*   *Example*:
    *   After 30 days: Move from `Standard` -> `Standard-IA`.
    *   After 90 days: Move to `Glacier` for long-term archiving.

**2. Expiration Actions:**
*   Automatically delete objects after a specific period.
*   *Example*:
    *   Delete access logs after 365 days.
    *   Delete old versions of files after 60 days (if Versioning is enabled).
    *   Delete Incomplete Multi-part uploads after 7 days (Very important to avoid garbage costs).

**Exam Tips & Important Rules:**

1.  **Transition Flow (Waterfall):**
    *   `Standard` -> `Standard-IA` -> `Intelligent-Tiering` -> `One Zone-IA` -> `Glacier` -> `Deep Archive`.
    *   You can transition directly from `Standard` to any class, but **cannot** transition back from Archive (Glacier/Deep Archive) to Standard via Lifecycle Rule (must Restore manually).

2.  **Time Constraints:**
    *   **Standard-IA / One Zone-IA**: Object must exist for at least **30 days** in Standard before transition.
    *   **Glacier**: Usually requires a minimum number of days before transition from Standard for optimization.

3.  **Filter by Size:**
    *   **Do not transition small files (< 128KB)** to `Standard-IA` or `Glacier`.
    *   Reason: IA/Glacier classes have a minimum object size charge of 128KB. Moving a 10KB file to IA will be charged as 128KB -> **Cost inefficient**.

4.  **Scope:**
    *   Can apply rule to **whole bucket** OR **a subset** (using Prefix or Tags).
    *   *Example*: Only transition files in `/logs` folder or files with tag `Department=HR`.

## 2. S3 Requester Pays

*   **Default**: **Bucket Owner** pays for all costs (storage + data transfer).
*   **Requester Pays Model**:
    *   **Who pays?**: The **Requester** pays for request and data transfer costs. Bucket owner only pays for storage.
    *   **Use Case**: Sharing large datasets (Big Data) with the community or customers without bearing the huge data transfer costs.
*   **Technical Requirements**:
    *   Requester must be an **Authenticated AWS User** (No Anonymous access).
    *   Requester must include `x-amz-request-payer` header in the request, otherwise access is denied (403).

## 3. S3 Event Notifications

*   **Concept**: S3 can send notifications when certain events happen in your bucket (e.g., New object created, Object removed, Object restored, Replication events).
*   **Destinations**:
    *   **SNS (Simple Notification Service)**: Send to a Topic (e.g., email, SMS).
    *   **SQS (Simple Queue Service)**: Send to a Queue (for decoupling/processing).
    *   **Lambda Function**: Trigger code execution (e.g., generate thumbnail when image is uploaded).
*   **Amazon EventBridge**: Newer integration, allows for advanced filtering and routing to many more destinations (over 18 AWS services).
*   **Permissions**: The destination resource (SNS/SQS/Lambda) must have an **Access Policy** allowing S3 to publish messages to it.

## 4. S3 Performance

*   **Baseline Performance**:
    *   Automatically scales to high request rates.
    *   Latency: 100-200 ms.
    *   3,500 PUT/COPY/POST/DELETE per second per prefix.
    *   5,500 GET/HEAD per second per prefix.
*   **Optimization Techniques**:
    *   **Multi-Part Upload**: Required for files > 5GB, recommended for files > 100MB. Uploads parts in parallel (faster, retryable).
    *   **S3 Transfer Acceleration**: Uses AWS Edge Locations to speed up uploads over long distances (uploads to Edge -> AWS backbone -> S3 Bucket).
    *   **S3 Byte-Range Fetches**: Parallelize GETs by requesting specific byte ranges. Speed up downloads.

## 5. S3 Batch Operations

*   **Purpose**: Perform bulk actions on billions of objects with a single API request or console click.
*   **How it works**:
    1.  Provide a list of objects (S3 Inventory or CSV).
    2.  Select operation (Replace tags, Copy, Restore from Glacier, Invoke Lambda).
    3.  S3 manages retries, progress tracking, and completion reports.
*   **Use Cases**: Modifying object metadata, copying objects between buckets, encrypting unencrypted objects.

## 6. S3 Storage Lens

*   **Concept**: An analytics dashboard to gain visibility into object storage usage and activity.
*   **Scope**: Can view across Organization, Region, Account, or Bucket level.
*   **Benefits**:
    *   **Cost Efficiency**: Identify coldest buckets, incomplete multipart uploads, etc.
    *   **Data Protection**: Check if buckets are encrypted or replicated.
    *   **default dashboard**: Free, pre-configured.

---

<a id="vietnamese-version"></a>

# Advanced Amazon S3

## 1. S3 Lifecycle Rules (Vòng đời dữ liệu)

Lifecycle Rules giúp bạn **tự động hóa** việc di chuyển dữ liệu giữa các lớp lưu trữ (Storage Classes) hoặc xóa dữ liệu cũ để **tiết kiệm chi phí**.

Có 2 loại hành động chính (Actions):

**1. Transition Actions (Chuyển đổi):**
*   Chuyển objects sang lớp lưu trữ rẻ hơn sau một khoảng thời gian.
*   *Ví dụ*:
    *   Sau 30 ngày: Move từ `Standard` -> `Standard-IA`.
    *   Sau 90 ngày: Move sang `Glacier` để lưu trữ lâu dài.

**2. Expiration Actions (Hết hạn/Xóa):**
*   Tự động xóa objects sau một thời gian nhất định.
*   *Ví dụ*:
    *   Xóa access logs sau 365 ngày.
    *   Xóa các phiên bản cũ (old versions) của file sau 60 ngày (nếu bật Versioning).
    *   Xóa các bản upload bị lỗi (Incomplete Multi-part uploads) sau 7 ngày (Rất quan trọng để không bị tính tiền rác).

**📝 Các quy tắc & Lưu ý quan trọng (Exam Tips):**

1.  **Transition Flow (Dòng chảy):**
    *   Dữ liệu thường chảy theo hướng "Thác nước": `Standard` -> `Standard-IA` -> `Intelligent-Tiering` -> `One Zone-IA` -> `Glacier` -> `Deep Archive`.
    *   Bạn có thể chuyển thẳng từ `Standard` sang bất kỳ lớp nào, nhưng **không thể** chuyển ngược lại từ Archive (Glacier/Deep Archive) về Standard bằng Lifecycle Rule (phải Restore thủ công).

2.  **Giới hạn thời gian (Time Constraints):**
    *   **Standard-IA / One Zone-IA**: Object phải tồn tại ít nhất **30 ngày** trong Standard mới được chuyển sang.
    *   **Glacier**: Object phải ở các lớp IA ít nhất bao lâu đó (tùy config), nhưng thường là chuyển từ Standard -> Glacier cần ít nhất số ngày nhất định để tối ưu.

3.  **Kích thước file (Filter by Size):**
    *   **Đừng chuyển file nhỏ (< 128KB)** sang `Standard-IA` hoặc `Glacier`.
    *   Lý do: Các lớp IA/Glacier tính phí object tối thiểu là 128KB. Ví dụ file 10KB update sang IA sẽ bị tính tiền như file 128KB -> **Lỗ tiền**.

4.  **Scope (Phạm vi):**
    *   Có thể apply rule cho **toàn bộ bucket** HOẶC **một phần** (dùng Prefix hoặc Tags).
    *   *Ví dụ*: Chỉ chuyển các file trong folder `/logs` hoặc các file có tag `Department=HR`.

## 2. S3 Requester Pays (Người gửi trả tiền)

*   **Mặc định**: **Bucket Owner** trả toàn bộ chi phí (lưu trữ + băng thông).
*   **Mô hình Requester Pays**:
    *   **Ai trả tiền?**: **Người gửi request (Requester)** trả tiền phí request và phí truyền tải dữ liệu (data transfer). Chủ bucket chỉ trả tiền lưu trữ.
    *   **Khi nào dùng?**: Chia sẻ dữ liệu lớn (Big Data) cho cộng đồng/khách hàng mà không muốn gánh chi phí download.
*   **Yêu cầu kỹ thuật**:
    *   Requester phải là **Authenticated AWS User** (Không hỗ trợ Anonymous).
    *   Phải thêm header `x-amz-request-payer` vào request, nếu không sẽ bị lỗi 403.

## 3. S3 Event Notifications (Thông báo sự kiện)

*   **Khái niệm**: S3 có thể gửi thông báo khi có sự kiện xảy ra trong bucket (ví dụ: tạo object mới, xóa object, restore, replication...).
*   **Điểm đến (Destinations)**:
    *   **SNS (Simple Notification Service)**: Gửi đến Topic (email, SMS).
    *   **SQS (Simple Queue Service)**: Gửi đến Queue (để xử lý bất đồng bộ).
    *   **Lambda Function**: Kích hoạt code xử lý (ví dụ: tạo thumbnail khi upload ảnh).
*   **Amazon EventBridge**: Cách tích hợp mới hơn, cho phép filter mạnh mẽ hơn và route đến nhiều đích hơn (hơn 18 dịch vụ AWS).
*   **Permissions**: Resource đích (SNS/SQS/Lambda) phải có **Access Policy** cho phép S3 gửi tin nhắn đến.

## 4. S3 Performance (Hiệu năng)

*   **Baseline Performance**:
    *   Tự động scale để đáp ứng lượng request cao.
    *   Độ trễ: 100-200 ms.
    *   3,500 PUT/COPY/POST/DELETE mỗi giây trên mỗi prefix.
    *   5,500 GET/HEAD mỗi giây trên mỗi prefix.
*   **Kỹ thuật Tối ưu hóa**:
    *   **Multi-Part Upload**: Bắt buộc cho file > 5GB, khuyến nghị cho file > 100MB. Upload song song các phần (nhanh hơn, có thể retry).
    *   **S3 Transfer Acceleration**: Sử dụng AWS Edge Locations để tăng tốc upload qua khoảng cách xa (upload lên Edge -> AWS backbone -> S3 Bucket).
    *   **S3 Byte-Range Fetches**: Tải song song bằng cách request các dải byte cụ thể (Range header). Tăng tốc download.

## 5. S3 Batch Operations

*   **Mục đích**: Thực hiện hành động hàng loạt trên hàng tỷ object chỉ với 1 API request.
*   **Cách hoạt động**:
    1.  Cung cấp danh sách object (S3 Inventory hoặc file CSV).
    2.  Chọn hành động (Thay đổi tag, Copy, Restore từ Glacier, gọi Lambda).
    3.  S3 tự quản lý tiến trình, retry và báo cáo kết quả.
*   **Ứng dụng**: Chỉnh sửa metadata, copy object giữa các bucket, mã hóa object cũ.

## 6. S3 Storage Lens

*   **Khái niệm**: Dashboard phân tích giúp nhìn thấy toàn cảnh về sử dụng lưu trữ và hoạt động của object storage.
*   **Phạm vi**: Xem được trên cấp Organization, Region, Account, hoặc Bucket.
*   **Lợi ích**:
    *   **Tối ưu chi phí (Cost Efficiency)**: Tìm ra các bucket ít dùng (coldest), các bản upload chưa hoàn thành.
    *   **Bảo vệ dữ liệu (Data Protection)**: Kiểm tra mã hóa hoặc replication đã được bật chưa.
    *   **Default dashboard**: Miễn phí, có sẵn.
