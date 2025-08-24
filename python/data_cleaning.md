# Cleaning Missing Values

The approach to handling missing values depends on the nature of the data and the percentage of missing data.

1. **Deletion:** If a feature (column) has a very high percentage of missing values (e.g., over `70-80%`), it's often best to delete the entire feature. If a few rows have missing data, and the dataset is large, you can delete the rows with missing values. However, this isn't recommended for smaller datasets, as you'd lose valuable information.

2. **Imputation:** This is the most common approach and involves replacing missing values with a substitute.

## Mean/Median/Mode Imputation

&emsp;&emsp; Mean imputation is suitable for features with a normal distribution and no significant outliers.

&emsp;&emsp; Median imputation is the most robust and widely used method for numerical features, especially when the data contains outliers or is skewed. The median is less affected by extreme values.

## Mode imputation 
&emsp;&emsp; is the standard for categorical features.

## Advanced Imputation
&emsp;&emsp; For more complex situations, advanced methods like K-Nearest Neighbors (KNN) imputation or multiple imputation by chained equations (MICE) can be used. These methods estimate missing values based on the relationships with other features in the dataset, often providing more accurate results.

# Encode Categorical Variables

Categorical variables (e.g., 'country' or 'color') must be converted into numerical formats for most machine learning algorithms. The choice of encoding method depends on whether the categories have an inherent order.

## One-Hot Encoding

&emsp;&emsp;This is the most common method for nominal categorical variables (variables without an order, like 'red', 'green', 'blue').

&emsp;&emsp;It creates a new binary column for each unique category. A value of 1 indicates the presence of that category, and 0 indicates its absence. This prevents the model from assuming an incorrect ordinal relationship.

&emsp;&emsp;It is the standard for algorithms like linear regression, logistic regression, and support vector machines (SVMs).

## Ordinal Encoding

&emsp;&emsp;This is used when categories have a natural, meaningful order (e.g., 'low', 'medium', 'high').

&emsp;&emsp;Each category is assigned an integer based on its rank (e.g., 'low' = 0, 'medium' = 1, 'high' = 2). This is useful for algorithms like decision trees and random forests, which can interpret the ordinal relationship.

## Other Encoding Methods
&emsp;&emsp;More advanced techniques like target encoding, binary encoding, or count encoding are used for high-cardinality features (features with many unique categories) to reduce the dimensionality that One-Hot Encoding would create.

# Scale Numeric Features

Scaling numeric features is essential for algorithms that are sensitive to the magnitude and range of the data. This includes distance-based algorithms like KNN, SVM, and K-means, as well as gradient-descent-based algorithms like linear and logistic regression and neural networks.

## Crucial Best Practice
Always perform feature scaling after splitting your data into training and test sets to prevent data leakage. The scaler should be fitted only on the training data and then used to transform both the training and test sets.

### Standardization (Z-score Normalization)

&emsp;&emsp;This is a robust and widely used technique.

&emsp;&emsp;It transforms the data to have a mean of 0 and a standard deviation of 1

$$z = \frac{x - \mu}{\sigma}$$


&emsp;&emsp;It works well with datasets that have a Gaussian (normal) distribution or when the algorithm assumes a normal distribution. It is also less affected by outliers than Min-Max scaling.

&emsp;&emsp;It is the standard for algorithms like linear regression and logistic regression.

### Normalization (Min-Max Scaling)

&emsp;&emsp;This method scales all feature values to a fixed range, typically [0, 1].

&emsp;&emsp;The formula is: 

$$
X_{scaled​}=\frac{X​−X_{min​X}}{X_{max}−X_{min}}
$$ 


&emsp;&emsp;It's a good choice for algorithms that require inputs to be within a specific range, such as neural networks and image processing algorithms.

&emsp;&emsp;A significant drawback is its s`ensitivity to outliers`, which can compress the majority of the data into a very small range.

### Robust Scaling

&emsp;&emsp;Use this technique when your dataset contains many outliers.

&emsp;&emsp;It scales the data using the median and the interquartile range (IQR), making it less affected by extreme values than other methods. 

The formula is: 

$$X_{scaled}​=\frac{X − Median}{IQR}$$