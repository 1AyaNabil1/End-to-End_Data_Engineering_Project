# End-to-End Data Engineering Project: dbt, Snowflake & Apache Airflow

## 🚀 Overview

This project represents a **complete end-to-end data engineering pipeline**, leveraging the power of **dbt (Data Build Tool)** for transformation, **Snowflake** for cloud warehousing, and **Apache Airflow** for orchestration. It covers the full data lifecycle — from ingestion and transformation to testing and scheduling — following modern data stack best practices.

## 🧰 Tech Stack

* **dbt Core** – SQL-based data transformation and modeling
* **Snowflake** – Scalable, cloud-based data warehouse
* **Apache Airflow** – Workflow scheduling and orchestration
* **Python** – Used for scripting and automation (Airflow DAGs)
* **Git** – Version control and collaboration

## 🗂️ Project Structure

```bash
snowflake_data_project/
├── Data_Files/                # Raw input data in CSV format
├── models/                   # dbt models: staging and marts layers
│   ├── staging/              # Cleansed layer
│   ├── marts/                # Final business metrics
│   └── example/              # sources.yml for raw data sources
├── tests/                    # dbt test configs
├── seeds/                    # Seed files (optional static data)
├── snapshots/                # (Future use) Data snapshots for slowly changing dimensions
├── dbt_core_dag.py           # Airflow DAG to run dbt workflow
├── dbt_project.yml           # dbt project configuration file
├── .gitignore                # Git ignored files
├── .gitattributes            # Git attribute settings
└── README.md                 # Project documentation
```

## ⚙️ Setup & Installation

### 1. 📥 Clone the Repository

```bash
git clone https://github.com/1AyaNabil1/End-to-End_Data_Engineering_Project.git
cd End-to-End_Data_Engineering_Project
```

### 2. 🐍 Set Up a Virtual Environment

```bash
python -m venv venv
source venv/bin/activate    # Mac/Linux
venv\Scripts\activate       # Windows
```

### 3. 🔐 Configure dbt Connection to Snowflake

Update the `~/.dbt/profiles.yml` file with your credentials:

```yaml
snowflake_data_project:
  outputs:
    dev:
      account: <your_snowflake_account>
      user: dbt_user
      password: <your_password>
      role: ACCOUNTADMIN
      database: finance_db
      warehouse: finance_wh
      schema: raw
      type: snowflake
  target: dev
```

### 4. ▶️ Run dbt Models

```bash
dbt run           # Build models

# Optional: run tests

dbt test          # Run data quality tests
```

### 5. 📅 Start Apache Airflow (Local)

```bash
airflow standalone  # Launches webserver and scheduler
```

## ✅ Features Implemented

* Raw CSV ingestion defined in `sources.yml`
* Staging models for: customers, orders, products, and order\_items
* Mart model: `fct_daily_order_revenue`
* Automated data validation via dbt tests (e.g., accepted values, uniqueness)
* Scheduled execution via Airflow DAG (`dbt_core_dag.py`)

## 📌 Notes

* Make sure your Airflow environment has access to dbt CLI.
* Replace placeholder credentials before running.
* Extend the DAG with more granular dbt tasks if needed.

---

Made with ❤️ by Aya | [GitHub](https://github.com/1AyaNabil1)
