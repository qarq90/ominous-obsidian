| Basis             | Classification                                     | Prediction                                   |
| ----------------- | -------------------------------------------------- | -------------------------------------------- |
| Definition        | Assigns data into predefined classes or categories | Estimates a continuous numeric value         |
| Output Type       | Discrete (labels/classes)                          | Continuous (numeric values)                  |
| Goal              | Identify class/category of data                    | Forecast future or unknown values            |
| Techniques Used   | Decision Trees, Naive Bayes, KNN, SVM              | Regression (Linear, Polynomial), Time Series |
| Nature of Problem | Categorical problem                                | Numerical problem                            |
| Example           | Classifying emails as spam or not spam             | Predicting house price based on features     |
| Another Example   | Classifying patients as diseased or healthy        | Predicting temperature for next day          |

---

| Feature             | **Bagging** (Bootstrap Aggregating)                                         | **Boosting**                                                                |
| ------------------- | --------------------------------------------------------------------------- | --------------------------------------------------------------------------- |
| **Goal**            | Reduce **variance** (overfitting)                                           | Reduce **bias** (underfitting)                                              |
| **Training**        | Base models trained **independently** in parallel                           | Base models trained **sequentially**; each tries to correct previous errors |
| **Data sampling**   | **Bootstrap samples** (random draws with replacement) from original dataset | Entire dataset used, but **weights** of misclassified samples are increased |
| **Weighting**       | All models have **equal weight** in final vote                              | Models have **different weights** (better models get more say)              |
| **Base models**     | Usually **high-variance**, **low-bias** models (e.g., deep trees)           | Usually **weak learners** (e.g., shallow trees, stumps)                     |
| **Effect on noise** | Robust to noisy data                                                        | Can be sensitive to outliers/noise                                          |
| **Example**         | Random Forest                                                               | AdaBoost, Gradient Boosting, XGBoost                                        |

---

|Aspect|**BI System**|**Traditional Reporting**|
|---|---|---|
|**Purpose**|Discover insights, support decision making|Provide static, periodic summaries|
|**Data freshness**|Real-time or near real-time|Batch, often daily/weekly/monthly|
|**Interactivity**|High (drill-down, slice-dice, what-if analysis)|Low (static reports, dashboards limited)|
|**User type**|Analysts, managers, data scientists|Operational staff, compliance|
|**Query complexity**|Ad-hoc, complex, iterative|Predefined, fixed SQL queries|
|**Tools**|Power BI, Tableau, Looker, Qlik|Crystal Reports, legacy SQL Server Reporting Services (SSRS)|
|**Data model**|Multi-dimensional (star schema, data cubes)|Simple normalized or flat tables|
|**Self-service**|Yes (business users explore data)|No (requires IT to generate reports)|
|**Focus**|Why did it happen? What will happen?|What happened? (historical record)|

---

| Feature                          | Star Schema                                                                          | Snowflake Schema                                                                                    | Star Constellation (Fact Constellation)                                                                           |
| -------------------------------- | ------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| **Definition**                   | One central fact table connected directly to multiple denormalized dimension tables. | A normalized version of star schema; dimension tables are broken into sub-dimensions (snowflaking). | Multiple fact tables sharing common, conformed dimension tables (fact constellation).                             |
| **Normalization**                | Denormalized (dimension tables contain redundant data).                              | Highly normalized (dimension tables are in 3NF or BCNF).                                            | Mixed – facts are usually denormalized; dimensions are often shared and can be either normalized or denormalized. |
| **Structure**                    | ⭐ Fact table in middle, dimensions around it (like a star).                          | ❄️ Fact table in middle, dimensions split into multiple related tables (like a snowflake).          | 🌌 Multiple fact tables (stars) that share dimension tables (like a constellation).                               |
| **Query Performance**            | **Fast** – fewer joins (single join from fact to each dimension).                    | **Slower** – more joins needed to traverse normalized sub-dimensions.                               | **Good** for cross-fact queries – but complexity increases with multiple fact tables.                             |
| **Ease of Use**                  | Simple, intuitive for business users.                                                | More complex due to many tables.                                                                    | Complex – requires understanding of multiple facts and shared dimensions.                                         |
| **Storage Space**                | Higher – data redundancy in dimension tables.                                        | Lower – no redundant data; efficient storage.                                                       | Moderate – depends on number of facts and whether dimensions are shared.                                          |
| **Data Integrity / Maintenance** | Harder to maintain – update anomalies possible (e.g., address change in many rows).  | Easier – changes made in one place (normalized).                                                    | Moderate – shared dimensions ease maintenance; but multiple facts complicate ETL.                                 |
| **Typical Use Case**             | Simple, read-heavy reporting, data marts, OLAP cubes.                                | Complex data warehouse with limited storage, high insert/update activity.                           | Multiple business processes (e.g., sales & inventory) that need to be analyzed together.                          |
| **Example**                      | Fact: Sales. Dims: Date, Product, Store (each flat, denormalized).                   | Fact: Sales. Dims: Product → Category → Supplier (separate tables).                                 | Fact: Sales and Fact: Inventory. Both share Dim_Date and Dim_Product.                                             |
