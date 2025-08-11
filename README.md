# Customer Churn Data Analysis

Public Tableau Interactive Dashboard is available at this [link](https://public.tableau.com/app/profile/shristi.shrestha2022/viz/CustomerChurnAnalysisDashboard_17530394841520/OverviewDashboard).

## Table of Contents
1.  [Project Overview](#project-overview)
2.  [Dataset](#dataset)
3.  [Tools & Technologies](#tools--technologies)
4.  [Data Cleaning & Preprocessing Methodology](#data-cleaning--preprocessing-methodology)
5.  [Screenshots](#screenshots)
6.  [Key Findings](#key-findings)
7.  [Setup & Usage](#setup--usage)
8.  [Project Structure](#project-structure)
9.  [Contact](#contact)

## Project Overview


## Dataset
-   **Source File**: `CustomerChurnDataset.xlsx`  
-   **Source Data**: [Telco Customer Churn](https://www.kaggle.com/datasets/blastchar/telco-customer-churn)
-   **Total Records**: 7,043 customer entries
-   **Total Features**: 23 columns
-   **Key Fields**:
    *   **customerID**: Unique identifier for each customer.
    *   **Demographics**: `gender`, `SeniorCitizen`, `Partner`, `Dependents`.
    *   **Account Information**: `tenure`, `Contract`, `PaymentMethod`, `PaperlessBilling`, `MonthlyCharges`, `TotalCharges`.
    *   **Subscribed Services**: `PhoneService`, `MultipleLines`, `InternetService`, `OnlineSecurity`, `OnlineBackup`, `DeviceProtection`, `TechSupport`, `StreamingTV`, `StreamingMovies`.
    *   **Support History**: `numAdminTickets`, `numTechTickets`.
    *   **Target Variable**: `Churn` (Yes/No).

## Tools & Technologies
The entire data cleaning and preparation process was conducted within a Python environment, leveraging the following tools:

-   **Data Manipulation & Cleaning**: Python 3.12 (with pandas and NumPy libraries)
-   **Development Environment**: Jupyter Notebook

![Python Logo](https://img.icons8.com/color/120/python--v1.png)![Jupyter Logo](https://img.icons8.com/?size=100&id=J0SgMWzAxqFj&format=png&color=000000)

## Data Cleaning & Preprocessing Methodology
The raw dataset was refined through a series of systematic steps to ensure its quality and consistency:

1.  **Initial Assessment & Data Profiling**
    *   The dataset was loaded and inspected using `df.info()` and `df.head()` to understand its structure, data types, and identify immediate issues.
    *   The `TotalCharges` column was identified as an `object` type instead of numeric, indicating the presence of non-numeric values.

2.  **Handling Missing and Incorrect Values in `TotalCharges`**
    *   The `TotalCharges` column was converted to a numeric type using `pd.to_numeric` with `errors='coerce'`. Due to issues with some entries, some entries were converted to `NaN` (Not a Number) which was then logically imputed by calculating `tenure * MonthlyCharges`.

3.  **Making Categorical Features Consistent**
    *   Several service-related columns (e.g., `MultipleLines`, `OnlineSecurity`, `OnlineBackup`) contained inconsistent values like "No phone service" or "No internet service" in addition to "No."
    *   To ensure consistency, these redundant categories were replaced with a "No", creating clean, binary "Yes/No" features suitable for analysis and modeling.

4.  **Enhancing Data Readability**
    *   The `SeniorCitizen` column, originally encoded as `0` and `1`, was mapped to more intuitive string values: "No" and "Yes" to improve the interpretability of the data.

5.  **Final Output**
    *   The fully cleaned and processed DataFrame was exported to a new file, `CustomerChurnCleanDataset.xlsx`, creating a cleaned dataset ready for analytical tasks.

## Screenshots
![Alt text](<Screenshot 2025-07-20 at 1.56.57 PM.jpg>)

![Alt text](<Screenshot 2025-07-20 at 1.59.12 PM.jpg>)

![Alt text](<Screenshot 2025-07-20 at 2.00.35 PM.jpg>)

![Alt text](<Screenshot 2025-07-20 at 2.02.33 PM.jpg>)


## Key Findings
## 📊 Overview
- **Total customers: 7,043** with **1,869 churned customers**
- **Overall churn rate: 26.5%** (over 1 in 4 customers leaving)
- **Revenue impact: $139K monthly loss** (30% of total $456K revenue at risk)

## 👥 Demographics & Tenure Period
- **Senior citizens**: 41.7% churn rate vs 23.6% for non-seniors
- **Customers without partners**: Higher churn (1200) than with partners (669)
- **Customers without dependents**: 31.3% churn vs 15.5% with dependents
- **New customers (0-12 months)**: 47.4% churn rate vs 6.6% for 60+ month customers

## 🔧 Subscribed Services
- **Service bundling effect**: Single service = ~20% churn, 8+ services = near 0% churn
- **Fiber optic customers**: 41.9% churn rate (highest among internet services)
- **DSL customers**: Only 19% churn rate (most stable internet service)
- **Online security**: Strong retention drivers (14.6% churn vs 31.3% without)
- **Tech Support**: Strong retention drivers (15.2% churn vs 31.2% without)

## 💳 Billing, Contract, Payment Method, Pricing & Support
- **Month-to-month contracts**: Highest churn: 1,655 churned out of 3,875.
- **One-Year contracts**: significantly reduce churn (only 166 churned).
- **Two-Year contracts**: have the lowest churn (only 48 churned), indicating long-term contracts increase retention.
- **Customers with Paperless Billing**: churn more (33.6%) compared to those not using Paperless Billing (16.3% churn).
- **Electronic check users**: Highest churn risk vs auto-pay methods (3-4% churn)
- **Mid-tier pricing ($70-90/month)**: Higher churn due to price sensitivity
- **Support engagement**: Customers with no admin/tech tickets show higher churn

## 📝 Conclusion
Short-term contracts, electronic check payments, higher monthly charges, and lack of support interaction are strong churn predictors. Retention strategies should focus on:
- Moving customers to annual/two-year contracts
- Incentivizing auto-pay & paperless billing
- Offering value-added services for mid-tier plans
- Proactive outreach to customers with no support interactions

## Setup & Usage
To replicate the data cleaning process on your local machine, please follow these steps:

1.  **Clone the Repository**
    ```bash
    git clone https://github.com/shristi-stha/CustomerChurnAnalysis.git
    cd CustomerChurnAnalysis
    ```
2.  **Set Up a Python Virtual Environment**
    ```bash
    # For macOS/Linux
    python3 -m venv env
    source env/bin/activate

    # For Windows
    python -m venv env
    .\env\Scripts\activate
    ```
3.  **Run the Cleaning Notebook**
    Open and execute the cells in the `Customer_Churn.ipynb` notebook. This will use the raw `CustomerChurnDataset.xlsx` as input and generate the cleaned `CustomerChurnCleanDataset.xlsx` file.
4. **Connect `CustomerChurnCleanDataset.xlsx` by opening `CustomerChurn_Dashboard.twbx` dashboard.**
5. The dashboard would look like [this](https://public.tableau.com/app/profile/shristi.shrestha2022/viz/CustomerChurnAnalysisDashboard_17530394841520/OverviewDashboard).

## Project Structure
```
CustomerChurnAnalysis/
│
├── Customer_Churn.ipynb            # Jupyter Notebook with the Python code for cleaning.
├── CustomerChurnDataset.xlsx       # The original, raw dataset.
├── CustomerChurnCleanDataset.xlsx  # The final, cleaned dataset (output).
├── CustomerChurn_Dashboard.twbx    # Tableau Interactive Dashboard.
└── README.md                       # This project documentation file.
```

## Contact
*(Shristi Shrestha)* - [GitHub](https://github.com/shrististha) | [LinkedIn](https://linkedin.com/in/shristi-stha)
