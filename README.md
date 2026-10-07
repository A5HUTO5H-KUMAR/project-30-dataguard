# DataGuard — Pipeline Health & Data Quality Dashboard

> An end-to-end data quality and pipeline observability platform built with Databricks, PySpark, Snowflake, Next.js, React, and TypeScript.

## 📌 Overview

**DataGuard** is an end-to-end **Data Quality & Pipeline Health Monitoring System** designed to detect, isolate, quantify, and visualize data-quality issues across an order-processing pipeline.

The project follows a modern:

**Raw → Bronze → Silver → Gold → Snowflake → Dashboard**

architecture.

The system validates incoming data, identifies data-quality issues, separates accepted and rejected records, calculates quality metrics, monitors data freshness, and presents the results through an operational dashboard.

---

## 🏗️ Architecture

```text
                Data Generator
                      │
                      ▼
               Raw CSV Files
                      │
                      ▼
              ┌───────────────┐
              │    BRONZE     │
              │               │
              │ Raw Data      │
              │ Metadata      │
              │ Load Manifest │
              └───────┬───────┘
                      │
                      ▼
              ┌───────────────┐
              │    SILVER     │
              │               │
              │ Validation    │
              │ Casting       │
              │ Deduplication │
              │ Referential   │
              │ Range Checks  │
              └───────┬───────┘
                      │
             ┌────────┴────────┐
             │                 │
             ▼                 ▼
       Accepted Data      Rejected Data
             │                 │
             └────────┬────────┘
                      │
                      ▼
              ┌───────────────┐
              │     GOLD      │
              │               │
              │ DQ Results    │
              │ Freshness     │
              └───────┬───────┘
                      │
                      ▼
              ┌───────────────┐
              │   SNOWFLAKE   │
              │               │
              │   DATAGUARD   │
              │    ANALYTICS  │
              └───────┬───────┘
                      │
                      ▼
              ┌───────────────┐
              │    NEXT.JS    │
              │    REACT      │
              │   DASHBOARD   │
              └───────────────┘

🛠️ Technology Stack

| Layer                           | Technology |
|---|---|
| Data Engineering                 | Databricks |
| Data Processing                  | PySpark |
| Data Warehouse                   | Snowflake |
| Frontend                         | Next.js |
| UI                               | React + TypeScript |
| Styling                          | Tailwind CSS |
| Charts                           | Recharts |
| Icons                            | Lucide React |
| Version Control                  | Git / GitHub |
| Deployment Target                | Vercel |

📊 Dataset
The project uses a deterministic data generator with controlled data-quality problems.
Historical Data
- 50,000 historical orders
- 3,000 customer records
- 10 historical order loads
- 10 historical customer loads
New Incoming Data
Six new order files are generated:
File	Rows	Purpose
day_11	5,000	Clean data
day_12	5,000	Invalid quantity values
day_13	5,000	Duplicate order IDs
day_14	5,000	Column contract violation
day_15	0	Empty file
day_16	5,000	Unknown customers and invalid timestamps


Total incoming rows: 25,000
Expected rejected records: 500

🚀 Local Setup
Prerequisites
- Node.js
- npm
- Git
- Databricks
- Snowflake
Install Dependencies
npm install

Start Development Server
npm run dev

Open:
http://localhost:3000

Production Build
npm run build

Start Production Server
npm start

🔐 Environment Variables
Create a .env.local file in the project root:
SNOWFLAKE_ACCOUNT=your_account
SNOWFLAKE_USERNAME=your_username
SNOWFLAKE_PASSWORD=your_password
SNOWFLAKE_WAREHOUSE=COMPUTE_WH
SNOWFLAKE_DATABASE=DATAGUARD
SNOWFLAKE_SCHEMA=ANALYTICS
SNOWFLAKE_ROLE=your_role

Never commit .env.local or Snowflake credentials to GitHub.
For production deployment, a restricted read-only Snowflake role should be used instead of an administrative role.
🔮 Future Enhancements
- Complete live Snowflake dashboard integration
- Automated Databricks Jobs
- Pipeline failure alerts
- Email/Slack notifications
- Historical quality trends
- Rule-level drill-down
- Load comparison
- Automated testing
- CI/CD pipeline
- Production Vercel deployment
- Restricted Snowflake read-only role
- Role-based dashboard access
