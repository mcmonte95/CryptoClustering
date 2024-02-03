# Cryptocurrency Clustering Challenge

This challenge explores the use of unsupervised learning to predict the impact of price changes on cryptocurrencies over 24-hour and 7-day periods. The process is divided into several steps, as outlined below.

## Table of Contents
- [Repository Guide](#repository-guide)
- [Data Preparation](#data-preparation)
- [Finding the Best Value for K](#finding-the-best-value-for-k)
- [Clustering with K-Means](#clustering-with-k-means)
- [Optimizing Clusters with PCA](#optimizing-clusters-with-pca)
- [Best Value for K with PCA Data](#best-value-for-k-with-pca-data)
- [Clustering with PCA Data](#clustering-with-pca-data)

## Repository Guide
- `Resources/`: This folder contains the raw CSV data file with cryptocurrency information used for analysis.
- `Crypto_Clustering.ipynb`: The Jupyter notebook where all the data preparation, analysis, and clustering are performed.

## Data Preparation

The data from the CSV file is normalized using the `StandardScaler()` module from scikit-learn. A new DataFrame is created with the scaled data, and the `coin_id` index from the original DataFrame is preserved.

## Finding the Best Value for K

The elbow method is employed to determine the optimal number of clusters (k). This involves:

- Creating a range of k values from 1 to 11.
- Calculating inertia for each k value to measure how well the data is clustered.
- Plotting an elbow curve to visually find the best k value.

## Clustering with K-Means

With the optimal k value identified:

- A K-Means model is initialized and fitted using the original scaled data.
- Cryptocurrencies are clustered, and a new column with predicted clusters is added to a copy of the original data.
- A scatter plot is created using hvPlot, with "price_change_percentage_24h" and "price_change_percentage_7d" as axes and clusters differentiated by color.

## Optimizing Clusters with PCA

Principal Component Analysis (PCA) is applied to the scaled data to reduce dimensionality to three principal components. The total explained variance of these components is calculated to understand the amount of information retained.

## Best Value for K with PCA Data

The elbow method is repeated using the PCA-reduced data to find a potentially different optimal k value. This new k value is compared with the one found using the original data.

## Clustering with PCA Data

- A new K-Means model is initialized with the best k value from the PCA data.
- The model is fitted, and cryptocurrencies are clustered using the PCA data.
- A scatter plot is created using hvPlot, this time with "PC1" and "PC2" as axes.


