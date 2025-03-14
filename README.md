# Rohlik-Sales-Prediction
Sales prediction project for the Rohlik Group Kaggle Competition. The goal is to forecast warehouse inventory sales for the next 14 days using historical sales data, inventory details, and calender events. Implemented LightGBM with Optuna tuning, achieving Rank 206/777


---

# 📊 Rohlik Sales Prediction – Kaggle Competition

## 🏆 Competition Overview

Rohlik Group, a leading European e-grocery innovator, aims to improve its sales forecasting across 11 warehouses in Czech Republic, Germany, Austria, Hungary, and Romania.   

This competition focuses on predicting sales for the next 14 days using historical data.   

## 📂 Dataset Description

The dataset consists of multiple files providing information about historical sales, inventory, and calendar events:    

**sales_train.csv → Historical sales data**     

**sales_test.csv → Test data without target variable**    

**inventory.csv → Product and warehouse details**    

**calendar.csv → Holiday and event details**    

**test_weights.csv → Weights for final metric computation**    


## 🔹 Key Features

sales → Target variable (sales volume per product & warehouse)    

sell_price_main → Selling price    

total_orders → Number of orders (provided for both train & test)     

type_0_discount, type_1_discount, … → Promotional discounts     

holiday, shops_closed, school_holidays → Calendar-based features     


---

## 🥇 My Rank & Score

✅ Rank: 206 / 777    
✅ Leaderboard Score (WMAE): 19.89490    


---

## 🛠 Approach & Model Used

**📌 Data Preprocessing**

✔ Merged sales_train.csv, inventory.csv, and calendar.csv → sales_train_full.csv   
✔ Merged sales_test.csv, inventory.csv, and calendar.csv → sales_test_full.csv    
    **- sales_train_full : 4007419 rows * 25 columns**  
    **- sales_test_full : 47021 rows * 23 columns**     
✔ Handled missing values   
✔ No duplicates   
✔ Negative discounts interpreted as no discount (per competition guidelines)   

**📌 Feature Engineering**

🔹 Created additional features based on sales,discount and dates.   

**📌 Model Training**

🔸 LightGBM (performed best without categorical encoding)    
🔸 Optuna hyperparameter tuning with 500 trials    
🔸 Time-based train-test split (to respect temporal ordering)    


---

## 📊 Performance Metric

The competition uses Weighted Mean Absolute Error (WMAE):

WMAE = (Σ (w_i * |y_i - ŷ_i|)) / (Σ w_i)


---

## 📌 Key Takeaways

✔ Feature Engineering Matters: Adding sales, discount, and date features improved performance.   
✔ Handling Categorical Features Carefully: LightGBM performed better with raw categorical features than encoded versions.   
✔ Hyperparameter Tuning: Optuna (500 trials) significantly improved the model’s accuracy.    
✔ Time-based Splitting: Ensuring correct train-test split in time series forecasting is crucial.     


---

📌 Future Improvements

✔ Experiment with external datasets for better feature engineering    
