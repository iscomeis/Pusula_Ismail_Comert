Ismail Comert
i_comertt@hotmail.com

# Predicting Treatment Duration Based on Patient Records  

## Overview
In this study, we work with a **clinical dataset of 2,235 patient records**.  
Our primary objective is to **predict treatment duration** based on patient data.  
The project follows a structured pipeline, covering Exploratory Data Analysis (EDA), Data Preprocessing, Feature Engineering, and Modeling.  

---

## 1. Exploratory Data Analysis (EDA)  
- Explored dataset structure, variable types, and missing values.  
- Visualized distributions, correlations, and categorical patterns.  
- Identified potential anomalies such as duplicated rows.  

---

## 2. Data Preprocessing & Feature Engineering  
To make the dataset **model-ready**, the following steps were applied:  

- **Standardization**: Removed leading/trailing spaces, converted text to lowercase, and replaced multiple spaces with a single space.  
  *This ensured uniformity across the dataset and simplified preprocessing.*  

- **Handling Missing Values**:  
  - Filled sparse categorical gaps with `"bilinmiyor"` (unknown) or `"yok"` (none).  

- **Duplicate Removal**:  
  - Nearly half of the dataset contained duplicate rows.  
  - These may represent repeated treatments for the same patient or data entry duplications.  
  - To avoid bias, duplicates were removed after standardization.  
  - *Note: In practice, domain expertise or consultation with data providers would be required before making this decision.*  

- **Multi-label Processing**:  
  - Defined a custom function to parse columns containing multiple values (e.g., `KronikHastalik`, `Alerji`, `Tanilar`).  
  - Converted comma-separated strings into lists.  
  - Applied `MultiLabelBinarizer` to generate binary columns for each unique value.
    
---

## 3. Modeling  
- Implemented and compared multiple machine learning algorithms:  
  - **Random Forest Regressor**  
  - **Gradient Boosting Regressor**  
  - **HistGradient Boosting Regressor**  

- Additionally, trained a **Deep Learning regression model** to benchmark performance.  

**Results:**  

| Model                  | CV Mean R² | Test R² | MAE  |
|-------------------------|------------|---------|------|
| Random Forest           | 0.669      | 0.729   | 0.989 |
| Gradient Boosting       | 0.841      | 0.827   | 0.742 |
| HistGradient Boosting   | 0.631      | 0.665   | 1.393 |
| Deep Learning           | –          | 0.762   | 0.774 |

---

## 4. Conclusion  
- The dataset required significant **cleaning, standardization, and duplicate handling** before modeling.  
- Proper preprocessing, especially in handling multi-label data and missing values, was critical for achieving consistent results.  
- Gradient Boosting emerged as the most reliable model in this case, though deep learning models also demonstrated promise for future work.  
