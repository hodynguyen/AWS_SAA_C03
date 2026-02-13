[Vietnamese Below](#vietnamese-version)

# Amazon S3 Introduction - Cheat Sheet SAA-C03

## 1. S3 Overview

### Basic Concepts
* **Object Storage**: Stores data as objects (not a file system hierarchy).
* **Buckets**: Container acting as top-level folder for objects, names must be **globally unique**.
* **Objects**: Key (name), Value (data), Version ID, Metadata, Tags.

### Important Limits
* **Max object size**: 5TB.
* **Single PUT**: Max 5GB → File > 5GB must use **Multi-Part Upload**.
* **Recommended**: Use Multi-Part Upload for files > 100MB.

### Durability & Availability
* **Durability**: 99.999999999% (11 nines) - probability that data is not lost.
* **Availability**: 99.99% (S3 Standard) - ability to access the service.

### Use Cases
* Backup & archive, Data lakes, Static websites, Media hosting, Software delivery.

## 2. S3 Security: Bucket Policy

### Concepts
* **Resource-based policy** attached strictly to the bucket.
* Controls **who** can do **what** with the bucket/objects.
* Applies to **all requests** (cross-account, public, internal).

### Policy Structure

```json
{
  "Version": "2012-10-17",
  "Statement": [{
    "Sid": "Description",
    "Effect": "Allow/Deny",
    "Principal": "*",                    // Who is allowed
    "Action": "s3:GetObject",            // What action
    "Resource": "arn:aws:s3:::bucket/*", // Which resource
    "Condition": {}                      // Conditions (optional)
  }]
}
```

### Important Examples
*   **Public Read (Static Website):**
    ```json
    {
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::my-website/*"
    }
    ```
*   **Force HTTPS:**
    ```json
    {
      "Effect": "Deny",
      "Principal": "*",
      "Action": "s3:*",
      "Resource": "arn:aws:s3:::my-bucket/*",
      "Condition": {
        "Bool": {"aws:SecureTransport": "false"}
      }
    }
    ```
*   **Force Encryption at Upload:**
    ```json
    {
      "Effect": "Deny",
      "Principal": "*",
      "Action": "s3:PutObject",
      "Resource": "arn:aws:s3:::my-bucket/*",
      "Condition": {
        "StringNotEquals": {
          "s3:x-amz-server-side-encryption": "AES256"
        }
      }
    }
    ```
*   **Cross-Account Access:**
    ```json
    {
      "Effect": "Allow",
      "Principal": {"AWS": "arn:aws:iam::123456789012:root"},
      "Action": ["s3:GetObject", "s3:ListBucket"],
      "Resource": [
        "arn:aws:s3:::shared-bucket",
        "arn:aws:s3:::shared-bucket/*"
      ]
    }
    ```

### Policy Evaluation Logic (Important!)
Priority Order:
1.  **Explicit DENY** (IAM/Bucket Policy)
    ↓
2.  **Explicit ALLOW** (IAM or Bucket Policy)
    ↓
3.  **Implicit DENY** (default)

**Golden Rule**: "Explicit DENY always wins".
*Example*:
*   Bucket Policy: ALLOW `s3:PutObject`
*   IAM Policy: DENY `s3:PutObject`
*   → Result: **DENY** (user cannot PutObject).

### IAM Policy vs Bucket Policy

| Criteria | IAM Policy | Bucket Policy |
| :--- | :--- | :--- |
| **Attached to** | User/Role/Group | Bucket |
| **Scope** | Specific User | All requests |
| **Cross-account** | ❌ | ✅ |
| **Public access** | ❌ | ✅ (Principal: "*") |
| **Use case** | Internal users | External, public, cross-account |

### Block Public Access
*   **Final safety net** preventing public access.
*   Overrides all Bucket Policies/ACLs.
*   4 settings: `BlockPublicAcls`, `IgnorePublicAcls`, `BlockPublicPolicy`, `RestrictPublicBuckets`.
*   **Best practice**: Enable all 4 (unless public access is explicitly needed).

## 3. S3 Versioning

### Concepts
*   Keeps multiple versions of the same object.
*   Enabled at **bucket level**, cannot be disabled (only suspended).
*   Each version has a unique **Version ID**.

### Delete Behavior
*   **Soft delete** (version not specified): Creates **Delete Marker**, can be restored.
*   **Hard delete** (version specified): Permanently deleted, cannot be restored.

### Restore
```bash
# Delete the Delete Marker to restore
aws s3api delete-object --bucket my-bucket --key file.txt --version-id <delete-marker-id>
```

### Use Cases
*   Protection against accidental deletion.
*   Rollback changes.
*   Compliance & audit.

### Best Practice
*   Combine with **Lifecycle Policies** to auto-archive/delete old versions.
*   Enable **MFA Delete** for production critical data.

## 4. S3 Replication

### Two Types
*   **Cross-Region Replication (CRR)**:
    *   Replicate to **different region**.
    *   Use cases: DR, compliance, lower latency.
*   **Same-Region Replication (SRR)**:
    *   Replicate within **same region**.
    *   Use cases: Log aggregation, prod/test sync.

### Requirements
1.  **Versioning** must be enabled on both source and destination.
2.  **IAM Role** with read/write permissions.
3.  **Asynchronous** - latency from seconds to minutes.

### Important
*   ✅ Only replicates **new objects** (after enabling).
*   ❌ Old objects do NOT replicate (use **S3 Batch Replication** if needed).
*   ❌ Permanent deletes (with version ID) do NOT replicate.
*   ⚠️ Delete markers: Optional (can enable/disable).

### Use Cases
*   **CRR**: DR, compliance multi-region, global low-latency.
*   **SRR**: Log aggregation, cross-account backup.

## 5. S3 Website Hosting

### Quick Setup
1.  Enable Static Website Hosting (set `index.html`, `error.html`).
2.  Upload files (HTML, CSS, JS, images).
3.  Bucket Policy: Public read (`s3:GetObject`).
4.  Turn off Block Public Access.

### URL Format
`http://<bucket-name>.s3-website-<region>.amazonaws.com`
⚠️ Only HTTP, no HTTPS → Use **CloudFront** if HTTPS is needed.

### Index Document
*   `http://bucket.../`           → `index.html`
*   `http://bucket.../about/`     → `about/index.html`
*   **Note**: Must have trailing slash `/`.

### Error Document
*   404, 403 → Serve `error.html`.
*   HTTP status code still correct (404, 403...).

### Use Cases
*   Personal portfolio, SPA (React/Vue), Documentation, Landing pages.

### Troubleshooting
*   **403 Forbidden**: Check Bucket Policy + Block Public Access.
*   **404 Not Found**: Check file exists + Static Hosting enabled + URL correct.

### Best Practice
*   Use **CloudFront** for HTTPS + custom domain.
*   Set **Cache-Control** headers (CSS/JS: 1 year, HTML: no-cache).
*   Enable **versioning** to rollback.

## 6. S3 Storage Classes

| Storage Class | Availability | AZs | Min Duration | Retrieval | Use Case |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Standard** | 99.99% | ≥3 | None | Free | Frequent access |
| **Intelligent-Tiering** | 99.9% | ≥3 | None | Free* | Unpredictable patterns |
| **Standard-IA** | 99.9% | ≥3 | 30 days | Paid | Infrequent, fast retrieval |
| **One Zone-IA** | 99.5% | 1 | 30 days | Paid | Recreatable data |
| **Glacier Instant** | 99.9% | ≥3 | 90 days | Paid | Archive, instant access |
| **Glacier Flexible** | 99.99% | ≥3 | 90 days | Paid | Archive, hours (1-12h) |
| **Glacier Deep** | 99.99% | ≥3 | 180 days | Paid | Archive, 12-48h |

*\*Intelligent-Tiering: Small monitoring fee (~$0.0025/1000 objects)*

### Quick Details
*   **S3 Standard**: Frequent access, low latency, high throughput.
*   **Intelligent-Tiering**: Automatically moves between tiers based on access patterns.
    *   Frequent → Infrequent (30 days) → Archive Instant (90 days).
*   **Standard-IA**: Cheaper than Standard ~50%, has retrieval fee, min 30 days.
*   **One Zone-IA**: Like Standard-IA but 1 AZ, cheaper ~20%, **data lost if AZ fails**.
*   **Glacier Instant**: Archive with millisecond retrieval, min 90 days.
*   **Glacier Flexible**: Retrieval 1-5 mins (Expedited), 3-5h (Standard), 5-12h (Bulk).
*   **Glacier Deep Archive**: Cheapest (~$1/TB/month), retrieval 12h (Standard) or 48h (Bulk).

### Lifecycle Transitions
```text
Standard → (30d) → Standard-IA → (30d) → One Zone-IA
         → (90d) → Glacier Instant → Glacier Flexible → (180d) → Deep Archive
```

### SAA-C03 Exam Tips

#### Storage Classes
*   Frequent access → **Standard**
*   Unpredictable → **Intelligent-Tiering**
*   Infrequent + fast → **Standard-IA**
*   Infrequent + 1 AZ OK → **One Zone-IA**
*   Archive + instant → **Glacier Instant**
*   Archive + hours → **Glacier Flexible**
*   Archive + days → **Glacier Deep**

#### Scenarios
*   Prevent deletes → Versioning + MFA Delete
*   Cross-region DR → CRR
*   Replicate existing → S3 Batch Replication
*   Static website HTTPS → S3 + CloudFront
*   SPA 404 on refresh → `error.html` = `index.html`
*   403 on website → Check Policy + Block Public Access

---

<a id="vietnamese-version"></a>

# Amazon S3 Introduction - Cheat Sheet SAA-C03

## 1. S3 Overview

### Khái niệm cơ bản
*   **Object Storage**: Lưu trữ dữ liệu dưới dạng objects (không phải file system).
*   **Buckets**: Container chứa objects, tên phải **globally unique**.
*   **Objects**: Key (tên), Value (data), Version ID, Metadata, Tags.

### Giới hạn quan trọng
*   **Max object size**: 5TB.
*   **Single PUT**: Max 5GB → File > 5GB phải dùng **Multi-Part Upload**.
*   **Recommended**: Multi-Part Upload cho file > 100MB.

### Durability & Availability
*   **Durability**: 99.999999999% (11 nines) - dữ liệu không bị mất.
*   **Availability**: 99.99% (S3 Standard) - khả năng truy cập được service.

### Use Cases
*   Backup & archive, Data lakes, Static websites, Media hosting, Software delivery.

## 2. S3 Security: Bucket Policy

### Khái niệm
*   **Resource-based policy** gắn vào bucket.
*   Kiểm soát **ai** có thể làm **gì** với bucket/objects.
*   Áp dụng cho **tất cả requests** (cross-account, public, internal).

### Cấu trúc Policy

```json
{
  "Version": "2012-10-17",
  "Statement": [{
    "Sid": "Description",
    "Effect": "Allow/Deny",
    "Principal": "*",                    // Ai được phép
    "Action": "s3:GetObject",            // Hành động gì
    "Resource": "arn:aws:s3:::bucket/*", // Resource nào
    "Condition": {}                      // Điều kiện (optional)
  }]
}
```

### Ví dụ quan trọng
*   **Public Read (Static Website):**
    ```json
    {
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::my-website/*"
    }
    ```
*   **Force HTTPS:**
    ```json
    {
      "Effect": "Deny",
      "Principal": "*",
      "Action": "s3:*",
      "Resource": "arn:aws:s3:::my-bucket/*",
      "Condition": {
        "Bool": {"aws:SecureTransport": "false"}
      }
    }
    ```
*   **Force Encryption at Upload:**
    ```json
    {
      "Effect": "Deny",
      "Principal": "*",
      "Action": "s3:PutObject",
      "Resource": "arn:aws:s3:::my-bucket/*",
      "Condition": {
        "StringNotEquals": {
          "s3:x-amz-server-side-encryption": "AES256"
        }
      }
    }
    ```
*   **Cross-Account Access:**
    ```json
    {
      "Effect": "Allow",
      "Principal": {"AWS": "arn:aws:iam::123456789012:root"},
      "Action": ["s3:GetObject", "s3:ListBucket"],
      "Resource": [
        "arn:aws:s3:::shared-bucket",
        "arn:aws:s3:::shared-bucket/*"
      ]
    }
    ```

### Policy Evaluation Logic (Quan trọng!)
Thứ tự ưu tiên:
1.  **Explicit DENY** (IAM/Bucket Policy)
    ↓
2.  **Explicit ALLOW** (IAM hoặc Bucket Policy)
    ↓
3.  **Implicit DENY** (default)

**Nguyên tắc vàng**: "Explicit DENY luôn thắng"
*Ví dụ*:
*   Bucket Policy: ALLOW `s3:PutObject`
*   IAM Policy: DENY `s3:PutObject`
*   → Kết quả: **DENY** (user không thể PutObject).

### IAM Policy vs Bucket Policy

| Tiêu chí | IAM Policy | Bucket Policy |
| :--- | :--- | :--- |
| **Gắn vào** | User/Role/Group | Bucket |
| **Scope** | User cụ thể | Tất cả requests |
| **Cross-account** | ❌ | ✅ |
| **Public access** | ❌ | ✅ (Principal: "*") |
| **Use case** | Internal users | External, public, cross-account |

### Block Public Access
*   **Safety net** cuối cùng ngăn public access.
*   Override tất cả Bucket Policies/ACLs.
*   4 settings: `BlockPublicAcls`, `IgnorePublicAcls`, `BlockPublicPolicy`, `RestrictPublicBuckets`.
*   **Best practice**: Bật tất cả 4 (trừ khi cần public access rõ ràng).

## 3. S3 Versioning

### Khái niệm
*   Giữ nhiều versions của cùng object.
*   Bật ở **bucket level**, không thể tắt (chỉ suspend).
*   Mỗi version có unique **Version ID**.

### Delete Behavior
*   **Soft delete** (không chỉ định version): Tạo **Delete Marker**, có thể restore.
*   **Hard delete** (chỉ định version): Xóa vĩnh viễn, không restore được.

### Restore
```bash
# Xóa Delete Marker để restore
aws s3api delete-object --bucket my-bucket --key file.txt --version-id <delete-marker-id>
```

### Use Cases
*   Bảo vệ khỏi xóa nhầm.
*   Rollback changes.
*   Compliance & audit.

### Best Practice
*   Kết hợp **Lifecycle Policies** để auto-archive/delete old versions.
*   Enable **MFA Delete** cho production critical data.

## 4. S3 Replication

### Hai loại
*   **Cross-Region Replication (CRR)**:
    *   Replicate sang **region khác**.
    *   Use cases: DR, compliance, lower latency.
*   **Same-Region Replication (SRR)**:
    *   Replicate trong **cùng region**.
    *   Use cases: Log aggregation, prod/test sync.

### Requirements
1.  **Versioning** phải bật ở cả source và destination.
2.  **IAM Role** với quyền read/write.
3.  **Asynchronous** - có độ trễ vài giây đến vài phút.

### Quan trọng
*   ✅ Chỉ replicate **objects mới** (sau khi enable).
*   ❌ Objects cũ KHÔNG replicate (dùng **S3 Batch Replication** nếu cần).
*   ❌ Permanent deletes (với version ID) KHÔNG replicate.
*   ⚠️ Delete markers: Optional (có thể enable/disable).

### Use Cases
*   **CRR**: DR, compliance multi-region, global low-latency.
*   **SRR**: Log aggregation, cross-account backup.

## 5. S3 Website Hosting

### Setup nhanh
1.  Enable Static Website Hosting (set `index.html`, `error.html`).
2.  Upload files (HTML, CSS, JS, images).
3.  Bucket Policy: Public read (`s3:GetObject`).
4.  Tắt Block Public Access.

### URL Format

`http://<bucket-name>.s3-website-<region>.amazonaws.com`
⚠️ Chỉ HTTP, không HTTPS → Dùng **CloudFront** nếu cần HTTPS.

### Index Document
*   `http://bucket.../`           → `index.html`
*   `http://bucket.../about/`     → `about/index.html`
*   Lưu ý: Phải có trailing slash `/`.

### Error Document
*   404, 403 → Serve `error.html`.
*   HTTP status code vẫn đúng (404, 403...).

### Use Cases
*   Personal portfolio, SPA (React/Vue), Documentation, Landing pages.

### Troubleshooting
*   **403 Forbidden**: Check Bucket Policy + Block Public Access.
*   **404 Not Found**: Check file tồn tại + Static Hosting enabled + URL đúng.

### Best Practice
*   Dùng **CloudFront** cho HTTPS + custom domain.
*   Set **Cache-Control** headers (CSS/JS: 1 năm, HTML: no-cache).
*   Enable **versioning** để rollback.

## 6. S3 Storage Classes
| Storage Class | Availability | AZs | Min Duration | Retrieval | Use Case |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Standard** | 99.99% | ≥3 | None | Free | Frequent access |
| **Intelligent-Tiering** | 99.9% | ≥3 | None | Free* | Unpredictable patterns |
| **Standard-IA** | 99.9% | ≥3 | 30 days | Paid | Infrequent, fast retrieval |
| **One Zone-IA** | 99.5% | 1 | 30 days | Paid | Recreatable data |
| **Glacier Instant** | 99.9% | ≥3 | 90 days | Paid | Archive, instant access |
| **Glacier Flexible** | 99.99% | ≥3 | 90 days | Paid | Archive, hours (1-12h) |
| **Glacier Deep** | 99.99% | ≥3 | 180 days | Paid | Archive, 12-48h |

*\*Intelligent-Tiering: Có monitoring fee nhỏ (~$0.0025/1000 objects)*

### Chi tiết nhanh
*   **S3 Standard**: Frequent access, low latency, high throughput.
*   **Intelligent-Tiering**: Tự động chuyển giữa tiers dựa trên access patterns.
    *   Frequent → Infrequent (30 days) → Archive Instant (90 days).
*   **Standard-IA**: Rẻ hơn Standard ~50%, có retrieval fee, min 30 days.
*   **One Zone-IA**: Giống Standard-IA nhưng 1 AZ, rẻ hơn ~20%, **mất data nếu AZ fail**.
*   **Glacier Instant**: Archive với retrieval milliseconds, min 90 days.
*   **Glacier Flexible**: Retrieval 1-5 phút (Expedited), 3-5h (Standard), 5-12h (Bulk).
*   **Glacier Deep Archive**: Rẻ nhất (~$1/TB/tháng), retrieval 12h (Standard) hoặc 48h (Bulk).

### Lifecycle Transitions
```text
Standard → (30d) → Standard-IA → (30d) → One Zone-IA
         → (90d) → Glacier Instant → Glacier Flexible → (180d) → Deep Archive
```

### Mẹo thi SAA-C03

#### Storage Classes
*   Frequent access → **Standard**
*   Unpredictable → **Intelligent-Tiering**
*   Infrequent + fast → **Standard-IA**
*   Infrequent + 1 AZ OK → **One Zone-IA**
*   Archive + instant → **Glacier Instant**
*   Archive + hours → **Glacier Flexible**
*   Archive + days → **Glacier Deep**

#### Scenarios
*   Prevent deletes → Versioning + MFA Delete
*   Cross-region DR → CRR
*   Replicate existing → S3 Batch Replication
*   Static website HTTPS → S3 + CloudFront
*   SPA 404 on refresh → `error.html` = `index.html`
*   403 on website → Check Policy + Block Public Access
