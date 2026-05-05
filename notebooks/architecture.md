# Pipeline Architecture

```mermaid
flowchart LR
    A[📦 Raw CSV Files\n9 Olist datasets] --> B[🥉 Bronze Layer\nDelta Lake\nRaw ingestion]
    B --> C[🥈 Silver Layer\nPySpark\nCleaning & Joining\n38 columns]
    C --> D[🥇 Gold Layer\nDatabricks SQL\n4 business tables]
    D --> E[🤖 ML Layer\nRandom Forest\nMLflow tracking]
    D --> F[🧠 GenAI Layer\nHugging Face BERT\nSentiment Analysis]
```

## Data flow

| Layer | Tool | Input | Output |
|---|---|---|---|
| Bronze | Delta Lake | 9 CSV files | 9 raw Delta tables |
| Silver | PySpark | 9 Delta tables | 1 master table, 38 columns |
| Gold | Databricks SQL | Master table | 4 aggregation tables |
| ML | MLflow + Scikit-learn | Gold data | Review score predictor |
| GenAI | Hugging Face | Review text | Sentiment labels |
