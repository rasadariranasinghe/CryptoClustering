# Crypto Clustering Project

## Overview

This project focuses on applying K-means clustering to a dataset of cryptocurrency market data. The goal is to identify clusters of cryptocurrencies based on various performance metrics and then optimize the clustering process using Principal Component Analysis (PCA). The project aims to determine whether clustering results improve when reducing dimensionality with PCA.

The tasks involve:
1. Normalizing the data.
2. Finding the optimal number of clusters using the elbow method.
3. Clustering cryptocurrencies using K-means.
4. Reducing the feature set using PCA and repeating the clustering process.
5. Comparing the results of clustering with the original data and the PCA-reduced data.

## Technologies Used

- **Python**: For data analysis, clustering, and visualization.
- **Pandas**: For data manipulation and preparation.
- **hvPlot**: For visualizing the elbow curves and cryptocurrency clusters.
- **scikit-learn**: For K-means clustering, StandardScaler, and PCA.
- **Jupyter Notebook**: For developing and running the code.

## Data Source

The dataset used in this project is **crypto_market_data.csv**, which contains various performance metrics for different cryptocurrencies. Such as
- `price_change_percentage_24h`: The price change in the last 24 hours.
- `price_change_percentage_7d`: The price change in the last 7 days.

## Project Workflow

### 1. Data Preprocessing
- The dataset is first loaded into a Pandas DataFrame.
- Basic summary statistics and visualizations are created to understand the data.
- The data is then normalized using the `StandardScaler()` module from scikit-learn to ensure that all features have equal importance in the clustering process.

### 2. Finding the Optimal Number of Clusters (Original Data)
- The elbow method is used to find the best value for `k` (number of clusters) on the original scaled data.
- Inertia values (sum of squared distances between samples and their cluster center) are computed for `k` values ranging from 1 to 11.
- A line chart is plotted to identify the optimal `k` based on the elbow point, where inertia values start to diminish at a slower rate.

### 3. K-means Clustering with Original Data
- The K-means model is initialized with the best value for `k` (found using the elbow method).
- The model is then fitted to the original scaled data, and clusters are predicted.
- A scatter plot is created using `hvPlot` with the following settings:
  - **X-axis**: `price_change_percentage_24h`
  - **Y-axis**: `price_change_percentage_7d`
  - **Color**: Cluster labels
  - **Hover Information**: Cryptocurrency `coinid`

### 4. Dimensionality Reduction Using PCA
- PCA is applied to reduce the features from the original data to three principal components.
- The explained variance for each principal component is computed, and the total explained variance is used to assess how much information the three principal components retain.
- A new DataFrame is created with the PCA data, and the index is set to the `coinid` from the original DataFrame.

### 5. Finding the Optimal Number of Clusters (PCA Data)
- The elbow method is repeated on the PCA-reduced data to find the best value for `k`.
- Inertia values are computed for `k` values ranging from 1 to 11, and a line chart is plotted to identify the optimal `k`.

### 6. K-means Clustering with PCA Data
- The K-means model is initialized with the best value for `k` (found using the elbow method on PCA data).
- The model is then fitted to the PCA data, and clusters are predicted.
- A scatter plot is created using `hvPlot` with the following settings:
  - **X-axis**: `PC1`
  - **Y-axis**: `PC2`
  - **Color**: Cluster labels
  - **Hover Information**: Cryptocurrency `coinid`

### 7. Composite Plots
- A composite plot is created using `hvPlot` and the `+` operator to compare:
  1. The elbow curves from the original and PCA data.
  2. The scatter plots of the clusters from the original and PCA data.

## Key Questions Answered

### 1. What is the Best Value for k Using the Original Data?
The elbow method is used to determine the best value for `k`. This value corresponds to the point where the inertia values start decreasing at a slower rate, indicating diminishing returns from adding more clusters.

### 2. What is the Best Value for k Using the PCA Data?
Similarly, the elbow method is applied to the PCA-reduced data to find the optimal number of clusters. The best `k` value may differ from the original data due to the reduced feature set.

### 3. What is the Impact of Using Fewer Features to Cluster the Data Using K-means?
Using fewer features (through PCA) can improve the clustering process by reducing data and focusing on the most important variance in the data. The total explained variance helps us understand how much information is retained after dimensionality reduction.

## Conclusion

This project demonstrated how to:
- Apply K-means clustering to a cryptocurrency dataset.
- Use the elbow method to determine the best number of clusters.
- Optimize clustering by reducing dimensionality with PCA.
- Visualize the clustering results using composite plots to compare different methods.

By using PCA, we reduced the feature set, which helped simplify the clustering process while retaining most of the variance in the data. This project offers a clear comparison between clustering with the original data and with PCA-reduced data, highlighting the trade-offs between complexity and performance.

## File Structure

- `Crypto_Clustering.ipynb`: Jupyter Notebook containing the code for the project.
- `crypto_market_data.csv`: Dataset containing cryptocurrency market information.

