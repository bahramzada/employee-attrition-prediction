# IBM HR Analytics & Employee Attrition Prediction

This repository contains a Data Science project aimed at analyzing employee attrition using the famous **IBM HR Analytics** dataset. The project utilizes Python for data cleaning, exploratory data analysis (EDA), and machine learning to predict whether an employee is likely to leave the company.

## 📂 Dataset

The dataset used in this project is the [IBM HR Analytics Attrition Dataset](https://www.kaggle.com/pavansubhasht/ibm-hr-analytics-attrition-dataset).
It contains fictional data regarding employee satisfaction, income, seniority, and demographics.

*   **Source:** Kaggle
*   **Target Variable:** `Attrition` (Yes/No)

## 🛠 Technologies & Libraries Used

The project is implemented in Python using a Jupyter Notebook. Key libraries include:

*   **Data Manipulation:** `pandas`, `numpy`
*   **Visualization:** `matplotlib`, `seaborn`
*   **Machine Learning:** `scikit-learn` (Random Forest, Train-Test Split, Metrics)
*   **Imbalanced Data Handling:** `imblearn` (SMOTE)
*   **Model Saving:** `joblib`

## ⚙️ Project Workflow

1.  **Data Loading:**
    *   Downloading the dataset directly via Kaggle API/Curl.
    *   Unzipping and loading into a Pandas DataFrame.

2.  **Data Cleaning & Preprocessing:**
    *   Dropping irrelevant columns that do not add value to the model: `EmployeeCount`, `Over18`, `StandardHours`, `EmployeeNumber`.
    *   Encoding the target variable `Attrition` (Mapped: Yes -> 1, No -> 0).

3.  **Exploratory Data Analysis (EDA):**
    *   **Correlation Matrix:** Visualizing relationships between numerical features using Heatmaps.
    *   **Distribution Analysis:** Analyzing factors like `MonthlyIncome` against Attrition status using Boxplots.

4.  **Model Building:**
    *   Handling class imbalance using **SMOTE** (Synthetic Minority Over-sampling Technique).
    *   Training a **Random Forest Classifier** to predict attrition.
    *   Evaluating model performance using Classification Reports and Confusion Matrix.

## 📊 Key Insights

*   *Example: Employees with lower monthly income show a higher tendency for attrition.*
*   *Example: [Buraya analizindən çıxan başqa bir maraqlı nəticəni yaza bilərsən]*

## 🚀 How to Run

1.  Clone the repository:
    ```bash
    git clone https://github.com/bahramzada/repository-name.git
    ```
2.  Install the required packages:
    ```bash
    pip install pandas numpy matplotlib seaborn scikit-learn imbalanced-learn joblib
    ```
3.  Run the Jupyter Notebook:
    ```bash
    jupyter notebook
    ```

## 📈 Results

The model performance was evaluated using two different thresholds. While the default threshold offers higher overall accuracy, the tuned threshold (0.3) significantly improves the ability to detect employees likely to leave (Recall for Class 1).

### 1. Default Model Performance (Threshold = 0.5)
*Standard Random Forest prediction.*

| Class | Precision | Recall | F1-Score | Support |
| :--- | :--- | :--- | :--- | :--- |
| **0 (No Attrition)** | 0.86 | 0.94 | 0.90 | 247 |
| **1 (Attrition)** | 0.40 | 0.21 | 0.28 | 47 |
| | | | | |
| **Accuracy** | | | **0.82** | **294** |
| **Weighted Avg** | 0.79 | 0.82 | 0.80 | 294 |

---

### 2. Tuned Model Performance (Threshold = 0.3)
*Threshold lowered to capture more potential attrition cases.*

**Confusion Matrix:**
| | Predicted: No | Predicted: Yes |
| :--- | :---: | :---: |
| **Actual: No** | 184 | 63 |
| **Actual: Yes** | 15 | 32 |

**Classification Report:**

| Class | Precision | Recall | F1-Score | Support |
| :--- | :--- | :--- | :--- | :--- |
| **0 (No Attrition)** | 0.92 | 0.74 | 0.83 | 247 |
| **1 (Attrition)** | 0.34 | **0.68** | 0.45 | 47 |
| | | | | |
| **Accuracy** | | | **0.73** | **294** |
| **Weighted Avg** | 0.83 | 0.73 | 0.77 | 294 |

> **Observation:** By lowering the threshold to 0.3, the **Recall for Class 1 (Attrition) increased from 0.21 to 0.68**. This means the model is much better at identifying employees who are actually at risk of leaving, even though it generates more false positives (lower precision).
