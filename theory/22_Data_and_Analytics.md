[Vietnamese Below](#vietnamese-version)

# Data & Analytics

## 1. Amazon Athena

Amazon Athena is a **serverless query service** to analyze data stored in **Amazon S3** using **SQL**.

### Key Features
*   **Serverless** — no infrastructure to manage.
*   Query data directly in **S3** using standard **SQL** (built on **Presto**).
*   Supports **CSV, JSON, ORC, Avro, Parquet** formats.
*   **Pay per query** — $5 per TB of data scanned.
*   Commonly used with **Amazon QuickSight** for dashboards/reporting.

### Performance Improvement
*   Use **columnar data** (Parquet or ORC) — reduces data scanned significantly.
*   **Compress** data (gzip, snappy, zstd).
*   **Partition** data in S3 (e.g., `s3://bucket/year=2024/month=01/`).
*   Use **larger files** (> 128MB) to minimize overhead.

### Federated Query
*   Query data across **multiple sources** (RDS, DynamoDB, Redshift, CloudWatch Logs, on-premises) using **Lambda Data Source Connectors**.
*   Results stored back in S3.

### Exam Tips
*   Athena = **serverless SQL on S3**.
*   "Analyze data in S3" or "query S3 logs" → **Athena**.
*   Use **Parquet/ORC** for cost and performance optimization.
*   **Pay per TB scanned** — columnar format saves money.

## 2. Amazon Redshift

Amazon Redshift is a **fully managed data warehouse** for **OLAP** (Online Analytical Processing) — analytics and data warehousing.

### Key Features
*   **Columnar storage** (not row-based) — 10x better performance than other data warehouses.
*   **Massively Parallel Query Execution (MPP)**.
*   **Pay-as-you-go** based on instances provisioned.
*   SQL interface (PostgreSQL-compatible).
*   Integrates with **QuickSight** and **Tableau** for BI tools.
*   Data load: from S3, DynamoDB, DMS, other databases.

### Redshift Cluster
*   **Leader Node**: Query planning, results aggregation.
*   **Compute Nodes**: Perform queries, up to 128 nodes.
*   **Node types**: RA3 (choose size), DC2 (dense compute), DS2 (dense storage).
*   **No Multi-AZ** mode (single-AZ). For DR: use **snapshots** (automated/manual) to another region.

### Redshift Spectrum
*   Query data in **S3 without loading it** into Redshift.
*   Must have a **Redshift cluster** to use Spectrum.
*   Query executed by Spectrum nodes (separate from compute nodes).

### Exam Tips
*   Redshift = **OLAP, data warehouse, analytics** (not OLTP — that's RDS/Aurora).
*   Redshift is **NOT serverless** by default (Redshift Serverless exists but is different).
*   **Columnar** storage, MPP, SQL.
*   "Analytics on structured data at scale" → **Redshift**.
*   Redshift vs Athena: Redshift = **loaded data, complex queries, joins**; Athena = **ad-hoc S3 queries**.

## 3. Amazon OpenSearch (ex: ElasticSearch)

Amazon OpenSearch is a managed service for **search and analytics** — successor to Amazon Elasticsearch Service.

### Key Features
*   **Full-text search**, partial matches, fuzzy search.
*   Complement to other databases (search capability on top of DynamoDB, RDS, etc.).
*   Comes with **OpenSearch Dashboards** (visualization, like Kibana).
*   Managed cluster or **Serverless** mode.
*   Does **NOT support SQL natively** (uses its own query DSL, but SQL plugin available).
*   Security through **Cognito**, **IAM**, **KMS encryption**, **TLS**.

### Common Patterns
*   **DynamoDB → DynamoDB Streams → Lambda → OpenSearch** (search on DynamoDB data).
*   **CloudWatch Logs → Subscription Filter → Lambda → OpenSearch** (log analytics).
*   **Kinesis Data Streams/Firehose → OpenSearch** (real-time analytics).

### Exam Tips
*   OpenSearch = **search and analytics** engine.
*   "Search functionality on top of a database" → **OpenSearch**.
*   "Log analytics" or "full-text search" → **OpenSearch**.

## 4. Amazon EMR (Elastic MapReduce)

Amazon EMR is a **managed Hadoop cluster** service for big data processing.

### Key Features
*   Creates **Hadoop clusters** (hundreds of EC2 instances) for big data.
*   Supports **Apache Spark, HBase, Presto, Flink**, and more.
*   Auto-scaling, integrated with **Spot Instances** for cost savings.
*   Use Cases: Data processing, machine learning, web indexing, big data analytics.

### Node Types
*   **Master Node**: Manage the cluster, coordinate, health checks — long running.
*   **Core Node**: Run tasks and store data — long running.
*   **Task Node**: Only run tasks (no storage) — usually Spot instances.

### Exam Tips
*   EMR = **managed Hadoop/Spark** for big data processing.
*   "Hadoop", "Spark", "HBase", "big data processing" → **EMR**.

## 5. Amazon QuickSight

Amazon QuickSight is a **serverless**, machine learning-powered **BI (Business Intelligence)** service for interactive dashboards.

### Key Features
*   **Serverless**, auto-scaling, per-session pricing.
*   Fast, ML-powered visualizations and insights.
*   Data sources: RDS, Aurora, Redshift, Athena, S3, DynamoDB, on-premises databases.
*   **SPICE engine**: In-memory computation for imported data.
*   **Column-Level Security (CLS)** for fine-grained access control.

### Use Cases
*   Business analytics, dashboards, ad-hoc analysis.
*   Visualizations and reports embedded in applications.

### Exam Tips
*   QuickSight = **serverless BI dashboards/visualizations**.
*   "Dashboard", "visualization", "BI" → **QuickSight**.

## 6. AWS Glue

AWS Glue is a **managed ETL (Extract, Transform, Load)** service for preparing and transforming data for analytics.

### Key Features
*   **Serverless**, fully managed.
*   **Glue Data Catalog**: Central metadata repository — catalog of datasets.
    *   Can be used by Athena, Redshift Spectrum, and EMR to discover data.
*   **Glue Job Bookmarks**: Prevent re-processing old data.
*   **Glue Elastic Views**: Combine and replicate data across data stores using SQL.
*   **Glue DataBrew**: Clean and normalize data using pre-built transformations.
*   **Glue Studio**: Visual interface to create, run, and monitor ETL jobs.
*   **Glue Streaming ETL**: Built on Apache Spark Structured Streaming (real-time).

### Common Pattern
```
S3 / RDS → Glue ETL → Redshift (data warehouse)
S3 → Glue Data Catalog → Athena (query)
```

### Exam Tips
*   Glue = **serverless ETL**.
*   **Glue Data Catalog** = metadata catalog for Athena/Redshift/EMR.
*   "ETL", "transform data", "prepare data for analytics" → **Glue**.
*   Glue can convert data to **Parquet** format (optimize for Athena).

## 7. AWS Lake Formation

AWS Lake Formation makes it easy to set up a **secure Data Lake** in days.

### Key Features
*   **Data Lake** = central place to store all structured and unstructured data at any scale.
*   Automates: data collection, cleansing, cataloging, transformation, deduplication (using ML).
*   Combines **structured** and **unstructured** data in the data lake.
*   Built on top of **AWS Glue** (uses Glue under the hood).
*   **Fine-grained access control** at row and column level.
*   Central place to manage **security and access** for all data lake data.

### Exam Tips
*   Lake Formation = **build a data lake** with centralized security.
*   "Data lake", "centralized permissions", "fine-grained access" → **Lake Formation**.
*   Uses Glue under the hood but adds **security layer**.

## 8. Amazon Managed Service for Apache Flink

Managed service to run **Apache Flink** applications for **real-time stream processing**.

### Key Features
*   Process and analyze **streaming data** in real-time.
*   Sources: **Kinesis Data Streams**, **Amazon MSK** (Kafka).
*   Write applications in **Java, Scala, SQL**.
*   Fully managed — auto-scaling, provisioning, snapshots.
*   Does **NOT read from Kinesis Data Firehose** (read from Streams or MSK).

### Exam Tips
*   Managed Flink = **real-time stream processing** with Flink.
*   Sources: Kinesis Data Streams or MSK (NOT Firehose).
*   "Apache Flink", "real-time stream analytics with code" → **Managed Flink**.

## 9. Amazon MSK (Managed Streaming for Apache Kafka)

Amazon MSK is a **fully managed Apache Kafka** service on AWS.

### Key Features
*   **Apache Kafka** = open-source platform for real-time streaming data pipelines.
*   Alternative to **Kinesis** for streaming data.
*   MSK creates and manages **Kafka brokers** and **Zookeeper** nodes for you.
*   Deploy in your **VPC**, Multi-AZ (up to 3 for HA).
*   Data stored on **EBS volumes** for as long as you want.
*   **MSK Serverless**: Run Kafka without managing capacity.

### MSK vs Kinesis Data Streams

| Feature | MSK | Kinesis Data Streams |
|---|---|---|
| **Message size** | 1MB default (configurable higher) | 1MB max |
| **Retention** | As long as you want | 1–365 days |
| **Streams/Partitions** | Kafka topics with partitions | Shards |
| **Protocol** | Kafka protocol | AWS proprietary |
| **Use Case** | Already use Kafka, need Kafka features | AWS-native streaming |

### Exam Tips
*   MSK = **managed Kafka** on AWS.
*   "Apache Kafka", "Kafka migration" → **MSK**.
*   MSK vs Kinesis: MSK = open-source Kafka; Kinesis = AWS-native.

## 10. Big Data Ingestion Pipeline

Architecture pattern for ingesting, transforming, and querying big data — **fully serverless**.

### Example Architecture
```
IoT Devices → Kinesis Data Streams → Kinesis Data Firehose → S3 (ingestion bucket)
                                          ↓ (transform via Lambda)
S3 → SQS → Lambda → Athena (query) → S3 (reporting bucket) → QuickSight (dashboard)
S3 → Glue ETL (catalog + transform) → Redshift (warehouse)
```

### Key Services in the Pipeline
*   **Kinesis Data Streams**: Real-time data ingestion.
*   **Kinesis Data Firehose**: Near real-time delivery to S3.
*   **Lambda**: Data transformation.
*   **S3**: Storage (data lake).
*   **Glue**: ETL + Data Catalog.
*   **Athena**: Serverless SQL query on S3.
*   **Redshift**: Data warehouse for complex analytics.
*   **QuickSight**: Dashboards and visualizations.

### Exam Tips
*   This is a **common exam scenario** — know how to chain these services.
*   Real-time ingestion → **Kinesis Data Streams**.
*   Near real-time to S3 → **Kinesis Data Firehose**.
*   Query S3 → **Athena**.
*   Dashboard → **QuickSight**.
*   ETL → **Glue**.
*   Data warehouse → **Redshift**.

---

<a id="vietnamese-version"></a>

# Data & Analytics

## 1. Amazon Athena

Amazon Athena là dịch vụ **truy vấn serverless** để phân tích dữ liệu trong **Amazon S3** bằng **SQL**.

### Tính năng chính
*   **Serverless** — không quản lý hạ tầng.
*   Truy vấn dữ liệu trực tiếp trên **S3** bằng **SQL** chuẩn (dựa trên **Presto**).
*   Hỗ trợ **CSV, JSON, ORC, Avro, Parquet**.
*   **Trả per query** — $5 mỗi TB dữ liệu quét.
*   Thường dùng với **Amazon QuickSight** cho dashboards.

### Cải thiện hiệu suất
*   Dùng **dữ liệu dạng cột** (Parquet hoặc ORC) — giảm dữ liệu quét đáng kể.
*   **Nén** dữ liệu (gzip, snappy, zstd).
*   **Phân vùng** dữ liệu trong S3 (ví dụ: `s3://bucket/year=2024/month=01/`).
*   Dùng **files lớn** (> 128MB) để giảm overhead.

### Federated Query
*   Truy vấn dữ liệu từ **nhiều nguồn** (RDS, DynamoDB, Redshift, CloudWatch Logs) qua **Lambda Data Source Connectors**.

### Exam Tips
*   Athena = **serverless SQL trên S3**.
*   "Phân tích dữ liệu trong S3" hoặc "query S3 logs" → **Athena**.
*   Dùng **Parquet/ORC** để tối ưu chi phí và hiệu suất.

## 2. Amazon Redshift

Amazon Redshift là **data warehouse được quản lý** cho **OLAP** — analytics và kho dữ liệu.

### Tính năng chính
*   **Lưu trữ dạng cột** — hiệu suất gấp 10 lần các data warehouse khác.
*   **MPP** (Massively Parallel Query Execution).
*   SQL (tương thích PostgreSQL).
*   Tích hợp **QuickSight** và **Tableau** cho BI.
*   Load dữ liệu từ S3, DynamoDB, DMS.

### Redshift Cluster
*   **Leader Node**: Planning, aggregation.
*   **Compute Nodes**: Thực hiện queries (tối đa 128 nodes).
*   **Không có Multi-AZ**. DR: dùng **snapshots** sang region khác.

### Redshift Spectrum
*   Query dữ liệu trong **S3 mà không cần load** vào Redshift.
*   Phải có **Redshift cluster** mới dùng Spectrum được.

### Exam Tips
*   Redshift = **OLAP, data warehouse, analytics** (không phải OLTP).
*   Redshift vs Athena: Redshift = **dữ liệu đã load, queries phức tạp**; Athena = **ad-hoc queries trên S3**.

## 3. Amazon OpenSearch (ex: ElasticSearch)

Dịch vụ được quản lý cho **tìm kiếm và phân tích**.

### Tính năng chính
*   **Full-text search**, tìm kiếm gần đúng, fuzzy search.
*   Bổ sung cho databases khác (thêm tìm kiếm cho DynamoDB, RDS).
*   Có **OpenSearch Dashboards** (trực quan hóa).
*   Managed cluster hoặc chế độ **Serverless**.

### Patterns phổ biến
*   **DynamoDB → Streams → Lambda → OpenSearch** (tìm kiếm trên DynamoDB).
*   **CloudWatch Logs → Lambda → OpenSearch** (log analytics).

### Exam Tips
*   OpenSearch = **search engine + log analytics**.
*   "Tìm kiếm" hoặc "log analytics" → **OpenSearch**.

## 4. Amazon EMR (Elastic MapReduce)

Dịch vụ **managed Hadoop cluster** cho xử lý big data.

### Tính năng chính
*   Tạo **Hadoop clusters** (hàng trăm EC2) cho big data.
*   Hỗ trợ **Spark, HBase, Presto, Flink**.
*   Auto-scaling, tích hợp **Spot Instances** tiết kiệm chi phí.

### Node Types
*   **Master Node**: Quản lý cluster — chạy dài hạn.
*   **Core Node**: Chạy tasks + lưu dữ liệu — chạy dài hạn.
*   **Task Node**: Chỉ chạy tasks (không lưu) — thường dùng Spot.

### Exam Tips
*   EMR = **managed Hadoop/Spark** cho big data.
*   "Hadoop", "Spark", "big data processing" → **EMR**.

## 5. Amazon QuickSight

Dịch vụ **BI (Business Intelligence) serverless** cho dashboards tương tác.

### Tính năng chính
*   **Serverless**, auto-scaling, tính phí per-session.
*   ML-powered visualizations.
*   Sources: RDS, Aurora, Redshift, Athena, S3.
*   **SPICE engine**: Tính toán in-memory cho dữ liệu imported.
*   **Column-Level Security (CLS)**.

### Exam Tips
*   QuickSight = **serverless BI dashboards**.
*   "Dashboard", "visualization", "BI" → **QuickSight**.

## 6. AWS Glue

Dịch vụ **ETL (Extract, Transform, Load) được quản lý** cho chuẩn bị dữ liệu analytics.

### Tính năng chính
*   **Serverless**, fully managed.
*   **Glue Data Catalog**: Kho metadata trung tâm — Athena, Redshift Spectrum, EMR dùng để discover data.
*   **Glue Job Bookmarks**: Ngăn xử lý lại dữ liệu cũ.
*   **Glue DataBrew**: Làm sạch dữ liệu bằng transformations có sẵn.
*   **Glue Studio**: Giao diện trực quan tạo và chạy ETL jobs.
*   **Glue Streaming ETL**: ETL real-time trên Apache Spark Structured Streaming.

### Exam Tips
*   Glue = **serverless ETL**.
*   **Glue Data Catalog** = catalog metadata cho Athena/Redshift/EMR.
*   "ETL", "transform data", "chuẩn bị dữ liệu" → **Glue**.
*   Glue chuyển đổi sang **Parquet** (tối ưu cho Athena).

## 7. AWS Lake Formation

Dịch vụ giúp thiết lập **Data Lake bảo mật** trong vài ngày.

### Tính năng chính
*   **Data Lake** = nơi lưu tập trung mọi dữ liệu có/không cấu trúc ở mọi quy mô.
*   Tự động: thu thập, làm sạch, catalog, transform, loại bỏ trùng lặp (dùng ML).
*   Dựa trên **AWS Glue** (dùng Glue bên dưới).
*   **Kiểm soát truy cập chi tiết** ở cấp row và column.

### Exam Tips
*   Lake Formation = **xây dựng data lake** với bảo mật tập trung.
*   "Data lake", "centralized permissions" → **Lake Formation**.

## 8. Amazon Managed Service for Apache Flink

Dịch vụ managed chạy ứng dụng **Apache Flink** cho **xử lý stream real-time**.

### Tính năng chính
*   Xử lý và phân tích **streaming data** real-time.
*   Sources: **Kinesis Data Streams**, **Amazon MSK** (Kafka).
*   Viết ứng dụng bằng **Java, Scala, SQL**.
*   **KHÔNG đọc từ Kinesis Data Firehose**.

### Exam Tips
*   Managed Flink = **stream processing real-time** với Flink.
*   Sources: Kinesis Data Streams hoặc MSK (KHÔNG phải Firehose).

## 9. Amazon MSK (Managed Streaming for Apache Kafka)

Amazon MSK là dịch vụ **Apache Kafka được quản lý** trên AWS.

### Tính năng chính
*   **Apache Kafka** = nền tảng mã nguồn mở cho streaming data pipelines.
*   Thay thế **Kinesis** cho streaming data.
*   MSK tạo và quản lý **Kafka brokers** và **Zookeeper** nodes.
*   Deploy trong **VPC**, Multi-AZ (tối đa 3 cho HA).
*   Dữ liệu trên **EBS volumes** — lưu bao lâu tùy ý.
*   **MSK Serverless**: Chạy Kafka không cần quản lý capacity.

### MSK vs Kinesis Data Streams

| Đặc điểm | MSK | Kinesis Data Streams |
|---|---|---|
| **Message size** | 1MB mặc định (configurable) | 1MB tối đa |
| **Retention** | Bao lâu tùy ý | 1–365 ngày |
| **Protocol** | Kafka protocol | AWS proprietary |
| **Use Case** | Đã dùng Kafka, cần Kafka features | AWS-native streaming |

### Exam Tips
*   MSK = **managed Kafka** trên AWS.
*   "Apache Kafka", "Kafka migration" → **MSK**.

## 10. Big Data Ingestion Pipeline

Pattern kiến trúc thu thập, transform, và query big data — **hoàn toàn serverless**.

### Kiến trúc ví dụ
```
IoT → Kinesis Streams → Firehose → S3 → Glue ETL → Redshift
                                      → Athena → QuickSight
```

### Services trong pipeline
*   **Kinesis Data Streams**: Thu thập dữ liệu real-time.
*   **Kinesis Data Firehose**: Gửi gần real-time tới S3.
*   **S3**: Lưu trữ (data lake).
*   **Glue**: ETL + Data Catalog.
*   **Athena**: Serverless SQL query trên S3.
*   **Redshift**: Data warehouse cho analytics phức tạp.
*   **QuickSight**: Dashboards.

### Exam Tips
*   Đây là **kịch bản thi phổ biến** — cần biết cách nối các services.
*   Real-time ingestion → **Kinesis Data Streams**.
*   Near real-time tới S3 → **Firehose**.
*   Query S3 → **Athena**. Dashboard → **QuickSight**. ETL → **Glue**.
