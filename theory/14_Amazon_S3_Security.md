[Vietnamese Below](#vietnamese-version)

# Amazon S3 Security

## 1. S3 Encryption

S3 provides multiple encryption methods to protect data **At Rest** (stored on disk) and **In Transit** (traveling over network).

### A. Encryption In Transit (SSL/TLS)
*   **Protection**: Protects data while it is being uploaded or downloaded.
*   **Mechanism**: Uses **HTTPS** (SSL/TLS) connection.
*   **Enforcement**: You can force encryption in transit using Bucket Policy with condition request: `"aws:SecureTransport": "false"` -> Deny.

### B. Encryption At Rest (Server-Side Encryption - SSE)
There are 4 main types of SSE:

#### 1. SSE-S3 (AES-256)
*   **Managed by**: AWS (S3).
*   **Key**: Known as `SSE-S3`. Keys are handled, managed, and rotated by AWS.
*   **Encryption Type**: AES-256 (Advanced Encryption Standard).
*   **Header**: `x-amz-server-side-encryption: AES256`.
*   **Pros**: Simplest, Free.

#### 2. SSE-KMS (Key Management Service)
*   **Managed by**: AWS KMS (User has control over the key).
*   **Key**: Creating and managing Customer Master Keys (CMKs) in KMS.
*   **Advantages**:
    *   **User Control**: You manage key rotation and access policies.
    *   **Audit Trail**: Logs key usage in **CloudTrail** (who accessed what, when).
*   **Limitations**: Impacted by KMS API Limits (API `GenerateDataKey` and `Decrypt`). If you have massive uploads/downloads, you might hit throttling limits.
*   **Header**: `x-amz-server-side-encryption: aws:kms`.

#### 3. DSSE-KMS (Dual-Layer Server-Side Encryption)
*   **Concept**: Applies **two layers** of encryption to objects.
*   **Use Case**: For highly regulated industries requiring strict compliance (e.g., DoD, NSA standards).
*   **Mechanism**: Similar to SSE-KMS but performs encryption twice with different keys.

#### 4. SSE-C (Customer-Provided Keys)
*   **Managed by**: **YOU** (The Client).
*   **Key**: You send the encryption key along with every request (Upload/Download).
*   **AWS Role**: AWS does **NOT** store the key. It only performs the encryption/decryption using the key you provided, then discards the key from memory.
*   **Requirement**: Must use HTTPS.
*   **Risk**: If you lose the key, data is lost **forever**.

### C. Client-Side Encryption
*   **Mechanism**: You encrypt the data **yourself** (on your client machine) BEFORE sending it to S3.
*   **Keys**: Fully managed by you. S3 only sees encrypted blob.

### D. Default Encryption
*   You can enforce default encryption on a bucket so that any new object uploaded without encryption headers will be automatically encrypted (usually SSE-S3 or SSE-KMS).
*   **Note**: Effective Jan 2023, AWS S3 automatically enables **SSE-S3** as the base level of encryption for all new objects if no other method is specified.

## 2. S3 CORS (Cross-Origin Resource Sharing)

*   **Origin**: Defines where a request comes from (Scheme + Host + Port).
    *   Example: `https://www.example.com` (Scheme: https, Host: www.example.com, Port: 443 implied).
*   **Concept**: Browsers by default block requests from one domain (origin) to another domain (e.g., website `example.com` trying to fetch image from `mybucket.s3.amazonaws.com`). This is a security feature called **Same-Origin Policy**.
*   **Use Case**: You host a static website on S3 or another domain, and your website's JavaScript needs to make API calls or fetch resources from *another* S3 bucket.
*   **Configuration**: You must configure **CORS Rules** on the S3 bucket to allow Cross-Origin requests.
    *   **Allowed Origins**: List of domains allowed (e.g., `https://www.example.com` or `*`).
    *   **Allowed Methods**: GET, PUT, POST, DELETE, HEAD.
    *   **Allowed Headers**: Headers the client can send.
*   **Exam Tip**: If you see "Cross-Origin Request Blocked" error -> You need to enable CORS on the S3 bucket.

## 3. S3 MFA Delete

MFA Delete adds an extra layer of protection by requiring **Multi-Factor Authentication (MFA)** for certain critical S3 operations.

### How It Works
*   **Prerequisite**: **Versioning must be enabled** on the bucket. MFA Delete only works with versioned buckets.
*   **MFA Required For**:
    *   **Permanently deleting** an object version (not just adding a delete marker).
    *   **Suspending versioning** on the bucket.
*   **MFA NOT Required For**:
    *   Enabling versioning.
    *   Listing deleted versions.
    *   Adding a delete marker (soft delete).

### Configuration
*   **Only the Bucket Owner (root account)** can enable/disable MFA Delete.
*   Cannot be enabled via the AWS Console — must use the **AWS CLI** or **API**.
*   Uses MFA device (virtual or hardware) to generate a code for authentication.

### Exam Tips
*   MFA Delete = **extra protection against accidental permanent deletion**.
*   If you see a question about preventing accidental deletion of S3 objects → think **Versioning + MFA Delete**.
*   Remember: **root account only**, **CLI/API only** (not Console).

## 4. S3 Access Logs

S3 Access Logs allow you to record and monitor **all requests** made to an S3 bucket for auditing and analysis purposes.

### How It Works
*   Any request made to S3 (authorized or denied) will be **logged** into another S3 bucket (called the **Logging Bucket** or **Target Bucket**).
*   Log format includes: requester, bucket name, request time, request action, response status, error codes, etc.
*   Logs can be analyzed using tools like **Amazon Athena**, **S3 Select**, or third-party tools.

### Configuration
*   You must specify a **Target Bucket** (Logging Bucket) in the **same AWS Region** as the source bucket.
*   The target bucket must have proper **ACL permissions** (grant `s3:PutObject` to the S3 Log Delivery group).

### ⚠️ Warning: Logging Loop
*   **NEVER set the Logging Bucket to be the same as the Monitored Bucket!**
*   This creates an infinite **logging loop**: every log write generates a new log entry → exponential growth in size → massive costs.

### Exam Tips
*   S3 Access Logs = **auditing who accessed what in your S3 bucket**.
*   Logging bucket must be in the **same region**.
*   Remember the **logging loop** warning — it's a classic exam trap.

## 5. S3 Pre-signed URLs

Pre-signed URLs allow you to give **temporary access** to a specific S3 object without making it public or sharing your credentials.

### How It Works
*   You generate a URL that is **pre-signed** with your credentials and has an **expiration time**.
*   Anyone with the URL can perform the allowed action (GET = download, PUT = upload) until the URL expires.
*   The URL inherits the **permissions of the user who generated it** (via IAM).

### Generation
*   Can be generated using **S3 Console**, **AWS CLI**, or **SDK**.
*   **S3 Console**: Max expiration = **12 hours**.
*   **AWS CLI**: Default expiration = **3600 seconds** (1 hour), max = **168 hours** (7 days) with `--expires-in` parameter.

### Use Cases
*   Allow a **logged-in user** to download a premium video from your S3 bucket.
*   Allow a user to **upload a file** to a specific location in your bucket (e.g., profile picture upload).
*   Generate a **temporary URL** for a file that is normally private.
*   Share files with an **ever-changing list of users** without managing IAM users for each.

### Exam Tips
*   Pre-signed URL = **temporary, time-limited access to private S3 objects**.
*   The URL inherits the **IAM permissions of the person who generated it**.
*   If the generating user loses access → the pre-signed URL **stops working**.
*   Great for: download/upload for non-AWS users, temporary sharing, dynamic user lists.

---

<a id="vietnamese-version"></a>

# Amazon S3 Security

## 1. S3 Encryption (Mã hóa S3)

S3 cung cấp nhiều phương pháp mã hóa để bảo vệ dữ liệu **At Rest** (khi lưu trên đĩa) và **In Transit** (khi truyền qua mạng).

### A. Encryption In Transit (SSL/TLS)
*   **Bảo vệ**: Bảo vệ dữ liệu khi đang upload hoặc download.
*   **Cơ chế**: Sử dụng kết nối **HTTPS** (SSL/TLS).
*   **Bắt buộc**: Bạn có thể ép buộc phải dùng HTTPS bằng Bucket Policy với điều kiện: `"aws:SecureTransport": "false"` -> Deny.

### B. Encryption At Rest (Mã hóa phía Server - SSE)
Có 4 loại SSE chính:

#### 1. SSE-S3 (AES-256)
*   **Quản lý bởi**: AWS (S3).
*   **Key**: Gọi là `SSE-S3`. AWS tự động tạo, quản lý và xoay vòng key.
*   **Loại mã hóa**: AES-256.
*   **Header**: `x-amz-server-side-encryption: AES256`.
*   **Ưu điểm**: Đơn giản nhất, Miễn phí.

#### 2. SSE-KMS (Key Management Service)
*   **Quản lý bởi**: AWS KMS (Người dùng có quyền kiểm soát key).
*   **Key**: Sử dụng Customer Master Keys (CMKs) trong dịch vụ KMS.
*   **Lợi ích**:
    *   **User Control**: Bạn quản lý việc xoay vòng key và chính sách truy cập key.
    *   **Audit Trail (Kiểm toán)**: Ghi lại lịch sử ai dùng key để giải mã file nào trong **CloudTrail**.
*   **Hạn chế**: Bị giới hạn bởi **KMS API Limits** (các lệnh `GenerateDataKey` và `Decrypt`). Nếu upload/download quá nhiều file nhỏ, có thể bị nghẽn (throttling).
*   **Header**: `x-amz-server-side-encryption: aws:kms`.

#### 3. DSSE-KMS (Dual-Layer Server-Side Encryption)
*   **Khái niệm**: Áp dụng **2 lớp** mã hóa cho objects.
*   **Use Case**: Dành cho các ngành công nghiệp quy định cực kỳ nghiêm ngặt (ví dụ: chuẩn quân đội, chính phủ).
*   **Cơ chế**: Giống SSE-KMS nhưng mã hóa 2 lần với các key khác nhau.

#### 4. SSE-C (Customer-Provided Keys)
*   **Quản lý bởi**: **BẠN** (Client).
*   **Key**: Bạn tự giữ key và gửi key kèm theo mỗi request (Upload/Download).
*   **Vai trò của AWS**: AWS **KHÔNG** lưu key. Nó chỉ dùng key bạn gửi để mã hóa/giải mã, sau đó xóa key khỏi bộ nhớ ngay lập tức.
*   **Yêu cầu**: Bắt buộc dùng HTTPS.
*   **Rủi ro**: Nếu bạn mất key, dữ liệu mất **vĩnh viễn**.

### C. Client-Side Encryption (Mã hóa phía Client)
*   **Cơ chế**: Bạn tự mã hóa dữ liệu **trên máy của mình** TRƯỚC khi gửi lên S3.
*   **Quản lý**: Bạn hoàn toàn chịu trách nhiệm về key và tool mã hóa. S3 chỉ nhìn thấy một cục dữ liệu đã mã hóa.

### D. Default Encryption
*   Bạn có thể cài đặt mã hóa mặc định cho bucket để mọi object mới được upload lên mà không có header mã hóa sẽ tự động được mã hóa (thường là SSE-S3 hoặc SSE-KMS).
*   **Lưu ý**: Từ tháng 1/2023, AWS S3 đã tự động bật **SSE-S3** làm chuẩn mã hóa cơ bản cho mọi object mới nếu không chỉ định phương pháp khác.

## 2. S3 CORS (Chia sẻ tài nguyên chéo nguồn)

*   **Origin (Nguồn)**: Định nghĩa nơi request xuất phát (Scheme + Host + Port).
    *   Ví dụ: `https://www.example.com` (Scheme: https, Host: www.example.com, Port: 443 ngầm định).
*   **Khái niệm**: Mặc định, trình duyệt chặn các request từ domain này (origin) sang domain khác (ví dụ: website `example.com` cố gắng lấy ảnh từ `mybucket.s3.amazonaws.com`). Đây là tính năng bảo mật **Same-Origin Policy**.
*   **Use Case**: Bạn host một web tĩnh trên S3 hoặc domain khác, và JavaScript của web cần gọi API hoặc lấy tài nguyên từ *một S3 bucket khác*.
*   **Cấu hình**: Bạn phải cấu hình **CORS Rules** trên S3 bucket đích để cho phép.
    *   **Allowed Origins**: Danh sách domain được phép (ví dụ: `https://www.example.com` hoặc `*`).
    *   **Allowed Methods**: GET, PUT, POST, DELETE, HEAD.
    *   **Allowed Headers**: Các header được phép gửi.
*   **Exam Tip**: Nếu thấy lỗi "Cross-Origin Request Blocked" -> Cần bật CORS trên S3 bucket.

## 3. S3 MFA Delete (Xóa có xác thực đa yếu tố)

MFA Delete thêm một lớp bảo vệ bằng cách yêu cầu **Xác thực đa yếu tố (MFA)** cho một số thao tác quan trọng trên S3.

### Cách hoạt động
*   **Điều kiện tiên quyết**: **Phải bật Versioning** trên bucket. MFA Delete chỉ hoạt động với bucket đã bật versioning.
*   **Cần MFA khi**:
    *   **Xóa vĩnh viễn** một phiên bản object (không phải chỉ thêm delete marker).
    *   **Tạm dừng (suspend) versioning** trên bucket.
*   **KHÔNG cần MFA khi**:
    *   Bật versioning.
    *   Liệt kê các phiên bản đã xóa.
    *   Thêm delete marker (xóa mềm).

### Cấu hình
*   **Chỉ Bucket Owner (tài khoản root)** mới có thể bật/tắt MFA Delete.
*   Không thể bật qua AWS Console — phải dùng **AWS CLI** hoặc **API**.
*   Sử dụng thiết bị MFA (ảo hoặc vật lý) để tạo mã xác thực.

### Exam Tips
*   MFA Delete = **bảo vệ thêm chống xóa vĩnh viễn nhầm**.
*   Nếu thấy câu hỏi về ngăn chặn xóa nhầm S3 objects → nghĩ đến **Versioning + MFA Delete**.
*   Ghi nhớ: **chỉ tài khoản root**, **chỉ CLI/API** (không dùng Console được).

## 4. S3 Access Logs (Nhật ký truy cập S3)

S3 Access Logs cho phép bạn ghi lại và giám sát **tất cả các request** đến một S3 bucket để phục vụ kiểm toán và phân tích.

### Cách hoạt động
*   Mọi request đến S3 (dù được cho phép hay bị từ chối) đều được **ghi log** vào một S3 bucket khác (gọi là **Logging Bucket** hay **Target Bucket**).
*   Log bao gồm: người gửi request, tên bucket, thời gian, hành động, trạng thái phản hồi, mã lỗi, v.v.
*   Log có thể được phân tích bằng **Amazon Athena**, **S3 Select**, hoặc các công cụ bên thứ ba.

### Cấu hình
*   Phải chỉ định một **Target Bucket** (Logging Bucket) trong **cùng AWS Region** với bucket nguồn.
*   Target bucket phải có **quyền ACL** phù hợp (cấp `s3:PutObject` cho nhóm S3 Log Delivery).

### ⚠️ Cảnh báo: Vòng lặp Log
*   **TUYỆT ĐỐI KHÔNG đặt Logging Bucket trùng với Bucket đang giám sát!**
*   Điều này tạo ra **vòng lặp log vô hạn**: mỗi lần ghi log lại sinh ra log mới → tăng trưởng mũ → chi phí khổng lồ.

### Exam Tips
*   S3 Access Logs = **kiểm toán ai đã truy cập gì trong S3 bucket**.
*   Logging bucket phải cùng **region**.
*   Nhớ cảnh báo **vòng lặp log** — đây là bẫy kinh điển trong đề thi.

## 5. S3 Pre-signed URLs (URL ký trước)

Pre-signed URLs cho phép bạn cấp **quyền truy cập tạm thời** vào một S3 object cụ thể mà không cần public bucket hay chia sẻ credentials.

### Cách hoạt động
*   Bạn tạo một URL được **ký trước** bằng credentials của bạn và có **thời hạn hết hạn**.
*   Bất kỳ ai có URL đều có thể thực hiện hành động được phép (GET = download, PUT = upload) cho đến khi URL hết hạn.
*   URL **kế thừa quyền của người tạo nó** (thông qua IAM).

### Cách tạo
*   Có thể tạo bằng **S3 Console**, **AWS CLI**, hoặc **SDK**.
*   **S3 Console**: Thời hạn tối đa = **12 giờ**.
*   **AWS CLI**: Thời hạn mặc định = **3600 giây** (1 giờ), tối đa = **168 giờ** (7 ngày) với tham số `--expires-in`.

### Use Cases
*   Cho phép người dùng đã đăng nhập **download video premium** từ S3 bucket.
*   Cho phép người dùng **upload file** vào một vị trí cụ thể trong bucket (ví dụ: upload ảnh đại diện).
*   Tạo **URL tạm thời** cho file bình thường là private.
*   Chia sẻ file với **danh sách người dùng thay đổi liên tục** mà không cần tạo IAM user cho từng người.

### Exam Tips
*   Pre-signed URL = **quyền truy cập tạm thời, có giới hạn thời gian vào S3 objects private**.
*   URL kế thừa **quyền IAM của người tạo nó**.
*   Nếu người tạo mất quyền → pre-signed URL **ngừng hoạt động**.
*   Phù hợp cho: download/upload cho người dùng không có AWS, chia sẻ tạm thời, danh sách user động.
