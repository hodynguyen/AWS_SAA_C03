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
