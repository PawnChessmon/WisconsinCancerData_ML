# Wisconsin Cancer Data Analysis

This repository contains an R Markdown document (`WisconsinCancerData.Rmd`) that performs exploratory data analysis, dimensionality reduction using Principal Component Analysis (PCA), and various clustering techniques on the **Wisconsin Cancer Dataset**. The main goal is to understand the underlying structure of the data and see how well unsupervised learning methods align with actual cancer diagnoses (Malignant vs. Benign).

---

## Analysis Overview

The R Markdown document goes through these key steps:

### Data Loading and Preparation

First, the **Wisconsin Cancer dataset** is downloaded from a URL and loaded into an R data frame. The 30 features (characteristics of the cells) are then extracted into a matrix for analysis. A binary `diagnosis` vector (1 for Malignant, 0 for Benign) is also created; this acts as our reference for checking the clustering results.

### Principal Component Analysis (PCA)

Before PCA, the code calculates and displays **column means** and **standard deviations** for an initial look at the data. Then, **Principal Component Analysis (PCA)** is performed on the scaled data. PCA is a powerful technique that reduces the number of dimensions by transforming the data into new, uncorrelated variables (principal components) that capture most of the data's variance. A **summary of the PCA results** and a **scree plot** are generated to help visualize how much variance each component explains, which can guide how many components to keep.

### PCA Visualization

To better understand the PCA results, a **biplot** is created. This plot shows both individual data points and original variables in the space of the first two principal components. This helps us see how variables contribute to the components and how data points relate to each other. Additionally, **scatter plots** of principal components (PC1 vs. PC2, PC1 vs. PC3, PC2 vs. PC3) are generated and **colored by the actual diagnosis**. These plots visually show if PCA effectively separates malignant from benign cases.

### Variance Explained

The analysis calculates and plots the **proportion of variance explained (PVE)** by each individual principal component, along with the **cumulative PVE**. These plots are crucial for deciding how many principal components are needed to capture a significant amount of the total variance in the dataset.

### Clustering Analysis

The document explores two different clustering techniques to group similar data points:

* **Hierarchical Clustering**: This method involves calculating **Euclidean distances** between scaled data points. Then, it builds a hierarchical tree (dendrogram) using the "complete" linkage method. The tree is then **cut to form 4 clusters**. The resulting cluster assignments are compared against the actual diagnoses using a **contingency table** to see how well the clusters match the known categories.
* **K-Means Clustering**: **K-means clustering** is performed with **2 centers**, reflecting the two known diagnosis types (Malignant and Benign). The algorithm runs multiple times with different starting points to find the best clustering solution. The k-means cluster assignments are then compared with both the actual diagnoses and the hierarchical clustering results to see how consistent they are.

### Clustering on Principal Components

Finally, the analysis performs **hierarchical clustering again**, but this time it uses only the **first 7 principal components** instead of all the original features. This demonstrates how using dimensionality reduction can sometimes improve clustering efficiency or results. This new hierarchical tree is also **cut into 4 clusters**, and these clusters (derived from the PCs) are compared with the actual diagnoses, as well as the results from the previous hierarchical and k-means clustering for a full comparison.

---

## Source

The Wisconsin Cancer Dataset was originally used in the following research:

K. P. Bennett and O. L. Mangasarian: "Robust Linear Programming Discrimination of Two Linearly Inseparable Sets"

---

