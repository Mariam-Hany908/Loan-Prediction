# Loan Prediction with Regularization and Hyperparameter Tuning

## Objective
The goal of this project is to build machine learning models that can predict whether a customer’s loan application will be approved.  
We compare *Logistic Regression, **Decision Tree Classifier, and **Random Forest, while applying **regularization* and *hyperparameter optimization (GridSearchCV)*.

---

## Dataset
- *Source*: [Kaggle – Loan Prediction Dataset](https://www.kaggle.com/datasets/ninzaami/loan-predication/data)
- *Rows*: ~614
- *Columns*: 13 (including target Loan_Status)

### Features
- Loan_ID: Unique identifier → dropped before training  
- Gender, Married, Education, Self_Employed, Property_Area, Loan_Status: Categorical features → encoded  
- Dependents: categorical ("0", "1", "2", "3+")  
- ApplicantIncome, CoapplicantIncome: numeric, combined into TotalIncome  
- LoanAmount: numeric, missing values handled, log-transformed  
- Loan_Amount_Term: numeric (usually 360 months)  
- Credit_History: key predictor (1 = good, 0 = bad)  

---

## Methodology
1. *Data Preprocessing*
   - Missing value handling  
   - Encoding categorical features  
   - Feature scaling (important for Logistic Regression)  
   - Train-test split (70/30)

2. *Model Training*
   - Logistic Regression (L1, L2, ElasticNet penalties)  
   - Decision Tree (with parameters: max_depth, min_samples_split)  
   - Random Forest (baseline)  

3. *Hyperparameter Tuning with GridSearchCV*
   - Logistic Regression: tuning C, penalty, solver, l1_ratio  
   - Decision Tree: tuning max_depth, min_samples_split, min_samples_leaf, criterion  
   - Random Forest: tuning number of estimators, max depth  

4. *Evaluation Metrics*
   - Accuracy, Precision, Recall, F1-Score  
   - Confusion Matrix  
   - Visual comparisons  

---

## Results

We conducted *6 experiments* in total:

| Model                          | Train Accuracy | Test Accuracy | Notes |
|--------------------------------|----------------|---------------|-------|
| Logistic Regression (baseline) | 82.05%         | 78.38%        | Stable, no overfitting |
| Logistic Regression (GridSearchCV) | 82.05%     | 78.38%        | Same as baseline |
| Decision Tree (no tuning)      | 100.0%         | 69.73%        | Severe overfitting |
| Decision Tree (GridSearchCV)   | 82.05%         | 78.38%        | Tuning reduced overfitting |
| Random Forest (no tuning)      | 100.0%         | 75.68%        | Still overfitting, but better than DT |
| Random Forest (GridSearchCV)   | 82.75%         | 78.38%        | Best performance |

### Key Insights
- Decision Tree (untuned) suffered from *overfitting* (100% train vs 69.7% test).  
- Random Forest (untuned) also overfit, but performed slightly better than a single tree.  
- Logistic Regression gave *stable and consistent results* without overfitting.  
- GridSearchCV significantly improved Decision Tree and Random Forest, bringing their performance closer to Logistic Regression.  
- *Best Model*: ✅ Random Forest with GridSearchCV (82.75% train, 78.38% test).  

---

## Deliverables
- *Jupyter Notebook*: Data preprocessing + model training + evaluation  
- *Visualizations*: Confusion matrix, bar plots of performance  
- *Short Report (1–2 pages)*:  
  - Dataset description  
  - Methodology  
  - Results & analysis  
  - Conclusion  

---

## Conclusion
- *Logistic Regression* → interpretable, stable, effective when data is linearly separable.  
- *Decision Tree* → interpretable rules but prone to overfitting without tuning.  
- *Random Forest* → more robust, reduces overfitting, and achieved the *best accuracy* after tuning.  

📌 *Final Takeaway*: In My Opinion Decision Tree with drid search is the best model 
