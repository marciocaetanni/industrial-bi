# Industrial BI Platform (Cláudio/MG)

An end-to-end Data Engineering and Business Intelligence platform designed to analyze the industrial sector of Cláudio, Minas Gerais, leveraging Brazilian open public datasets.

[![Python](https://img.shields.io/badge/Python-3.13-blue?logo=python&logoColor=white)](https://www.python.org)

[![Java](https://img.shields.io/badge/Java-25-red?logo=openjdk&logoColor=white)](https://www.oracle.com/java/)

[![React](https://img.shields.io/badge/React-19-61DAFB?logo=react&logoColor=black)](https://react.dev)

[![MIT License](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

---

## 📌 Project Overview

This architecture integrates multiple public data sources, automates scheduled data ingestion and transformation pipelines, hosts a structured relational Data Warehouse in PostgreSQL, and performs statistical analyses. The data is exposed via a production-grade RESTful API built with Spring Boot and visualized through an interactive, responsive analytical dashboard built with React.

The primary objective of this repository is to demonstrate production-ready skills across **Data Engineering**, **Backend Development**, **Frontend Engineering**, and **Advanced Data Analytics** applied to a real-world regional economic use case.

### Key Features
*   **Automated ETL Pipelines:** Orchestrated data workflows managing data extraction, cleansing, and normalization.
*   **Multi-Source Ingestion:** Seamless integration with various public REST APIs and large-scale flat CSV datasets.
*   **Relational Data Warehouse:** Optimized PostgreSQL schema tailored for analytical query performance.
*   **Advanced Analytics:** Built-in statistical analysis and predictive modeling modules.
*   **Decoupled Micro-Architecture:** Fully containerized environment ensuring seamless deployment across different systems.

---

## 📐 System Architecture

```text
                Public Data Sources
       (IBGE, RAIS, COMEX, etc.)
                     │
                     ▼
             Apache Airflow
                     │
                     ▼
              Python ETL
     Extract → Transform → Load
                     │
                     ▼
                PostgreSQL
                     │
                     ▼
              Spring Boot API
                     │
                     ▼
               React Frontend
```

---

## 🛠️ Tech Stack

### Data Engineering & DevOps
*   **Core Languages:** Python, SQL
*   **Data Pipelines:** Pandas, Requests, Apache Airflow
*   **Database:** PostgreSQL (Data Warehousing & Relational Storage)
*   **Infrastructure:** Docker, Docker Compose, Git

### Backend Engineering
*   **Core Language:** Java
*   **Framework:** Spring Boot (REST API Execution)
*   **Data Access:** Spring Data JPA, Hibernate

### Frontend Engineering
*   **Core Language:** TypeScript
*   **Framework:** React
*   **Routing & UI:** React Router, Recharts (Data Visualization Layouts)

---

## 🗂️ Project Structure

```text
industrial-bi/
├── .gitignore          # Git exclusion rules
├── docker-compose.yml  # Multi-container orchestration configurations
├── requirements.txt    # Python application dependencies
├── README.md           # Project documentation
├── airflow/            # Airflow DAGs and orchestration workflows
├── analytics/          # Jupyter notebooks, statistical and predictive models
├── backend/            # Spring Boot application source code
├── database/           # SQL migration scripts and schemas
├── etl/                # Python ETL processing scripts
└── frontend/           # React frontend single-page application
```

---

## ⚙️ Data Pipeline (ETL)

The ETL pipeline operates on a decoupled architecture composed of three main processing stages:

### 1. Extract
Automated scripts ingest raw transactional and socio-economic data directly from open public API endpoints and downloadable large-scale flat files (`.csv`), including:
*   **IBGE:** Demographic, structural, and regional economic indices.
*   **RAIS:** Formal employment registries, wage distributions, and sector capacities.
*   **COMEX Stat:** Foreign trade balances, localized import/export volumes.

### 2. Transform
Raw datasets undergo strict data cleansing and validation routines within memory-optimized `pandas` DataFrames:
*   Deduplication of overlapping transactional rows.
*   Schema alignment, case normalization, and column renaming.
*   Data type casting (e.g., handling Unix/ISO dates, casting structural IDs).
*   Imputation and filtering of missing fields (`null` handling) and mathematical anomalies.
*   Relational merges and joins to generate consolidated analytical entities.

### 3. Load
The validated datasets are transactionally committed into a normalized PostgreSQL schema designed for high-availability reads.

---

## 📊 Analytics Framework

The platform supports multi-layered analytical operations developed directly within the Python environment:
*   **Descriptive Analytics:** Historical tracking of industrial output and localized labor market evolution.
*   **Diagnostic Analytics:** Identification of economic dependencies, export anomalies, and sector bottlenecks.
*   **Predictive Analytics:** Implementation of Machine Learning time-series forecasting models to project industrial growth and job market shifts.

---

## 🔌 API Endpoints

The Spring Boot application exposes secure, structured REST endpoints returning standardized `application/json` data models.

```http
GET /api/employment  - Retrieves temporal employment distributions and metrics
GET /api/exports     - Retrieves local export/import values and trade balance logs
GET /api/industries  - Lists registered active industrial entities and categorization
```

---

## 🚀 Getting Started & Installation

### Prerequisites
Ensure you have the following components globally installed:
*   **Python 3.10+** & **Pip**
*   **Java JDK 17+**
*   **Docker & Docker Compose**
*   **Git**

### Local Environment Setup

1. **Clone the repository:**
   ```bash
   git clone https://github.com/marciocaetanni/industrial-bi.git
   cd industrial-bi
   ```

2. **Initialize and isolate the Python environment:**
   ```bash
   # Create environment
   python -m venv venv

   # Activate environment (Windows PowerShell)
   .\venv\Scripts\Activate.ps1

   # Activate environment (Linux / macOS)
   source venv/bin/activate
   ```

3. **Install application dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Launch the containerized infrastructure:**
   ```bash
   docker compose up -d
   ```
   *This single command spins up the isolated PostgreSQL instance, Apache Airflow cluster, Spring Boot application, and the React client interface in detached mode.*

---

## 🔮 Future Roadmap

*   Deploy live Time-Series forecasting models directly to the web dashboard.
*   Implement JWT-based Authentication and explicit User Role management (`RBAC`).
*   Incorporate Automated PDF/Excel report generation modules.
*   Integrate Geospatial Analysis (`GIS` maps) to map active industrial hubs dynamically.
*   Introduce an AI-powered Natural Language interface allowing non-technical users to query the database using LLMs.

---

## 📄 License

This software is distributed under the terms of the [MIT License](LICENSE).
