# Customer Churn Data Analysis

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
-   **Total Records**: 7,043 customer entries
-   **Total Features**: 23 columns
-   **Key Fields**:
    *   `customerID`: Unique identifier for each customer.
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
    *   The `TotalCharges` column was converted to a numeric type using `pd.to_numeric` with `errors='coerce'`. This process revealed 11 entries that were originally empty strings, which were converted to `NaN` (Not a Number).
    *   These missing values were logically imputed by calculating `tenure * MonthlyCharges`. This approach assumes that customers with a tenure of 0 months had not yet accrued any total charges, providing a sensible estimate.

3.  **Standardizing Categorical Features**
    *   Several service-related columns (e.g., `MultipleLines`, `OnlineSecurity`, `OnlineBackup`) contained inconsistent values like "No phone service" or "No internet service" in addition to "No."
    *   To ensure consistency, these redundant categories were replaced with a standard "No", creating clean, binary "Yes/No" features suitable for analysis and modeling.

4.  **Enhancing Data Readability**
    *   The `SeniorCitizen` column, originally encoded as `0` and `1`, was mapped to more intuitive string values: "No" and "Yes". This improves the interpretability of the data for business stakeholders and analysts.

5.  **Final Output**
    *   The fully cleaned and processed DataFrame was exported to a new file, `CustomerChurnCleanDataset.xlsx`, creating a pristine dataset ready for downstream analytical tasks.

## Screenshots

## Key Findings

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

## Project Structure
```
CustomerChurnAnalysis/
│
├── Customer_Churn.ipynb.ipynb             # Jupyter Notebook with the Python code for cleaning.
├── CustomerChurnDataset.xlsx       # The original, raw dataset.
├── CustomerChurnCleanDataset.xlsx  # The final, cleaned dataset (output).
└── README.md                       # This project documentation file.
```

## Contact
*(Shristi Shrestha)* - [GitHub](https://github.com/shrististha) | [LinkedIn](https://linkedin.com/in/shristi-stha)
