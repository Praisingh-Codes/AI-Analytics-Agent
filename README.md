#### Project Overview – DataPulse: AI Analytics Agent

<div align="justify">DataPulse is an intelligent multi-agent analytics system designed to turn raw CSV business data into automated KPIs, insights, and executive-ready reports.

This agent processes sales/retail datasets, detects schema automatically, computes financial KPIs and generates narrative summaries using Google Gemini (with automatic fallback to offline reporting when no model is available).</div>

It follows a modular architecture inspired by real industry data-analysis workflows.

![DataPulse AI Thumbnail](resources/card%20and%20thumbnail%20image.png)


#### Problem Statement

Small and medium businesses often lack data teams to interpret sales data or generate business-ready reports.

Manually performing analytics every day loading datasets, calculating KPIs, identifying trends and summarizing insights requires significant time and expertise.

These challenges include:

- Repetitive KPI calculations

- Difficulty identifying trends without dashboards

- No automated narrative reporting

- Time lost manually cleaning and inspecting CSV files

- Inconsistent insights due to manual interpretation

This results in slow decision-making and missed opportunities.

#### Solution Statement

DataPulse AI Analytics Agent automates the entire workflow:

✔ Automatically loads CSVs (with encoding fallback)

✔ Detects schema, data types, missing values, and sample rows

✔ Computes key financial KPIs:

- Total Revenue

- Total Cost

- Total Profit

- Average Revenue

- Average Profit

- Top 5 Products

✔ Auto-detects columns — no strict schema required

Revenue-like columns (sales, amount, total, price)

Cost-like columns (cost, cogs, expense)

Product-like columns (product, item, sku)

✔ Generates a business-ready narrative report using Gemini

(And falls back to a local text generator if Gemini is unavailable)

✔ Stores session history with previous insights

#### Architecture

![Architecture Diagram](resources/architecture%20Image.png)

Your architecture image corresponds exactly to the system described below:

-- DataPulseOrchestrator (Central Brain)

Coordinates the complete workflow:

- Ingestion

- KPI Computation

- Narrative Generation

- Session Memory

-- IngestionAgent

Handles:

- CSV loading

- Encoding fallback

- Schema extraction

- Profile extraction

-- AnalyticsAgent

Responsible for:

- KPI calculations

- Column detection

- Product ranking

-- NarrativeAgent

Uses Google Gemini to turn numbers into:

- Executive summaries

- Insights

- Recommendations

- Trend explanations

- Falls back to offline mode when no API key/model is available.

-- SessionStore

Stores:

- Business context

- Historical reports

- KPI history
  
Used for contextual multi-run analytics.


#### Project Structure

AI Analytics Agent/

├── data/

│   └── retail_sales_dataset.csv

├── resources/

│   ├── architecture_image.png

│   └── card_thumbnail_image.png

├── Analytics Agent Code.ipynb

└── requirements.txt


#### Workflow

1️⃣Load Dataset

CSV is ingested with auto-detected encoding.

2️⃣Inspect Schema

- Column names

- Data types

- Missing values

- First 5 rows

3️⃣Compute KPIs

Auto-detected revenue and cost → profit calculations
Plus Top 5 products based on revenue.

4️⃣Generate Narrative

Gemini or fallback offline generator produces:

- Executive summary

- Key insights

- Recommendations

5️⃣Store Session

Memory used for multi-run analytics.

#### Value Statement

DataPulse transforms raw CSV files into actionable insights within seconds no Excel formulas, no BI dashboards and no manual calculations.

It saves hours of repetitive analytics work, enabling faster decision-making and better business strategy especially for small businesses without dedicated analysts.

▶ Installation

    python -m venv .venv

    .venv\Scripts\activate

    pip install -r requirements.txt

▶ Running the Notebook

Open:

Analytics Agent Code.ipynb

Run all cells and execute:

    csv_path = "data/retail_sales_dataset.csv"

    result = orchestrator.run_sales_report(csv_path, "My Retail Co.", "Retail")

    result["report"]
