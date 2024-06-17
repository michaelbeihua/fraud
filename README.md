# Consignment Fraud Detection

The buy-sell-trade retail model is vulnerable to insider fraud when employees exploit a company's buying and pricing procedures to arbitrage personal items at the business's expense.
This project is a Python-based machine learning tool designed to identify potential insider fraud by using an isolation forest algorithm to spot anomalies in resale/consignment transactions data.

## Algorithm

The algorithm works by isolating anomalies instead of profiling normal data points.
An isolation forest "isolates" observations by randomly selecting a feature and then randomly selecting a split value between the maximum and minimum values of the selected feature.
This process creates a clear distinction between anomalies and normal observations, with anomalies requiring fewer splits (further away from other data) than normal points (data is more clumped).
The algorithm is unsupervised, meaning that it learns from unlabeled data to discover hidden patterns without human intervention
&mdash; as fraud can be complex, and obtaining real fraudulent data difficult, I thought reducing assumptions and maintaining model flexibility would improve useability.
A similar anomaly detection algorithm to consider implementing could be a one-class support vector machine (SVM), though this decision should depend on the nature of the data.

## Data

The parameters of the data generated in this solution were sourced from a combination of observed online listings of popular fashion retailer 2nd Street and insider information provided by a colleague familiar with the company's operations.
The structure of transaction data was modeled after consignment store point-of-sale (POS) software.
Data was generated according to two predefined sets of behavior, legitimate and fraudulent (contamination), and then combined before model training and left unlabeled.
All data was stored in PostgreSQL [though not necessary for the scope of the project] for its scalability and security in real-world applications.
Feature engineering was kept simple (days_between, profit_margin) to limit dimensionality of model input, prioritizing impact on key business metrics.

## Usage

```python secondhand_fraud_detection.py```
