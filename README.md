# Churn Analysis Dashboard

## Table of Contents

- [Case Study](#case-study)
- [Dataset Description](#dataset-description)
- [Data Model](#data-model)
- [DAX Measures for Power BI](#dax-measures-for-power-bi)
- [Data Analysis](#data-analysis)
- [Dashboard](#dashboard)


## Case Study
The objective of this case study is to analyze *Customer Churn performance* by tracking total customers, churned customers, churn rate, and customer distribution across demographics and financial segments.  
The dashboard provides a comprehensive overview of *churn trends, churn drivers, and high-risk customer groups*, helping the bank strengthen retention strategies and reduce customer losses.


## Dataset Description

This dataset contains detailed information on bank customers, including demographics, credit score, balance, activity status, and churn status.  
It enables analysis of customer behavior, churn segmentation, and churn prediction patterns.

Below are the key tables and their fields:

---

### *customer_data* (Fact Table — customer-level data)
- *Customer ID* – Unique identifier for each customer  
- *Gender* – Male / Female  
- *Age* – Age of the customer  
- *Age Groups* – Age bucket category  
- *Country* – France, Spain, Germany  
- *Credit Score* – Credit rating  
- *Credit Score Groups* – Categorized score bucket  
- *Acct Balance* – Bank account balance  
- *Acct Balance Groups* – Balance bucket  
- *Activity Status* – Active / Inactive  
- *Credit Card Status* – Owned / Not Owned  
- *Churn Status* – 1 = Exited, 0 = Active  

> Main table used to analyze churn metrics and behavior patterns.

---

### *Age Groups*
- *Age Groups ID* – Unique identifier  
- *Age Groups* – Age range (ex: <20, 21–30, 31–40)

> Helps analyze churn across customer age buckets.

---

### *Credit Score Groups*
- *Credit Scores* – Group identifier  
- *Credit Score Groups* – Low, Medium, High

> Helps evaluate churn based on customer credit score stability.

---

### *Acct Balance Groups*
- *Acct Balance ID* – Group identifier  
- *Acct Balance* – 0, 1K–10K, 10K–100K, 100K–200K, >200K  

> Helps analyze churn tendencies based on customer financial value.

---

## Data Model
The data model is designed using a *Star Schema*:

- **Fact Table:** customer_data  
- **Dimension Tables:** Age Groups, Credit Score Groups, Acct Balance Groups  
- **Relationships:** 1-to-many, single direction  

This model supports clean filtering, drilldowns, and accurate DAX measures.



DAX Measures for Power BI
### 1.Customers
           Customers = COUNT(customer_data[Customer ID]) 
### 2.Customer Lost
           Customer Lost = CALCULATE(COUNT(customer_data[Churn Status]),customer_data[Churn Status]="Churned")
### 3.Churn Rate
            Churn Rate = customer_data[Customer Lost]/customer_data[Customers]

---

## Data Analysis

### 1. Customers by Gender  
Insight:  
Churn distribution varies by gender, indicating different engagement levels among male and female customers.

### 2. Customers by Activity Status  
Insight:  
Inactive customers show significantly higher churn, highlighting a strong link between engagement and retention.

### 3. Churn by Credit Card Ownership  
Insight:  
Customers without a credit card have higher churn, suggesting increased retention among cardholders.

### 4. Customers by Country  
Insight:  
Germany shows the highest churn among the three countries, making it a critical region for customer retention strategies.

### 5. Customers and Churn Rate by Age Groups  
Insight:  
The age category 41–50 has the highest churn, indicating potential dissatisfaction or unmet expectations in this group.

### 6. Customers and Churn Rate by Credit Score Groups  
Insight:  
Mid-range credit score customers churn more frequently, signaling possible financial challenges.

### 7. Customers and Churn Rate by Account Balance  
Insight:  
High-balance customers (>200K) show increasing churn, implying potential competition from external financial services.

---

##  Churn Analysis Dashboard

<p align="center">
  <img src="https://github.com/user-attachments/assets/775e7f8c-a06b-40be-ac69-6470ba20a8c9" 
       alt="churn-analysis-dashboard" 
       width="900">
</p>



            
