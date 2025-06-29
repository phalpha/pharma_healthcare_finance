# Pharma, Healthcare, Finance: Analyzing these Relationships

## Project Overview

This project explores the financial relationships between drug and medical device companies and healthcare providers using the Center for Medicare and Medicaid Services (CMS) Open Payments Data from 2022. The dataset comprises 14.11 million records reflecting transactions totaling $12.59 billion.

**Central Question:** Given the characteristics of a transaction (transaction purpose, payer/recipient, state where the transaction was conducted, etc.), can we predict the price of the transaction?

The project explores trends and patterns within the financial landscape of healthcare and forecasts transaction amounts using both statistical and machine learning methodologies.

## Dataset Description

The Open Payments Dataset contains information about financial relationships between drug/medical device companies and healthcare providers, collected by the US federal government. We used the 2022 data containing payments made between January 1, 2022 and December 31, 2022.

The data is reported across three categories:

- **General** (13,148,520 rows, 91 columns, 6.12 GB): Payments not in connection with research
- **Research** (953,320 rows, 252 columns, 537.69 MB): Payments made in connection with research agreements
- **Ownership** (3,919 rows, 30 columns, 1.58 MB): Information on ownership or investment stakes

Key features include recipient information (name, location, specialty), reporting entity details (company name, payment date, nature of payment), and dollar amounts.

## Data Analysis

### Payment Type Analysis
- **Most frequent transactions:** Food and beverage, travel and lodging, non-consulting compensation
- **Highest total cost:** Royalty and license fees (~$1 billion total)
- **Highest average cost per transaction:** Acquisitions, followed by royalties and licensing

### Geographic Analysis
- **Top states by total cost:** California, Texas, New York, Pennsylvania
- **Notable outlier:** Pennsylvania (~$826 million) due to large mRNA vaccine royalties paid to University of Pennsylvania researchers

### Product Categories
Top spending areas include infectious diseases, surgery, neuroscience, and immunology.

## Predicting Payment Amount

We implemented two prediction models using features like recipient state, specialty, company name, payment type, and product indicators.

### K-Nearest Neighbors
- Used categorical distance function with feature weighting
- Experimented with different K values, chose K=10
- **Test RMSE:** 705.8

### Linear Regression
- Added feature engineering: PA state indicator, top product categories, inter-state distances
- Used BigQuery ML for implementation
- **Test RMSE:** 843.3

## Performance Comparison

**KNN vs Linear Regression:**
- KNN achieved better prediction accuracy (lower RMSE)
- Linear regression was significantly more efficient in terms of IO costs, time, and monetary cost
- KNN: 4 min 6 sec runtime, $0.016 cost
- Linear regression: 25 seconds runtime, negligible cost

## Conclusion

This project analyzed the relationship between drug/medical companies and healthcare providers through the 2022 Open Payments Data. We visualized payment patterns across geographic locations, companies, and payment types, and successfully implemented prediction models for transaction amounts.

The analysis demonstrates how large healthcare financial datasets can provide insights into industry relationships and potentially identify payment discrepancies. Future work could expand to multi-year analysis, classification approaches, and integration with additional pharmaceutical company data.

---

This was my final project for a CS 145 Project class on databases
