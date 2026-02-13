# IAM and AWS CLI

## I. Core concepts

### Root Account
- Created by default
- Has full permissions and cannot be restricted
- Best practice: Lock it away, enable MFA, do not use for daily tasks

### IAM User
- Represents a real person or an application
- Can be grouped into Groups
- Best Practice: One physical person = one IAM User

### IAM Groups
- Contains many Users
- Used to assign permissions to multiple users with a shared function
- Note: Groups cannot contain other groups

### IAM Roles - IMPORTANT
- Similar to a User but not associated with a specific person
- Used by:
    - AWS Services: EC2, Lambda, Glue, ... needing access to S3, DynamoDB
    - Cross-account: User from Account A wants to access resources in Account B
    - Identity Federation: User from an external system logs into AWS
- Uses Temporary Security Credentials (Time-limited tokens, safer than long-term Access Keys)


## II. Permissions & Policies

### JSON Policy Structure

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "Identifier",
      "Effect": "Allow",          // Allow or Deny
      "Principal": { "AWS": "..." }, // Who is granted permission (User/Role)
      "Action": "s3:GetObject",   // What action
      "Resource": "arn:aws:s3:::my-bucket/*" // Where
    }
  ]
}
```

### Policy Logic
- **Implicit Deny** (Default deny): If there's no policy -> denied
- **Explicit Allow**: Must have an Allow statement to permit action
- **Explicit Deny** (Absolute prohibition): Deny always wins over Allow, if full admin exists but 1 policy denies S3 -> S3 access denied

### IAM Best Practice
- **Least Privilege Principle**: Grant only minimum necessary permissions, do not grant full access
- Use **Access Advisor** to check if users have excess permissions (permissions granted but never used)

## III. IAM Security Tools

### IAM Credentials Report (Account Level)
- Reports all Users in the account
- Lists status: Password, Access Key (rotated?), MFA (enabled?)
- Used for general auditing

### IAM Access Advisor (User Level)
- Shows which services a user accessed and when they last accessed them
- Used to refine permissions (revoke long-unused permissions)

### MFA (Multi-factor Authentication)
- Mandatory for Root and IAM Users
- Types of MFA:
    - Virtual MFA: Google Authenticator, Authy (Phone)
    - U2F Security Key: YubiKey (Plug into USB) -> most secure
    - Hardware Key Fob: Physical device generating numbers (Gemalto)

## IV. Access Methods

| Methods | Use | Object |
| :--- | :--- | :--- |
| AWS Console | Password + MFA | Person (Web + UI) |
| CLI/SDK | Access Key ID + Secret Access Key | Dev, Script, App |
| IAM Role | Temporary Token | EC2 Instance, Lambda Function |

**Note**: Do not hard-code access keys, if code runs on EC2 use IAM Role

## V. IAM Roles for Services

When an EC2 needs to access S3
- Create a Policy allowing `s3:ListBucket`
- Create an IAM Role and attach that Policy
- Attach that Role to the EC2 Instance
- Code on EC2 using AWS SDK will automatically retrieve permissions without key configuration

## VI. Amazon Cognito (User Auth for Mobile/Web Apps)

IAM solution for millions of Users (do not use IAM User here as AWS limits User/Account count)

| Component | Function (Exam Keyword) | Example |
| :--- | :--- | :--- |
| **User Pools** | **Authentication** (Verify identity). Sign-up, Sign-in, User Directory. Supports Facebook, Google Login. | User enters user/pass to log into Web Game. |
| **Identity Pools** | **Authorization** (Grant permissions). Grants direct access to AWS Resources. | Logged-in user wants to upload avatar to their S3 Bucket. |

## VII. Advanced IAM & Multi-account Strategy

### AWS Organizations
- Centrally manage multiple Accounts (Consolidated Billing)
- Service Control Policies (SCPs)
    - The "iron cage" limiting maximum permissions of Member Accounts
    - Important: SCP does not grant permissions (allow), only limits/denies permissions
    - Applies to Root User of Member Account as well

### IAM Identity Center (Old AWS SSO)
- "Single Sign-On" solution
- Links with company Active Directory
- User uses 1 company account to log into AWS console of 10 different accounts

## VIII. AWS Directory Service (Active Directory Integration)

| Directory Type | When to use? |
| :--- | :--- |
| **AWS Managed Microsoft AD** | When real AD is needed on Cloud. Supports Group Policy, Trust Relationship with On-Prem AD. |
| **AD Connector** | Just a "Proxy Gateway". Redirects requests to On-Prem AD. No data stored on Cloud. |
| **Simple AD** | "Poor man's" AD (based on Samba), fewer features. Used for small projects. |

## IX. Exam Tips

- "EC2 needs access to S3/DynamoDB" -> IAM Role
- "Mobile App needs access to AWS" -> Cognito (or Web Identity Federation with Role), do not store keys in app
- "Audit who hasn't changed pass/enabled MFA" -> IAM Credentials Report
- "Excess/unused permissions" -> Access Advisor
- "Multi-account Security" -> Organization + SCP
- "Github Actions/External System needs to deploy to AWS" -> IAM Roles (OpenID Connect - OIDC) instead of creating User

---

[Vietnamese Below]

# IAM and AWS CLI

## I. Core concepts

### Root Account
- Được tạo mặc định
- Có toàn quyền và không thể giới hạn quyền
- Best practice: Khoá lại, kích hoạt MFA, không cùng cho các tác vụ hàng ngày

### IAM User
- Đại diện cho một người thật hoặc một ứng dụng
- Có thể được nhóm vào các Groups
- Best Practice: Một người thật = một IAM User

### IAM Groups
- Chưa nhiều Users
- Dùng để gán quyền cho nhiều users có chung một chức năng
- Lưu ý: Group không thể chứa group khác

### IAM Roles - IMPORTANT
- Giống với User nhưng không gắn với một người cụ thể
- Được dùng bởi
    - AWS Services: EC2, Lambda, Glue, … cần quyền truy cập S3, DynamoDB
    - Cross-account: User từ Account A muốn truy cập resource Account B
    - Identity Federation: User từ hệ thống ngoài đăng nhập vào AWS
- Sử dụng Temporary Security Credentials (Token có thời hạn, an toàn hơn Access Key lâu dài)


## II. Permissions & Policies

### JSON Policy Structure

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "Identifier",
      "Effect": "Allow",          // Allow hoặc Deny
      "Principal": { "AWS": "..." }, // Ai được quyền (User/Role)
      "Action": "s3:GetObject",   // Làm cái gì
      "Resource": "arn:aws:s3:::my-bucket/*" // Ở đâu
    }
  ]
}
```

