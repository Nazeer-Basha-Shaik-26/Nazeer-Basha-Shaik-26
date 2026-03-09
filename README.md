<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0f2027,50:203a43,100:2c5364&height=200&section=header&text=Nazeer%20Basha%20Shaik&fontSize=52&fontColor=00d4ff&fontAlignY=38&desc=Senior%20Data%20Engineer%20%7C%20GCP%20%7C%20BigQuery%20%7C%20Cloud%20Migration%20Specialist&descAlignY=60&descSize=18&descColor=a8dadc&animation=fadeIn" width="100%"/>

<br/>

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Nazeer%20Basha%20Shaik-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/nazeer-basha-data-engineer)
[![Email](https://img.shields.io/badge/Gmail-nazeershaikwf%40gmail.com-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:nazeershaikwf@gmail.com)
[![Phone](https://img.shields.io/badge/Call-%2B1(980)--483--2369-25D366?style=for-the-badge&logo=whatsapp&logoColor=white)](tel:+19804832369)
[![GCP Certified](https://img.shields.io/badge/GCP-Professional%20Data%20Engineer-4285F4?style=for-the-badge&logo=google-cloud&logoColor=white)](https://cloud.google.com/certification/data-engineer)
[![AWS Certified](https://img.shields.io/badge/AWS-Certified%20Data%20Engineer-FF9900?style=for-the-badge&logo=amazon-aws&logoColor=white)](https://aws.amazon.com/certification/)

</div>

---

## 👋 About Me

I'm **Nazeer Basha Shaik**, a **Senior Data Engineer** with **6+ years of experience** architecting and delivering enterprise-scale data platforms on **Google Cloud Platform (GCP)**. My core expertise lies in **cloud data migration** (Teradata/Oracle/SAS → GCP), building real-time and batch ETL/ELT pipelines, and designing BigQuery-based data warehouses that power analytics at organizations like **CVS Health** and **Wells Fargo**.

```
💼 Current Role  : Senior Data Engineer @ CVS Health, Dallas TX
📍 Location      : Charlotte, NC, USA
☁️  Speciality   : Teradata → GCP Migration | BigQuery | Dataflow | Airflow
🎓 Education     : M.S. Computer Science — NAU, USA
🏆 Certifications: GCP Professional Data Engineer | AWS Data Engineer | IBM Hadoop
```

---

## 🏆 Certifications

<div align="center">

| Certification | Issuer | Badge |
|---|---|---|
| **Professional Data Engineer** | Google Cloud | ![GCP](https://img.shields.io/badge/GCP-Professional-4285F4?style=flat-square&logo=google-cloud&logoColor=white) |
| **Certified Data Engineer** | Amazon Web Services | ![AWS](https://img.shields.io/badge/AWS-Certified-FF9900?style=flat-square&logo=amazon-aws&logoColor=white) |
| **Hadoop Fundamentals** | IBM | ![IBM](https://img.shields.io/badge/IBM-Hadoop-052FAD?style=flat-square&logo=ibm&logoColor=white) |

</div>

---

## 🚀 Featured Project — Teradata to GCP Migration (Wells Fargo)

> **Enterprise Data Warehouse Migration | Teradata → BigQuery (GCP)**
> *Client: Wells Fargo, Charlotte, NC | Aug 2023 – Dec 2023*

Full-scale migration of Wells Fargo's Teradata enterprise data warehouse to **Google Cloud Platform** — covering BTEQ-to-BigQuery SQL conversion, live data synchronization, schema validation, and automated production deployment via Git CI/CD pipelines.

### 🔁 Migration Architecture

```
┌──────────────────────────────────────────────────────────────────────┐
│                    TERADATA → GCP MIGRATION PIPELINE                 │
│                                                                      │
│  Teradata (Source)        Conversion Layer            GCP (Target)   │
│  ┌───────────────┐        ┌──────────────────┐      ┌─────────────┐ │
│  │ .bteq scripts │──────► │ BTEQ → BQ SQL    │────► │ BQ SQL files│ │
│  │ Stored procs  │        │   Converter      │      └──────┬──────┘ │
│  │ TD Macros     │        │ + Schema Validator│             │        │
│  └───────────────┘        └──────────────────┘             ▼        │
│                                                     ┌─────────────┐ │
│  Git Pipeline                                       │ GCS Prod    │ │
│  ┌───────────────┐                                  │   Bucket    │ │
│  │ feature branch│── PR Review ──► main ───────────►│  (via CI/CD)│ │
│  └───────────────┘                                  └──────┬──────┘ │
│                                                            │        │
│                                                            ▼        │
│                                                     ┌─────────────┐ │
│                                                     │  BigQuery   │ │
│                                                     │  Warehouse  │ │
│                                                     └─────────────┘ │
└──────────────────────────────────────────────────────────────────────┘
```

### 📂 Repository Structure

```
teradata-to-gcp-migration/
│
├── 📁 bteq_scripts/                     # Original Teradata BTEQ source files
│   ├── extract_customer_txn.bteq
│   ├── transform_ledger_summary.bteq
│   └── load_account_dim.bteq
│
├── 📁 bqsql_converted/                  # Converted BigQuery SQL files
│   ├── extract_customer_txn.sql
│   ├── transform_ledger_summary.sql
│   └── load_account_dim.sql
│
├── 📁 scripts/
│   ├── bteq_to_bqsql_converter.py       # Core automated conversion engine
│   ├── validate_schema.py               # Pre/post migration schema validator
│   └── deploy_to_gcs.sh                 # GCS prod bucket deployment
│
├── 📁 tests/
│   ├── test_row_counts.sql
│   └── test_data_quality.sql
│
├── .github/workflows/
│   └── deploy_to_prod.yml               # CI/CD: auto-deploy on merge to main
│
└── README.md
```

### ⚙️ BTEQ → BigQuery SQL: Key Syntax Conversions

| Teradata BTEQ | BigQuery SQL | Notes |
|---|---|---|
| `CREATE VOLATILE TABLE` | `CREATE TEMP TABLE` | Session-scoped temp tables |
| `TD_MONTH_BEGIN(col)` | `DATE_TRUNC(col, MONTH)` | Date truncation |
| `CURRENT_DATE - 1` | `DATE_SUB(CURRENT_DATE(), INTERVAL 1 DAY)` | Date arithmetic |
| `ZEROIFNULL(col)` | `IFNULL(col, 0)` | Null coalescing |
| `NULLIFZERO(col)` | `NULLIF(col, 0)` | Zero-to-null |
| `SAMPLE N` | `LIMIT N` | Row sampling |
| `.EXEC macro_name` | `CALL procedure_name()` | Macro → Stored Proc |
| `PRIMARY INDEX (col)` | *(Removed — use CLUSTER BY)* | Clustering strategy |
| `VARCHAR(n)` | `STRING` | String types |
| `BYTEINT / SMALLINT` | `INT64` | Integer types |

---

### 🔄 Real Conversion Example — Ledger Summary Transform

**Before (BTEQ — Teradata):**
```sql
.LOGON tdhost/username,password;
.SET SESSIONS 4;

CREATE VOLATILE TABLE vt_ledger_summary AS (
    SELECT
        account_id,
        TD_MONTH_BEGIN(txn_date)         AS month_start,
        SUM(txn_amount)                  AS total_amount,
        ZEROIFNULL(SUM(fee_amount))      AS total_fees,
        COUNT(txn_id)                    AS txn_count
    FROM banking_db.transactions
    WHERE txn_date BETWEEN '2023-01-01' AND CURRENT_DATE - 1
      AND status_code NOT IN (
          SEL bad_code FROM ref_db.invalid_status
      )
    GROUP BY 1, 2
) WITH DATA PRIMARY INDEX (account_id)
ON COMMIT PRESERVE ROWS;

INSERT INTO reporting.ledger_summary SELECT * FROM vt_ledger_summary;

.LOGOFF;
.QUIT;
```

**After (BigQuery SQL — GCP):**
```sql
-- ============================================================
-- Converted from BTEQ : transform_ledger_summary.bteq
-- Target              : Google BigQuery (GCP)
-- Project             : Wells Fargo Data Migration
-- Engineer            : Nazeer Basha Shaik
-- ============================================================

CREATE TEMP TABLE tmp_ledger_summary AS (
    SELECT
        account_id,
        DATE_TRUNC(txn_date, MONTH)           AS month_start,
        SUM(txn_amount)                       AS total_amount,
        IFNULL(SUM(fee_amount), 0)            AS total_fees,
        COUNT(txn_id)                         AS txn_count
    FROM `wf-gcp-prod.banking_db.transactions`
    WHERE txn_date BETWEEN '2023-01-01'
      AND DATE_SUB(CURRENT_DATE(), INTERVAL 1 DAY)
      AND status_code NOT IN (
          SELECT bad_code FROM `wf-gcp-prod.ref_db.invalid_status`
      )
    GROUP BY 1, 2
);

INSERT INTO `wf-gcp-prod.reporting.ledger_summary`
SELECT * FROM tmp_ledger_summary;
```

---

### 🚢 Git-Based CI/CD Deployment to GCS Production Bucket

```yaml
# .github/workflows/deploy_to_prod.yml
name: Deploy BQ SQL → GCS Production Bucket

on:
  push:
    branches: [main]
    paths: ['bqsql_converted/**']

jobs:
  validate-and-deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3

      - name: Authenticate to GCP
        uses: google-github-actions/auth@v1
        with:
          credentials_json: ${{ secrets.GCP_SA_KEY }}

      - name: Validate SQL (dry-run)
        run: |
          for file in bqsql_converted/*.sql; do
            bq query --dry_run --use_legacy_sql=false < "$file"
          done

      - name: Deploy to GCS Prod Bucket
        run: |
          gsutil -m cp -r bqsql_converted/*.sql \
            gs://${{ secrets.GCS_PROD_BUCKET }}/bqsql/$(date +%Y%m%d)/
```

### 📊 Migration Impact @ Wells Fargo

```
📦 BTEQ scripts converted           :  180+ scripts
✅ Automated conversion success rate :  98.3%
⚡ Query performance improvement     :  ~45% faster on BigQuery vs Teradata
🔁 CI/CD deployments to GCS         :  40+ successful pipeline runs
🧪 Data validation checks passed    :  100% — zero data loss confirmed
🔄 Live sync during migration        :  Real-time Teradata ↔ GCP maintained
```

---

## 💼 Professional Experience

### 🏥 Senior Data Engineer — CVS Health, Dallas TX
**Jan 2024 – Present**

- Led and mentored a team of **6 data engineers** (onsite + offshore) delivering GCP data solutions aligned with business priorities
- Designed **dimensional data models** (star/snowflake schemas) supporting analytics and reporting layers in BigQuery
- Migrated legacy **Teradata and Oracle** ETL workflows to GCP-native solutions with benchmarking and full validation
- Migrated **SAS-based pipelines** to GCP BigQuery + Dataflow, reducing processing time by **60%** and infra cost by **35%**
- Engineered **time-partitioned and clustered BigQuery tables** cutting query scan cost significantly
- Built data ingestion frameworks using **GCP Pub/Sub + Dataflow** for near real-time event-driven pipelines
- Orchestrated complex ETL workflows via **Cloud Composer (Apache Airflow)** with SLA-based scheduling and retries
- Implemented **Python + Great Expectations** unit tests and validation rules for anomaly detection pre-load
- Developed **Terraform IaC** to provision BigQuery datasets, IAM roles, and Pub/Sub topics

### 🏦 Senior Data Engineer — Wells Fargo, Charlotte NC
**Aug 2023 – Dec 2023**

- Designed and implemented ETL pipelines on **GCP Cloud Dataflow + BigQuery** to automate full Teradata migration
- Converted complex **Teradata SQL, stored procedures, and BTEQ macros to BigQuery SQL**, improving query efficiency
- Maintained **live data sync** between Teradata and GCP throughout migration — zero data loss on banking transactions
- Automated ETL workflows using **Google Cloud Composer**, eliminating manual intervention during migration
- Built **PySpark streaming applications** reading from Kafka, persisting to HBase and Cassandra
- Designed **Snowflake financial data models** covering GL data, transactional records, and regulatory reporting
- Deployed **GCP Cloud Functions** to automate event-driven data workflow triggers

### 🏢 Data Engineer — TCS, Hyderabad, India
**Jul 2019 – Aug 2022**

- Built ETL pipelines on **Azure Data Factory** for Azure Data Lake, SQL, and Blob Storage ingestion
- Processed insurance data (policyholder, claims, external sources) using **Azure Databricks**
- Designed ETL frameworks with **SSIS** using Lookup, Aggregate, Conditional Split transformations
- Developed **Informatica** mappings and workflows for data extraction, validation, and transformation
- Implemented **data partitioning and bucketing** in Apache Hive for optimized query performance
- Created **Power BI and Tableau** dashboards and KPI scorecards for stakeholder reporting

---

## 🧰 Tech Stack

<div align="center">

**Cloud & Data Warehouse**

![GCP](https://img.shields.io/badge/Google%20Cloud-4285F4?style=for-the-badge&logo=google-cloud&logoColor=white)
![BigQuery](https://img.shields.io/badge/BigQuery-4285F4?style=for-the-badge&logo=google-bigquery&logoColor=white)
![Snowflake](https://img.shields.io/badge/Snowflake-29B5E8?style=for-the-badge&logo=snowflake&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-FF9900?style=for-the-badge&logo=amazon-aws&logoColor=white)
![Azure](https://img.shields.io/badge/Azure-0078D4?style=for-the-badge&logo=microsoft-azure&logoColor=white)

**Processing & Orchestration**

![Apache Airflow](https://img.shields.io/badge/Apache%20Airflow-017CEE?style=for-the-badge&logo=apache-airflow&logoColor=white)
![Apache Spark](https://img.shields.io/badge/Apache%20Spark-E25A1C?style=for-the-badge&logo=apache-spark&logoColor=white)
![Apache Kafka](https://img.shields.io/badge/Apache%20Kafka-231F20?style=for-the-badge&logo=apache-kafka&logoColor=white)
![Apache Beam](https://img.shields.io/badge/Apache%20Beam-E6526F?style=for-the-badge&logo=apache&logoColor=white)
![dbt](https://img.shields.io/badge/dbt-FF694B?style=for-the-badge&logo=dbt&logoColor=white)

**Languages & DevOps**

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-CC2927?style=for-the-badge&logo=microsoft-sql-server&logoColor=white)
![Scala](https://img.shields.io/badge/Scala-DC322F?style=for-the-badge&logo=scala&logoColor=white)
![Git](https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white)
![Terraform](https://img.shields.io/badge/Terraform-7B42BC?style=for-the-badge&logo=terraform&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-2088FF?style=for-the-badge&logo=github-actions&logoColor=white)

**Databases & Visualization**

![Teradata](https://img.shields.io/badge/Teradata-F37440?style=for-the-badge&logo=teradata&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-316192?style=for-the-badge&logo=postgresql&logoColor=white)
![Tableau](https://img.shields.io/badge/Tableau-E97627?style=for-the-badge&logo=tableau&logoColor=white)
![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=power-bi&logoColor=black)

</div>

---

## 📊 GitHub Stats

<div align="center">

![Nazeer's GitHub Stats](https://github-readme-stats.vercel.app/api?username=Nazeer-Basha-Shaik-26&show_icons=true&theme=dark&bg_color=0d1117&title_color=00d4ff&icon_color=00d4ff&text_color=c9d1d9&border_color=30363d)

![Top Languages](https://github-readme-stats.vercel.app/api/top-langs/?username=Nazeer-Basha-Shaik-26&layout=compact&theme=dark&bg_color=0d1117&title_color=00d4ff&text_color=c9d1d9&border_color=30363d)

</div>

---

## 📁 Repository Highlights

| Repository | Description | Stack |
|---|---|---|
| [🔄 teradata-to-gcp-migration](https://github.com/Nazeer-Basha-Shaik-26/teradata-to-gcp-migration) | Full BTEQ → BigQuery migration with CI/CD (Wells Fargo) | Python, BQ SQL, GCP, GitHub Actions |
| [🛠️ bteq-bqsql-converter](https://github.com/Nazeer-Basha-Shaik-26/bteq-bqsql-converter) | Automated BTEQ to BigQuery SQL converter engine | Python, Regex, AST Parsing |
| [⚡ gcp-dataflow-pipelines](https://github.com/Nazeer-Basha-Shaik-26/gcp-dataflow-pipelines) | Production Apache Beam/Dataflow ETL pipelines | Python, Apache Beam, GCP |
| [🎼 airflow-dags-gcp](https://github.com/Nazeer-Basha-Shaik-26/airflow-dags-gcp) | Cloud Composer / Airflow DAGs for GCP workflows | Python, Airflow, GCP |
| [🧪 bq-data-quality-framework](https://github.com/Nazeer-Basha-Shaik-26/bq-data-quality-framework) | Great Expectations data quality checks for BigQuery | Python, SQL, dbt |

---

## 🤝 Open to Opportunities

I'm actively seeking **Senior Data Engineer** and **Cloud Data Architect** roles focused on **GCP**, **BigQuery**, and large-scale **cloud data migrations**.

📧 **nazeershaikwf@gmail.com** &nbsp;|&nbsp; 📞 **+1 (980)-483-2369**

<div align="center">

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Let's%20Connect-0077B5?style=for-the-badge&logo=linkedin)](https://www.linkedin.com/in/nazeer-basha-data-engineer)
[![Email](https://img.shields.io/badge/Email-nazeershaikwf%40gmail.com-D14836?style=for-the-badge&logo=gmail)](mailto:nazeershaikwf@gmail.com)

</div>

---

<div align="center">
<img src="https://capsule-render.vercel.app/api?type=waving&color=0:2c5364,50:203a43,100:0f2027&height=120&section=footer" width="100%"/>

*"Migrating enterprise data at scale — from Teradata to BigQuery, one pipeline at a time."*

</div>
