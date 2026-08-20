# Standardization using StandardScaler

This project demonstrates **feature standardization** using Scikit-learn's `StandardScaler` on the **Social Network Ads** dataset.

## 📌 Objective

The main objective is to understand how standardization affects machine learning features and how it can improve the performance of algorithms such as **Logistic Regression**.

## 📂 Dataset

The dataset used is `Social_Network_Ads.csv`.

The dataset contains information about users of a social network, including:

* `Age`
* `EstimatedSalary`
* `Purchased`

For this project:

* `Age` and `EstimatedSalary` are used as input features.
* `Purchased` is used as the target variable.

## 🔧 Libraries Used

* NumPy
* Pandas
* Seaborn
* Matplotlib
* Scikit-learn

## ⚙️ Steps Performed

### 1. Load the Dataset

The dataset is loaded using Pandas:

```python
df = pd.read_csv('Social_Network_Ads.csv')
```

### 2. Select Required Columns

The unnecessary columns are removed and the index is reset.

```python
df = df.iloc[:, 2:]
df.index = range(1, len(df) + 1)
```

### 3. Separate Features and Target

```python
X = df[['Age', 'EstimatedSalary']]
y = df['Purchased']
```

Here:

* `X` contains the independent variables.
* `y` contains the dependent/target variable.

### 4. Train-Test Split

The dataset is divided into training and testing sets:

```python
X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.3, random_state=0
)
```

70% of the data is used for training and 30% for testing.

### 5. Apply Standardization

`StandardScaler` is used to standardize the features.

```python
scaler = StandardScaler()

X_train_scaled = scaler.fit_transform(X_train)
X_test_scaled = scaler.transform(X_test)
```

The scaler is **fitted only on the training data** and then used to transform both training and test data. This prevents data leakage.

Standardization transforms the features so that they have approximately:

* Mean = 0
* Standard deviation = 1

The transformation is based on the z-score:

```text
z = (x - mean) / standard_deviation
```

### 6. Compare Before and After Scaling

Scatter plots and KDE plots are used to visualize the data before and after standardization.

The plots show that standardization changes the **scale** of the features but does not fundamentally change their distribution.

### 7. Train Logistic Regression Models

Two Logistic Regression models are trained:

```python
lr = LogisticRegression()
lr_scaled = LogisticRegression()

lr.fit(X_train, y_train)
lr_scaled.fit(X_train_scaled, y_train)
```

One model uses the original features and the other uses standardized features.

### 8. Make Predictions

```python
y_pred = lr.predict(X_test)
y_pred_scaled = lr_scaled.predict(X_test_scaled)
```

### 9. Compare Accuracy

The accuracy of both models is compared:

```python
print(f"Actual: {accuracy_score(y_test, y_pred)}")
print(f"Scaled: {accuracy_score(y_test, y_pred_scaled)}")
```

## 📊 Conclusion

This experiment shows how **feature scaling** can be applied before training a machine learning model.

`Age` and `EstimatedSalary` have very different numerical ranges. Standardization puts them on a comparable scale, which is particularly useful for algorithms that are sensitive to feature magnitude.

Logistic Regression is trained both before and after standardization to compare their performance.

## 🧠 Key Learning

* Standardization changes the scale of features.
* It does not remove the original information from the features.
* `StandardScaler` uses the mean and standard deviation of the training data.
* Always `fit` the scaler on training data only.
* Use the same fitted scaler to transform test/new data.
* Feature scaling is important for many distance- and gradient-based algorithms.
* Logistic Regression can benefit from standardized features, especially when features have very different scales.

## 📁 Files

```text
Standardization/
│
├── Social_Network_Ads.csv
├── Standardisation_24.ipynb
└── README.md
```

## 🛠️ Technologies

Python • Pandas • NumPy • Matplotlib • Seaborn • Scikit-learn
