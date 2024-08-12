# Credit Card Fraud Detection

## 1. Project Overview
Credit card fraud is a significant problem that requires robust detection methods to minimize losses. This project aims to analyze and build models for detecting fraudulent transactions in a highly imbalanced dataset. We utilized various data preprocessing techniques, explored data visualization, and applied machine learning models to achieve the best possible results in detecting fraud.

## 2. Dataset Background
The dataset consists of transactions made by European cardholders in September 2013, encompassing 284,807 transactions over two days. Among these, only 492 transactions were fraudulent, making the dataset highly imbalanced, with fraudulent transactions accounting for just 0.172% of the total.

### 2.1 Features
- **Time**: Seconds elapsed between each transaction and the first transaction in the dataset.
- **Amount**: Transaction amount, which could be used for cost-sensitive learning.
- **Class**: Response variable (1 for fraud, 0 for non-fraud).
- **V1-V28**: Principal components obtained via PCA, with confidentiality preventing access to the original features.

## 3. Exploratory Data Analysis (EDA)
### 3.1 Univariate and Bivariate Analysis
- **Data Points**: 285,000 transactions with 30 features, including time, amount, and labeled classes.
- **Data Skewness**: 99.83% of the transactions were non-fraudulent.
- **Time Feature**: Showed a bimodal distribution with peaks likely corresponding to daytime and nighttime transactions.
- **Amount Feature**: Transactions over 10,000 units were minimal and excluded from the dataset.
- **Fraudulent Transactions**: Mostly involved small amounts (<1000 units) and were independent of the time of day.

### 3.2 Conclusions from EDA
- The dataset was clean, with no null values.
- The high skewness necessitated techniques like undersampling and stratified splitting for model accuracy.
- Fraudulent transactions tended to be of low amounts and were not time-dependent.

## 4. Data Preprocessing
### 4.1 Scaling
- **Standardization**: Applied to make data more Gaussian-like.
- **Robust Scaler**: Used to handle outliers.

### 4.2 Splitting the Dataset
- **StratifiedKFold**: Maintained class distribution in training and test datasets, crucial for handling the imbalanced nature of the data.

### 4.3 Undersampling
- Performed to balance the dataset, reducing the dominance of non-fraudulent transactions.

### 4.4 Outlier Detection and Removal
- **Interquartile Range (IQR)**: Used to remove outliers from highly correlated features.

### 4.5 Dimensionality Reduction and Visualization
- **PCA**: Reduced dimensionality for visualization.
- **t-SNE**: Used for a non-linear reduction to visualize data in lower dimensions.

## 5. Modeling and Evaluation
### 5.1 Model Selection
- **Logistic Regression**: Simple and effective, especially for imbalanced data.
- **K-Nearest Neighbors (KNN)**: Considered for its ability to perform well in small datasets.
- **Support Vector Classifier (SVC)**: Chosen for its robustness in handling imbalanced datasets.
- **Decision Tree Classifier**: Included for its interpretability and ability to handle complex relationships.

### 5.2 Evaluation Metrics
- **Cross-Validation Score**: Used to evaluate model performance.
- **ROC AUC Score**: Assessed the overall ability of the models to distinguish between classes.
- **Confusion Matrix**: Visualized true vs. predicted classifications.
- **Precision, Recall, F1-Score**: Focused on recall for the fraud class to minimize false negatives.
- **Average Precision Score**: Provided insight into the model's precision-recall balance.

### 5.3 Model Performance
- **SVC**: Showed the best performance in minimizing false negatives, crucial for fraud detection.
- **Logistic Regression, KNN, and Decision Tree**: Had comparable or better precision/F1 scores but were less effective in recall for the fraud class.

## 6. Testing and Final Evaluation
- **Final Testing**: Conducted on the original test data to evaluate real-world performance.
- **Best Model**: SVC, due to its superior recall rate for the fraud class, making it the most effective model for this application.

## 7. Conclusion
This project effectively applied various data preprocessing techniques and machine learning models to tackle the problem of credit card fraud detection. Despite the challenges posed by an imbalanced dataset, we successfully identified a model that balances precision and recall, with a focus on minimizing false negatives to ensure that fraudulent transactions are correctly identified.

