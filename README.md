<h1 align="center"> E-Commerce Customer Churn Prediction </h1>
<p align="center">
    <img src="https://cdn.analyticsvidhya.com/wp-content/uploads/2020/05/Churn-Prediction-scaled.jpg" width="900" height="400">
</p>

# Problem Statements
Churn rate adalah rasio pelanggan yang berhenti berlangganan dengan perusahaan dalam periode waktu tertentu. Salah satu mekanisme terbaik untuk mempertahankan pelanggan saat ini adalah mengidentifikasi potensi churn dan merespon dengan cepat untuk mencegahnya. Teknik data mining dapat diterapkan untuk menganalisis perilaku pelanggan dan untuk memprediksi pengurangan pelanggan (churn) potensial sehingga strategi pemasaran khusus dapat diadopsi untuk mempertahankannya.

## Business Question
1. Berapa persen customer yang memilih untuk churn ?
2. Apakah jenis kelamin berpengaruh terhadap kemungkinan customer untuk churn?
3. Apakah ada pengaruh antara tenure dengan churn rate?
4. Apakah jarak rumah customer dengan warehouse memiliki pengaruh terhadap churn?
5. Apakah customer yang komplain cenderung akan memilih untuk churn ?
6. Bagaimana churn rate berdasarkan kategori produk yang dibeli customer ?
7. Bagaiman churn rate berdasarkan metode pembayaran yang digunakan

## Goal
1. Mengidentifikasi penyebab churn.
2. Membangun machine learning untuk mendeteksi customer yang akan churn.

## Data Dictionary
|           Variable          |                           Description                           |
|:---------------------------:|:---------------------------------------------------------------:|
| CustomerID                  | Unique customer ID                                              |
| Churn                       | Churn Flag                                                      |
| Tenure                      | Tenure of customer in   organization                            |
| PreferredLoginDevice        | Preferred login   device of customer                            |
| CityTier                    | City tier                                                       |
| WarehouseToHome             | Distance in between   warehouse to home of customer             |
| PreferredPaymentMode        | Preferred payment   method of customer                          |
| Gender                      | Gender of customer                                              |
| HourSpendOnApp              | Number of hours spend   on mobile application or website        |
| NumberOfDeviceRegistered    | Total number of   deceives is registered on particular customer |
| PreferedOrderCat            | Preferred order   category of customer in last month            |
| SatisfactionScore           | Satisfactory score of   customer on service                     |
| MaritalStatus               | Marital status of   customer                                    |
| NumberOfAddress             | Total number of added   added on particular customer            |
| Complain                    | Any complaint has   been raised in last month                   |
| OrderAmountHikeFromlastYear | Percentage increases   in order from last year                  |
| CouponUsed                  | Total number of   coupon has been used in last month            |
| OrderCount                  | Total number of   orders has been places in last month          |
| DaySinceLastOrder           | Day Since last order   by customer                              |
| CashbackAmount              | Average cashback in   last month                                |

# Work Steps
1. Problem Statement
   - Context
   - Business Questions
   - Goals
   - Data Dictionary
2. Data Exploration
   - Load Dataset
   - Data Information
   - Statistics Descriptive
   - Check Null Values
   - Check Duplicated Data
3. Data Cleansing
   - Handling Missing Values
   - Handling Inconsistent Data
   - Handling Outliers
4. Exploratory Data Analysis
   - Univariate Analysis
   - Multivariate Analysis
5. Feature Engineering
   - Add New Features
   - Remove Unnecessary Features
   - Feature Encoding 
   - Feature Scaling 
6. Sampling Dataset 
   - Separate Train and Test Set
   - Oversampling Using SMOTE
7. Modelling
   - Choose Best Model
   - Feature Selection using Recursive Feature Elimination
   - Hyperparameter Tuning
8. Model Evaluation
   - Confusion Matrix
   - Classification Report
   - Precision Recall and ROC Curve
   - Feature Importance
   - Thresholds Adjustment
9. Save Model

