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
