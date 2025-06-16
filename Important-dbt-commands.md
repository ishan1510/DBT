# 📘 Essential dbt CLI Commands for End-to-End Projects

## 🔧 Project Setup & Configuration
- `dbt init` – Create a new dbt project
- `dbt debug` – Test the connection and configuration
- `dbt deps` – Install packages listed in `packages.yml`
- `dbt clean` – Remove artifacts like logs and compiled files

## 🧱 Model Building & Running
- `dbt run` – Build models (transforms your SQL into tables/views)
- `dbt run --select model_name` – Run a specific model
- `dbt build` – Runs `run + test + seed + snapshot` in one command (dbt 1.4+)

## 🧪 Testing
- `dbt test` – Run schema and data tests
- `dbt test --select model_name` – Run tests on a specific model

## 🌱 Data Seeding
- `dbt seed` – Load CSV files in `/seeds` folder into your warehouse

## 🔍 Documentation & Lineage
- `dbt docs generate` – Generate documentation site
- `dbt docs serve` – Open the docs in a local browser

## 🔄 Snapshots
- `dbt snapshot` – Create historical snapshots of slowly changing dimensions

## 🧭 Model Selection & Dependencies
- `dbt run --select tag:tag_name` – Run models with a specific tag
- `dbt run --select +model_name` – Run the model and its dependencies
- `dbt run --select model_name+` – Run the model and all downstream models

---

> Use these commands throughout your dbt workflow – from project initialization to deployment and documentation.