# Data Explopration
## Dataset Preview
|   | CustomerID | Churn | Tenure | PreferredLoginDevice | CityTier | WarehouseToHome | PreferredPaymentMode | Gender | HourSpendOnApp | NumberOfDeviceRegistered |   PreferedOrderCat | SatisfactionScore | MaritalStatus | NumberOfAddress | Complain | OrderAmountHikeFromlastYear | CouponUsed | OrderCount | DaySinceLastOrder | CashbackAmount |   |
|--:|-----------:|------:|-------:|---------------------:|---------:|----------------:|---------------------:|-------:|---------------:|-------------------------:|-------------------:|------------------:|--------------:|----------------:|---------:|----------------------------:|-----------:|-----------:|------------------:|---------------:|---|
| 0 |      50001 |     1 |    4.0 |         Mobile Phone |        3 |             6.0 |           Debit Card | Female |            3.0 |                        3 | Laptop & Accessory |                 2 |        Single |               9 |        1 |                        11.0 |        1.0 |        1.0 |               5.0 |         159.93 |   |
| 1 |      50002 |     1 |    NaN |                Phone |        1 |             8.0 |                  UPI |   Male |            3.0 |                        4 |             Mobile |                 3 |        Single |               7 |        1 |                        15.0 |        0.0 |        1.0 |               0.0 |         120.90 |   |
| 2 |      50003 |     1 |    NaN |                Phone |        1 |            30.0 |           Debit Card |   Male |            2.0 |                        4 |             Mobile |                 3 |        Single |               6 |        1 |                        14.0 |        0.0 |        1.0 |               3.0 |         120.28 |   |
| 3 |      50004 |     1 |    0.0 |                Phone |        3 |            15.0 |           Debit Card |   Male |            2.0 |                        4 | Laptop & Accessory |                 5 |        Single |               8 |        0 |                        23.0 |        0.0 |        1.0 |               3.0 |         134.07 |   |
| 4 |      50005 |     1 |    0.0 |                Phone |        1 |            12.0 |                   CC |   Male |            NaN |                        3 |             Mobile |                 5 |        Single |               3 |        0 |                        11.0 |        1.0 |        1.0 |               3.0 |         129.60 |   |

# Statistics Decriptive
| CustomerID |        Churn |      Tenure |    CityTier | WarehouseToHome | HourSpendOnApp | NumberOfDeviceRegistered | SatisfactionScore | NumberOfAddress |    Complain | OrderAmountHikeFromlastYear |  CouponUsed |  OrderCount | DaySinceLastOrder | CashbackAmount |             |
|-----------:|-------------:|------------:|------------:|----------------:|---------------:|-------------------------:|------------------:|----------------:|------------:|----------------------------:|------------:|------------:|------------------:|---------------:|-------------|
|      count |  5630.000000 | 5630.000000 | 5366.000000 |     5630.000000 |    5379.000000 |              5375.000000 |       5630.000000 |     5630.000000 | 5630.000000 |                 5630.000000 | 5365.000000 | 5374.000000 |       5372.000000 |    5323.000000 | 5630.000000 |
|       mean | 52815.500000 |    0.168384 |   10.189899 |        1.654707 |      15.639896 |                 2.931535 |          3.688988 |        3.066785 |    4.214032 |                    0.284902 |   15.707922 |    1.751023 |          3.008004 |       4.543491 |  177.223030 |
|        std |  1625.385339 |    0.374240 |    8.557241 |        0.915389 |       8.531475 |                 0.721926 |          1.023999 |        1.380194 |    2.583586 |                    0.451408 |    3.675485 |    1.894621 |          2.939680 |       3.654433 |   49.207036 |
|        min | 50001.000000 |    0.000000 |    0.000000 |        1.000000 |       5.000000 |                 0.000000 |          1.000000 |        1.000000 |    1.000000 |                    0.000000 |   11.000000 |    0.000000 |          1.000000 |       0.000000 |    0.000000 |
|        25% | 51408.250000 |    0.000000 |    2.000000 |        1.000000 |       9.000000 |                 2.000000 |          3.000000 |        2.000000 |    2.000000 |                    0.000000 |   13.000000 |    1.000000 |          1.000000 |       2.000000 |  145.770000 |
|        50% | 52815.500000 |    0.000000 |    9.000000 |        1.000000 |      14.000000 |                 3.000000 |          4.000000 |        3.000000 |    3.000000 |                    0.000000 |   15.000000 |    1.000000 |          2.000000 |       3.000000 |  163.280000 |
|        75% | 54222.750000 |    0.000000 |   16.000000 |        3.000000 |      20.000000 |                 3.000000 |          4.000000 |        4.000000 |    6.000000 |                    1.000000 |   18.000000 |    2.000000 |          3.000000 |       7.000000 |  196.392500 |
|        max | 55630.000000 |    1.000000 |   61.000000 |        3.000000 |     127.000000 |                 5.000000 |          6.000000 |        5.000000 |   22.000000 |                    1.000000 |   26.000000 |   16.000000 |         16.000000 |      46.000000 |  324.990000 |

# Data Cleaning
## 
