# Olist E-Commerce Lakehouse on Databricks

End-to-end data lakehouse pipeline built on Databricks Community Edition using the 
Brazilian E-Commerce Public Dataset by Olist (100,000 real orders).

## Architecture

See [detailed architecture](notebooks/architecture.md) for the full pipeline diagram.


Raw CSV Files → Bronze (Delta Lake) → Silver (PySpark) → Gold (Aggregations) → ML (MLflow) → GenAI (Hugging Face) → Streaming (Auto Loader)

## What this project covers

- **Bronze layer** — ingestion of 9 raw CSV files into Delta Lake
- **Silver layer** — data cleaning, deduplication, and joining of all 9 tables into a single master table with 38 columns using PySpark
- **Gold layer** — 4 business-ready aggregation tables covering sales by category, delivery performance, payment analysis, and customer satisfaction
- **ML layer** — Random Forest model predicting customer review scores (1-5), with experiment tracking and model versioning using MLflow
- **GenAI layer** — multilingual sentiment analysis on Portuguese customer reviews using a Hugging Face BERT model, results saved back to Delta Lake
- **Streaming layer** — simulated real-time order ingestion using Databricks Auto Loader and Structured Streaming, processing JSON batches into Delta Lake as they arrive

## Key findings

- Health & beauty is the top revenue category at $1.27M
- Credit card accounts for 85% of orders with an average of 3.6 installments
- Delivery delays are the strongest predictor of low review scores
- ML model achieved 62.6% accuracy predicting review scores from delivery and product data
- Sentiment analysis aligned strongly with review scores for clearly positive and negative reviews, with neutral reviews being hardest to classify

## Tech stack

- Apache Spark / PySpark
- Delta Lake
- Databricks SQL
- MLflow
- Hugging Face Transformers
- Python / Pandas / Scikit-learn

## Dataset

Brazilian E-Commerce Public Dataset by Olist — kaggle.com/datasets/olistbr/brazilian-ecommerce
