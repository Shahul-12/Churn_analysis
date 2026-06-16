🛒 E-Commerce Customer Churn Analysis
Identifying At-Risk Customers & Quantifying Revenue Impact from Raw Transactional Data


───

📌 Project Summary

In e-commerce, understanding why customers stop buying — and who is about to — is one of the highest-value problems a data team can solve. This project takes raw order transaction data from the Olist Brazilian E-Commerce platform and transforms it into an actionable customer churn analysis, complete with risk segmentation and revenue impact quantification.

The core question: Given only order history, can we identify which customers are drifting away — and how much revenue is at risk if we do nothing?

───

💼 Business Context





Dataset
Olist Brazilian E-Commerce (public)

Records
112,650 order items

Customers
96,478 unique

Period
September 2016 — September 2018

Churn Definition
No purchase within 180 days of reference date

Churn Rate
60.7% (58,570 customers)



Key insight from EDA: 99%+ of customers placed only a single order. This fundamentally shaped the analysis — churn is driven by when and how well that one experience went, not by purchase frequency.

───

📊 Key Business Findings

1. R$`6.86M in Revenue is At Risk
Customers were segmented into four risk tiers based on predicted churn probability:


Segment
Customers
Revenue at Risk

🔴 High Risk
18,080
R`$ 1.13M

🟠 Medium Risk
38,683
R$` 3.65M

🟡 Low Risk
26,984
R`$ 1.89M

🟢 Safe
12,731
R$` 0.18M

Total
96,478
R`$ 6.86M



2. Delivery Speed is the #1 Churn Driver
The strongest predictors of churn were all delivery-related:
• Time from purchase to order approval
• Time from approval to carrier pickup
• End-to-end delivery duration

Customers who received their orders faster were significantly more likely to return.

3. High Freight Cost Drives Churn
Customers with a high freight-to-spend ratio churned at a higher rate. When shipping costs feel disproportionate to the order value, customers don't come back.

4. Medium Risk is the Priority Segment
With R$`3.65M at risk and 38,683 customers, the Medium Risk tier offers the highest ROI for retention campaigns — large enough to matter, early enough to save.

───

🔍 Analytical Approach

Step 1 — Data Cleaning & Preparation
• Parsed 6 datetime columns from string format
• Handled missing delivery timestamps (< 2% of records)
• Filtered to delivered orders only for behavioral analysis

Step 2 — Customer-Level Feature Engineering
Aggregated 112,650 order-level rows into 96,478 customer profiles:

Spend Behaviour
• Total spend, average order value, freight ratio, spend per item

Delivery Experience
• Approval time (hours), carrier pickup time (days), end-to-end delivery (days)
• Delivery delay vs estimate, late delivery rate

Purchase Behaviour
• Day of week purchasing pattern, weekend buyer flag

Step 3 — Exploratory Data Analysis
• Churn distribution and recency patterns
• Single vs repeat buyer breakdown
• Monthly order volume trends (Sep 2016 → Sep 2018)
• Delivery delay vs churn probability relationship

Step 4 — Predictive Modelling
Built a Random Forest classifier to score each customer's churn probability:


Parameter
Value

Algorithm
Random Forest

Trees
300

Class balancing
Weighted (60/40 imbalance)

Threshold
0.40 (tuned for precision-recall balance)

Features
12 behavioral + delivery signals



Model Performance


Metric
Score

ROC-AUC
0.843

Accuracy
76.0%

Precision (Churned)
0.83

Recall (Churned)
0.79

F1-Score (Churned)
0.80



Step 5 — Risk Segmentation & Business Output
• Scored all 96,478 customers with churn probability
• Assigned to actionable risk tiers
• Quantified revenue at risk per segment
• Validated model calibration (predicted probability vs actual churn rate)

💡 Business Recommendations

1. Target Medium Risk customers first
Largest revenue at risk (R`$3.65M). These customers are drifting — a timely re-engagement campaign (discount, personalised email) has the highest expected return.

2. Invest in logistics speed
Delivery approval time and carrier pickup speed are the strongest churn predictors. Reducing end-to-end delivery time by even 1–2 days could meaningfully improve retention.

3. Review freight pricing for smaller orders
High freight-to-spend ratio customers churn more. Consider freight subsidies or free shipping thresholds for orders where shipping cost is disproportionate.

4. Re-engage within 150 days
Churn accelerates after 180 days of inactivity. Automated re-engagement triggers at 150 days (before the threshold) would catch customers while they are still recoverable.

───

🛠️ Tech Stack


Tool
Purpose

Python
Core language

Pandas & NumPy
Data wrangling and feature engineering

Matplotlib & Seaborn
Exploratory and business visualisations

Scikit-learn
Modelling, evaluation, and scaling

Joblib
Model serialisation




👤 About This Project

This project was built to demonstrate end-to-end analytical thinking — from understanding a business problem, through data wrangling and feature engineering, to delivering outputs that a business team can act on. The emphasis throughout is on insight and decision support, not just model accuracy.

Skills demonstrated:
• Translating a business problem into an analytical framework
• Feature engineering from raw transactional data
• Exploratory data analysis and storytelling with visualisations
• Predictive modelling with business-oriented evaluation
• Customer segmentation and revenue impact quantification
