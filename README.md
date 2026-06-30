# E-commerce Analytics: Marketing Budget Insights

*Junior data analyst test task - SQL, Tableau and Python.*

### Task
The work has three parts:
- **SQL** - 5 queries against the public `thelook_ecommerce` dataset in BigQuery.
- **Tableau** - an interactive dashboard with the key visualizations.
- **Python (bonus)** - a linear regression "age -> purchase amount" plus a search for a better model.

### What we had
A dataset of ~55,000 e-commerce transactions (Kaggle). Key fields: gender, age group, purchase date, product category, discount flag, gross and net amount, payment method, city. Important detail: there is no exact age in the data - only **age groups**.

### What we mainly did
- **SQL:** users from Brazil in 2023, product counts per category, Shipped orders (JOIN), top-10 most expensive orders, countries with more than 500 users (HAVING).
- **Tableau:** monthly revenue trend, discount effectiveness (average check with discount vs full price), categories by age group, a KPI card with total revenue, filters. A separate business-case dashboard "men vs women".
- **Python:** a linear regression of purchase amount on age, with data-quality checks and a two-way verification of the result (scikit-learn + statsmodels).

### How we explored
- For the regression we converted age bands into a numeric proxy using band midpoints (e.g. 25-45 -> 35), since exact age is missing.
- We computed the coefficient, R², p-value and correlation.
- We additionally ran a **search for a better model**: polynomial regression (degree 2 and 3), a decision tree, a random forest and a linear model with one-hot encoded age group. All models were compared fairly - on a held-out test set and with 5-fold cross-validation (R² and RMSE).

### Conclusions
- **Gender does not determine profitability.** Men, women and the "Other" group bring almost identical revenue (~₹52M each), the same average check (~₹2.86-2.87K) and the same discount share (~49.7-49.8%).
- **The real driver is age.** The 25-45 segment generates ~40% of revenue, and together with 18-25 these groups make up ~70% of income.
- **Age does NOT affect purchase amount.** The regression coefficient is ~0.27 (10 extra years add only ~2.7 INR), R² ≈ 0, p-value ≈ 0.63. None of the tested models beat simply predicting the average - so the weakness is in the data, not the model.
- **Recommendation.** Targeting the budget by age or gender is not justified. Stronger levers are product category, discount behaviour, purchase frequency and location. The discount policy also deserves a review: ~50% of all purchases use a discount, which pressures margin.

### Repository structure
⊢ SQL
  ⊢ task1
    ⊢ task1.png
    ⌞ task1.csv
  ⊢ task12
    ⊢ task2.png
    ⌞ task2.csv
  ⊢ task3
    ⊢ task3.png
    ⌞ task3.csv
  ⊢ task4
    ⊢ task4.png
    ⌞ task4.csv
  ⊢ task5
    ⊢ task5.png
    ⌞ task5.csv
  ⊢ queries.sql
  ⌞ queries.txt
|
⊢ Tableau
  ⊢ Dashboard1.png
  ⊢ Dashboard2.png
  ⌞ final_project.twbx
|
⊢ python_predict
  ⊢ data
    ⌞ project1_df.csv
  ⊢ regression_age_EN.ipynb
  ⌞ requirements.txt
|
⌞ README.md

### How to run the notebooks
```bash
pip install -r requirements.txt
```

