# MSCS_634_Project_Deliverable-4-Final-Insights

## Advanced Data Mining in Healthcare  

## Project Overview  
This project demonstrates a **complete data mining pipeline** using a synthetic healthcare dataset.  
The workflow covers:  

- Data collection and cleaning  
- Exploratory data analysis (EDA)  
- Regression modeling (billing prediction)  
- Classification (test results prediction)  
- Clustering (patient segmentation)  
- Association rule mining (condition–medication relationships)  

The goal is to gain **operational and clinical insights** into healthcare utilization, costs, and prescribing patterns.  

## Dataset  
- **File:** `healthcare_dataset.csv`  
- **Size:** ~55,500 records × 15 attributes  
- **Key Attributes:**  
  - Demographics: `age`, `gender`, `blood_type`  
  - Clinical: `medical_condition`, `test_results`, `medication`  
  - Administrative: `hospital`, `insurance_provider`, `admission_type`, `doctor`  
  - Financial: `billing_amount`, `room_number`  
  - Dates: `date_of_admission`, `discharge_date`  

**Cleaning performed:**  
- Removed **534 duplicate rows**  
- Capped billing outliers above **99th percentile**  
- Standardized column names and text values  
- Added engineered features (e.g., age bands)  

Final dataset size: **54,416 records**  

## Key Results

### Regression (Billing Prediction)

* Models: Linear, Ridge, Lasso
* **RMSE ≈ 13,865**
* **R² ≈ 0.0** → billing not predictable with given features

### Classification (Test Results Prediction)

* Target: Normal / Abnormal / Inconclusive
* Decision Tree Accuracy: **32.7%**
* Naive Bayes Accuracy: **32.9%**
* Tuned Decision Tree Accuracy: **33.2%**
* Insight: Very weak predictability, features not sufficient

### Clustering (Patient Segmentation)

* Method: KMeans (k = 3), PCA visualization
* Groups identified:

  * Younger patients, billing ≈ 12k–15k
  * Middle-aged, billing ≈ 25k–30k
  * Older patients, billing > 40k
* Clear stratification by **age and cost**

### Association Rules (Condition → Medication)

| Condition    | Medication  | Support | Confidence | Lift  |
| ------------ | ----------- | ------- | ---------- | ----- |
| Cancer       | Lipitor     | 0.0347  | 0.2083     | 1.036 |
| Asthma       | Paracetamol | 0.0343  | 0.2072     | 1.034 |
| Arthritis    | Aspirin     | 0.0346  | 0.2065     | 1.036 |
| Obesity      | Penicillin  | 0.0343  | 0.2056     | 1.033 |
| Hypertension | Ibuprofen   | 0.0341  | 0.2048     | 1.023 |

* Rules show weak lift (~1.0) but align with **expected medical patterns**

## Insights & Recommendations

* **Billing amounts** require richer features (e.g., procedures, codes) for predictive modeling.
* **Test results** classification is weak → dataset lacks diagnostic variables.
* **Clustering** reveals clear patient utilization segments (low, medium, high cost).
* **Association rules** confirm logical prescribing but need stronger support.

## Future Work

* Enrich dataset with clinical and procedural codes
* Test advanced models (Random Forest, XGBoost, Neural Nets)
* Evaluate fairness across subgroups (age, gender)
* Deploy models as decision-support tools for hospital management

