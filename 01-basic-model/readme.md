# Basic Machine Learning Model – Placement Prediction

This project demonstrates a basic Machine Learning workflow using a small
student placement dataset.

The model predicts whether a student will be placed based on their **CGPA**
and **IQ** using **Logistic Regression**.

## Dataset

The dataset contains the following columns:

| Feature | Description |
|---|---|
| `cgpa` | Student's CGPA |
| `iq` | Student's IQ score |
| `placement` | Target variable (1 = Placed, 0 = Not Placed) |

The `Unnamed: 0` column is an index column and is not used as a feature.

## Machine Learning Workflow

The project follows these steps:

1. Load the dataset using Pandas
2. Select `CGPA` and `IQ` as input features
3. Separate the target variable (`placement`)
4. Split the data into training and testing sets
5. Standardize the features using `StandardScaler`
6. Train a `LogisticRegression` model
7. Make predictions on the test data
8. Evaluate the model using accuracy score
9. Predict placement for a new student

## Technologies Used

- Python
- NumPy
- Pandas
- Scikit-learn
- Google Colab / Jupyter Notebook

## Model

**Algorithm:** Logistic Regression

**Input Features:**
- CGPA
- IQ

**Target:**
- Placement

```text
CGPA + IQ
    ↓
StandardScaler
    ↓
Logistic Regression
    ↓
Placement Prediction