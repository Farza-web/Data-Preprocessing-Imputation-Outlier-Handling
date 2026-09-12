# Data Preprocessing: Imputation & Outlier Handling

This repository contains my **Data Preprocessing classwork** using Python, Pandas, NumPy, Matplotlib, and Seaborn.

The main focus of this work is handling **missing values** and **outliers** in different datasets.

## 📌 Objectives

The classwork covers:

1. Imputing missing values in the `Occupation` column of the UCI Adult Census dataset.
2. Detecting outliers in the `age` column of the Diabetes dataset.
3. Mitigating Diabetes `age` outliers using:

   * Trimming
   * Capping
4. Detecting outliers in the `price` column of the House dataset.
5. Mitigating House `price` outliers using:

   * Trimming
   * Capping

## 📂 Datasets Used

### 1. UCI Adult Census Dataset

Used for handling missing values in the `Occupation` column.

**Task:**

* Identify missing values
* Find the most frequent occupation
* Replace missing values using **mode imputation**

### 2. Diabetes Prediction Dataset

Used for detecting and handling outliers in the `age` column.

**Task:**

* Calculate mean and standard deviation
* Identify outliers using the **3-Sigma method**
* Handle outliers using trimming and capping

### 3. House Dataset

Used for detecting and handling outliers in the `price` column.

**Task:**

* Calculate Q1, Q3, and IQR
* Identify price outliers using the **IQR method**
* Handle outliers using trimming and capping

## 🛠️ Technologies Used

* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Kaggle Notebook

## 📊 Methods Used

### Missing Value Imputation

For the categorical `Occupation` column, the missing values are replaced with the **mode**, which is the most frequently occurring value.

```python
most_common_occupation = uci['Occupation'].mode()[0]

uci['Occupation'] = uci['Occupation'].fillna(
    most_common_occupation
)
```

## 📈 Outlier Detection

### 3-Sigma Method

The 3-Sigma method is used for the Diabetes `age` column.

```text
Upper Limit = Mean + 3 × Standard Deviation
Lower Limit = Mean - 3 × Standard Deviation
```

### IQR Method

The IQR method is used for the House `price` column.

```text
IQR = Q3 - Q1

Lower Limit = Q1 - 1.5 × IQR
Upper Limit = Q3 + 1.5 × IQR
```

## ✂️ Outlier Mitigation

### Trimming

Trimming removes observations that fall outside the calculated lower and upper limits.

```python
data_trimmed = data[
    (data['column'] >= lower_limit) &
    (data['column'] <= upper_limit)
]
```

### Capping

Capping replaces outlier values with the corresponding lower or upper limit instead of removing the rows.

```python
data['column'] = np.where(
    data['column'] > upper_limit,
    upper_limit,
    np.where(
        data['column'] < lower_limit,
        lower_limit,
        data['column']
    )
)
```

## 📁 Repository Structure

```text
Data-Preprocessing-Imputation-Outlier-Handling/
│
├── Data_Preprocessing.ipynb
├── README.md
└── images/
    └── plots/
```

## 🎯 Learning Outcomes

Through this classwork, I learned how to:

* Identify missing values in a dataset
* Handle categorical missing values using mode imputation
* Detect statistical outliers
* Use the 3-Sigma method
* Use the IQR method
* Remove outliers using trimming
* Reduce the effect of outliers using capping
* Visualize outliers using box plots
* Perform basic data preprocessing using Python

## 👩‍💻 Author

**Farzana Akter Omi**

Computer Science & Engineering Student

## ⭐ Conclusion

Data preprocessing is an important step before applying machine learning algorithms. Proper handling of missing values and outliers can improve data quality and make datasets more suitable for further analysis and machine learning tasks.
