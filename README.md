# Real Estate Price Prediction using Machine Learning

**A machine learning project designed to predict real estate prices based on various property characteristics.**  
The goal is to develop a model that accurately estimates property prices using structured data and advanced machine learning techniques.

---

## Context

This project was conducted as part of our **final Machine Learning project** in the second year of our **double bachelor's degree in Artificial Intelligence and Organizational Sciences** at **Paris Dauphine University**.

Accurately predicting real estate prices is a major challenge due to the **complexity of the market** and the **variety of influencing factors** (location, size, energy efficiency, etc.). Our objective is to develop a **robust machine learning model** that can estimate prices efficiently, handling missing data and high-dimensional categorical variables.

🚀 **🏆 Our team achieved strong performance in the challenge!**  
- **Top results in model optimization with XGBoost**  
- **Implemented advanced feature engineering techniques**  

🔗 **Challenge link:** [Real Estate Price Prediction Challenge](https://challengedata.ens.fr/participants/challenges/68/)

---

## Dataset Overview

The dataset consists of **40,000 real estate listings** with **27 features** characterizing the properties.

### **Target Variable (`PRICE`)**
- **Continuous variable** representing the property price.
- **Highly dispersed distribution**, requiring careful preprocessing.

### **Feature Categories**
The dataset includes a mix of **numerical and categorical variables**:

| Feature Category | Description |
|-----------------|-------------|
| `ID_ANNONCE` | Unique property listing identifier |
| `CITY` | City where the property is located |
| `PROPERTY_TYPE` | Type of property (house, apartment, etc.) |
| `SIZE`, `LAND_SIZE` | Area of the property (square meters) |
| `NB_ROOMS`, `NB_BEDROOMS`, `NB_BATHROOMS` | Number of rooms, bedrooms, and bathrooms |
| `ENERGY_PERFORMANCE_CATEGORY`, `GHG_CATEGORY` | Energy efficiency classifications |
| `EXPOSITION` | Property orientation |

The dataset contains **significant missing values** in multiple variables, requiring extensive preprocessing.

---

## 🔧 Data Preprocessing

### **1️⃣ Handling Categorical Variables**
- **Label Encoding** for ordinal features (e.g., `ENERGY_PERFORMANCE_CATEGORY`).
- **One-Hot Encoding** for nominal variables (e.g., `CITY`, `PROPERTY_TYPE`).

### **2️⃣ Handling Missing Values**
- Used **K-Nearest Neighbors (KNN) Imputer** for numerical features to estimate missing values based on similar properties.
- Considered **Iterative Imputation** for further refinement.

### **3️⃣ Feature Engineering**
- **Identified redundant features** and removed unnecessary variables.
- **Standardized numerical features** to improve model performance.

---

## Machine Learning Models

We experimented with various regression models to optimize price prediction.

### **Models Tested**
| Model | Performance |
|--------|------------|
| Linear Regression | Low accuracy due to feature complexity |
| K-Nearest Neighbors (KNN) | Improved but computationally expensive |
| Random Forest | Moderate accuracy, limited by non-sequential training |
| **XGBoost (Best Model)** | **Top performance with hyperparameter tuning** |

### **Model Selection & Optimization**
- **XGBoost was chosen** due to its superior handling of large datasets and feature interactions.
- **Hyperparameter tuning** using **GridSearchCV**, leading to optimized parameters:

```json
{
  "subsample": 0.91,
  "scale_pos_weight": 6,
  "reg_lambda": 0.00015,
  "reg_alpha": 0.005,
  "n_estimators": 1600,
  "min_child_weight": 4,
  "max_depth": 10,
  "learning_rate": 0.04,
  "gamma": 0.11,
  "colsample_bytree": 0.85
}
