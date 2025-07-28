# 🏡 Advanced House Price Prediction

This project tackles the **"House Prices: Advanced Regression Techniques"** dataset from Kaggle. The primary objective is to build an accurate regression model to predict house sale prices by conducting **in-depth exploratory data analysis (EDA)**, performing **robust data preprocessing**, and evaluating a variety of **machine learning algorithms**.

---

## 📦 Dataset

The dataset comprises **81 features** that describe various attributes of residential homes. The goal is to predict the final **SalePrice**.

---

## 🔍 Methodology

### 1. Exploratory Data Analysis (EDA)

The initial analysis revealed several key insights:

- The target variable, `SalePrice`, was found to be **highly right-skewed**.
- Many **numerical features** also exhibited significant skewness.
- A total of **19 features** were identified as having missing values, with some columns like `PoolQC`, `MiscFeature`, `Alley`, and `Fence` being **mostly empty**.

---

### 2. In-Depth Preprocessing Steps

To prepare the data for modeling, the following preprocessing steps were meticulously carried out:

#### ✅ Target Variable Transformation

- Due to its right skew (skewness of **1.88**), the `SalePrice` was transformed using a **log transformation** (`np.log1p`).
- This normalized its distribution, reducing the skewness to **0.12**, making it more suitable for linear-based regression models.

#### ✅ Handling Missing Values

- **Categorical features** implying absence (e.g., `PoolQC`, `MiscFeature`, `Alley`, `Fence`, `FireplaceQu`) were filled with **"None"**.
- **Garage-related** features (`GarageType`, `GarageFinish`, `GarageQual`, `GarageCond`) were filled with **"None"**.
- **Basement-related** features (`BsmtQual`, `BsmtCond`, `BsmtExposure`, `BsmtFinType1`, `BsmtFinType2`) were filled with **"None"**.
- `MasVnrType` was filled with **"None"** and `MasVnrArea` with **0**.
- **LotFrontage** was imputed using the **median value within each Neighborhood**, for localized accuracy.
- Other **numerical features** like `GarageYrBlt` were filled with **0**.
- Categorical columns like `Electrical` and `MSZoning` were filled with their respective **mode values**.

#### ✅ Feature Skewness Transformation

- All numerical features with **skewness > 0.75** were log-transformed using `np.log1p`.
- This mitigates the influence of outliers and helps models that assume normally distributed inputs.
- A total of **21 features** were transformed.

#### ✅ Categorical Feature Encoding

- The dataset contains both **nominal** (no order) and **ordinal** (ordered) features, which were encoded accordingly.
- The `Id` column was **dropped** as it is not predictive.

#### ✅ Feature Engineering

- **Seven new important features** were engineered and added to the final data frame.

---

### 3. Modeling and Evaluation

After preprocessing:

- The data was split into **training** and **validation** sets.
- Multiple regression models were trained and evaluated based on their **Root Mean Squared Error (RMSE)**.
- Models were tested **with and without PCA** to study the impact of dimensionality reduction.

---

## 📊 Results

A comprehensive comparison of models, with and without PCA, is provided in the project.  
The RMSE scores and learning performance reflect the impact of preprocessing, skew correction, and feature engineering.

<img width="265" height="204" alt="image" src="https://github.com/user-attachments/assets/0f2f1175-84bb-4600-b354-75a5258c9b83" />

