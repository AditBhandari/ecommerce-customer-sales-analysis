# E-Commerce Customer & Sales Analytics

An end-to-end data analysis project using Python and Pandas to analyze transactional e-commerce data, uncover sales patterns, understand customer behavior, and segment customers using RFM analysis.

---

## Overview

This project analyzes the **UCI Online Retail dataset**, which contains transactional data from a UK-based online retailer covering December 2010 to December 2011.

The goal is to transform raw transaction data into meaningful business insights through:

- Data cleaning
- Feature engineering
- KPI analysis
- Time-series analysis
- Product analysis
- Geographic analysis
- Customer behavior analysis
- Revenue concentration analysis
- RFM customer segmentation
- Correlation analysis

The project focuses on answering business questions rather than simply producing visualizations.

---

## Business Questions

The analysis investigates:

- How does revenue change over time?
- Which months generate the most revenue?
- Which products generate the most revenue?
- Are the highest-volume products also the highest-revenue products?
- Which countries contribute the most revenue and orders?
- How frequently do customers purchase?
- How concentrated is revenue among high-value customers?
- Which customers have the highest monetary value?
- What does the customer base look like using RFM analysis?
- What relationship exists between purchase frequency and monetary value?

---

## Dataset

**Dataset:** UCI Online Retail

The dataset contains approximately 542,000 transaction records with the following fields:

| Column | Description |
|---|---|
| `InvoiceNo` | Transaction/invoice identifier |
| `StockCode` | Product identifier |
| `Description` | Product description |
| `Quantity` | Number of items purchased |
| `InvoiceDate` | Transaction date and time |
| `UnitPrice` | Price per item |
| `CustomerID` | Customer identifier |
| `Country` | Customer's country |

The dataset is available through the **UCI Machine Learning Repository**.

---

## Data Cleaning

The raw dataset was cleaned before analysis.

The following steps were performed:

1. Removed duplicate records.
2. Identified cancelled invoices using invoice numbers beginning with `C`.
3. Removed cancelled transactions from the sales analysis.
4. Removed transactions with non-positive quantities.
5. Removed transactions with non-positive unit prices.
6. Retained transactions with missing `CustomerID` for overall sales analysis.
7. Created a separate customer-level dataset for analyses requiring customer identification.

This resulted in a cleaner transaction dataset suitable for revenue and customer analysis.

---

## Feature Engineering

Several features were created to support the analysis.

### Revenue

Revenue was calculated at the transaction-line level:

```text
Revenue = Quantity × UnitPrice
```

### Time Features

`InvoiceDate` was converted to datetime format and used to create monthly periods for time-based analysis.

### Customer-Level Features

Customer-level metrics were calculated for:

- Revenue
- Number of orders
- Number of items purchased
- Average unit price

---

## Analysis

### 1. Business KPIs

The project calculates:

- Total Revenue
- Total Orders
- Total Customers
- Average Order Value
- Total Items Sold

These provide a high-level overview of the business during the observation period.

---

### 2. Time Analysis

Revenue, order volume, and average order value are analyzed monthly to identify:

- Revenue trends
- Changes in order volume
- Changes in average order value
- High-performing periods

---

### 3. Product Analysis

Products are analyzed using:

- Total revenue
- Quantity sold
- Average unit price
- Number of orders

This allows comparison between high-volume products and high-revenue products.

The analysis also includes a data-quality check for unusual transactions and operational descriptions such as postage or manual charges.

---

### 4. Geographic Analysis

Countries are compared using:

- Revenue
- Number of orders
- Number of customers
- Average order value

A minimum-order threshold is also used when comparing AOV because countries with very few transactions can produce unstable averages.

---

### 5. Customer Analysis

Customer behavior is examined through:

- Purchase frequency
- Customer revenue
- Number of items purchased
- Revenue concentration

Customers are grouped by purchase frequency to distinguish between one-time buyers and repeat customers.

Revenue concentration is also calculated for the top:

- 1 customer
- 5 customers
- 10 customers
- 50 customers
- 100 customers

---

### 6. RFM Analysis

Customers are segmented using **RFM analysis**.

#### Recency

How recently the customer made a purchase.

#### Frequency

How many orders the customer made.

#### Monetary

How much revenue the customer generated.

Each metric is converted into a quintile-based score from 1–5.

Customers are then grouped into:

- High Value
- Loyal
- Potential
- At Risk
- Low Value

The resulting segments can be used to understand differences in customer engagement and monetary contribution.

---

### 7. Correlation Analysis

The project examines relationships between:

- Recency
- Frequency
- Monetary value

A correlation matrix and Frequency vs Monetary scatter plot are used to explore these relationships.

Correlation is treated as an association and **not as evidence of causation**.

---

## Key Findings

The final notebook contains the detailed results and visualizations.

Some of the major patterns investigated include:

- Revenue is strongly concentrated in the UK market.
- Revenue varies substantially across months, with changes driven by both order volume and average order value.
- High-volume products are not necessarily the highest-revenue products.
- Customer spending is highly right-skewed, with a relatively small number of customers contributing substantially more revenue than the typical customer.
- Customer purchase frequency also shows a strongly skewed distribution.
- RFM analysis reveals meaningful differences in recency, purchase frequency, and monetary value across customer segments.

Specific numerical findings and supporting visualizations are available in the notebook.

---

## Visualizations

The project includes visualizations covering:

- Monthly revenue
- Monthly order volume
- Average order value over time
- Top products by revenue
- Top products by quantity
- Revenue by country
- Customer purchase-frequency distribution
- Customer spending distribution
- RFM distributions
- RFM correlation matrix
- Customer frequency vs monetary value

---

## Technologies

- **Python**
- **Pandas**
- **NumPy**
- **Matplotlib**
- **Seaborn**
- **Jupyter Notebook**

---

## Project Structure

```text
ecommerce-customer-sales-analysis/
│
├── data/
│   └── Online Retail.xlsx
│
├── notebooks/
│   └── ecommerce_analysis.ipynb
│
├── README.md
├── requirements.txt
└── .gitignore
```

> The raw dataset does not need to be committed to the repository. It can be downloaded separately from the UCI Machine Learning Repository.

---

## How to Run

### 1. Clone the repository

```bash
git clone <your-repository-url>
cd ecommerce-customer-sales-analysis
```

### 2. Install dependencies

```bash
pip install -r requirements.txt
```

### 3. Add the dataset

Place `Online Retail.xlsx` inside the `data/` directory.

### 4. Open the notebook

Open:

```text
notebooks/ecommerce_analysis.ipynb
```

Run the notebook from top to bottom.

---

## Limitations

- The dataset represents one retailer and a specific historical period, so the results should not be generalized to all e-commerce businesses.
- Missing `CustomerID` values prevent customer-level analysis for some transactions.
- The dataset does not contain explicit costs, margins, or profit, so revenue should not be interpreted as profit.
- Some transaction descriptions represent operational charges rather than conventional products.
- RFM segments depend on the scoring methodology and thresholds selected.
- Correlation analysis identifies relationships but does not establish causation.

---

## Future Improvements

Potential extensions include:

- Customer churn prediction
- Customer lifetime value modeling
- Customer clustering using unsupervised learning
- Sales forecasting
- Product recommendation systems
- Statistical hypothesis testing
- Machine-learning-based customer segmentation

---

## Author

**Adit Bhandari**

This project is part of a broader progression from data analysis toward machine learning and AI.