### Policy Logic
- **Implicit Deny** (Mặc định từ chối): Nếu không có policy gì -> cấm
- **Explicit Allow**: Phải có một dòng Allow thì mới được làm
- **Explicit Deny** (Cấm tuyệt đối): Deny luôn chiến thằng Allow, nếu có full admin nhưng 1 policy deny S3 -> cấm S3

### IAM Best Practice
- **Least Privilege Principle**: Chỉ cấp quyền vừa đủ để làm việc, không cấp full access
- Sử dụng **Access Advisor** để soi xem user có thừa quyền không (quyền được cấp nhưng không bao giờ dùng)

## III. IAM Security Tools

### IAM Credentials Report (Cấp Account)
- Báo cáo toàn bộ Users trong tài khoản
- Liệt kê trạng thái: Password, Access Key (có rotate chưa), MFA (có enable chưa)
- Dùng để audit tổng quan

### IAM Access Advisor (Cấp User)
- Cho biết user đã truy cập dịch vụ nào và lần cuối truy cập là khi nào
- Dùng để tinh chỉnh quyền (thu hồi quyền lâu không dùng).

### MFA (Multi-factor Authentication)
- Bắt buộc bật cho Root và IAM Users
- Các loại MFA
    - Virtual MFA: GG Authenticator, Authy (Điện thoại)
    - U2F Security Key: YubiKey (Cắm vào USB) -> an toàn nhất
    - Hardware Key Fob: Thiết bị vật lý nhảy số (Gemalto)

## IV. Access Methods

| Methods | Use | Object |
| :--- | :--- | :--- |
| AWS Console | Password + MFA | Con người (Web + UI) |
| CLI/DKS | Access Key ID + Secret Access Key | Dev, Script, App |
| IAM Role | Temporary Token | EC2 Intance, Lambda Function |

**Note**: Không hard-code access key, nếu code chạy trên EC2 thì dùng IAM Role

## V. IAM Roles for Services

Khi một EC2 cần truy cập S3
- Tạo một Policy cho phép `s3:ListBucket`
- Tạo IAM Role và gắn Policy đó vào
- Gần Role đó cho EC3 Instance
- Code trên EC2 dùng AWS SDK sẽ từ động lấy được quyền mà không cần cấu hình key

## VI. Amazon Cognito (User Auth cho Mobile/Web Apps)

Giải pháp IAM cho hàng triệu Users (không dùng IAM User ở đây vì AWS limit số lượng User/Account)

| Thành phần | Chức năng (Keyword thi) | Ví dụ |
| :--- | :--- | :--- |
| **User Pools** | **Authentication** (Xác thực). Sign-up, Sign-in, User Directory. Hỗ trợ Facebook, Google Login. | User nhập user/pass để đăng nhập vào Web Game. |
| **Identity Pools** | **Authorization** (Phân quyền). Cấp quyền truy cập trực tiếp vào AWS Resource. | User đã đăng nhập muốn upload avatar lên S3 Bucket của họ. |

## VII. Advanced IAM & Multi-account Strategy

### AWS Organizations
- Quản lý tập trung nhiều Account (Consolidated Billing)
- Service Control Policies (SCPs)
    - Là cái “lồng sắt” giới hạn quyền tối đa của các Member Account
    - Quan trọng: SCP không cấp quyền (alllow) chỉ giới hạn quyền (limit/deny)
    - Áp dụng cho cả Root User của Member Account

### IAM Identity Center (AWS SSO cũ)
- Giải pháp “Single Sign-On”
- Link với Active Directory của công ty
- User dùng 1 tài khoản công ty đăng nhập vào AWS console của 10 account khác nhau

## VIII. AWS Directory Service (Tích hợp Active Directory)

| Loại Directory | Khi nào dùng? |
| :--- | :--- |
| **AWS Managed Microsoft AD** | Khi cần AD thật trên Cloud. Hỗ trợ Group Policy, Trust Relationship với On-Prem AD. |
| **AD Connector** | Chỉ là "Cổng Proxy". Redirect request về On-Prem AD. Không lưu data trên Cloud. |
| **Simple AD** | Bản AD "nhà nghèo" (dựa trên Samba), ít tính năng. Dùng cho dự án nhỏ. |

## IX. Exam Tips

- “EC2 cần truy cập S3/DynamoDB” -> IAM Role
- “Mobile App cần truy cập AWS” -> Cognito (hoặc Web Identity Federation với Role), không lưu key trong app
- “Audit xem ai chưa đổi pass/enable MFA” -> IAM Credentials Report
- “Quyền thừa/không dùng” -> Access Advisor
- “Multi-account Security” 0> Organization + SCP
- “Github Actions/External System cần deploy vào AWS” -> IAM Roles (OpenID Connect - OIDC) thay vì tạo User
