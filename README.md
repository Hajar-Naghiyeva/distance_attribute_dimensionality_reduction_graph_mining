# README for Programming Assignment 3

## CSCI4700 – Data Mining

## Assignment Overview

This README file provides instructions and explanations for completing the programming assignment for **CSCI4700 – Data Mining**. The assignment focuses on analyzing datasets and implementing various data mining techniques. The datasets and tasks are described below.

---

## Datasets

1. **Adult Dataset**: 
   - Source: UCI Machine Learning Repository.
   - Description: Contains 14 attributes and 48,842 data points.

2. **E. coli Gene Data**: 
   - Files Provided: 
     - `Ecoli.txt` (undirected network).
     - `Ecoli-directed.txt` (directed network).
   - Description: Represents gene interactions as a network.

---

## Tasks

### 1. Distance and Attribute Dependence
- **Steps:**
  1. Discretize numerical attributes using the equal-frequency method.
  2. One-hot encode all attributes.
  3. Select a random sample of 100 data points.
  4. Compute closest and farthest points using Hamming and Jaccard distances.
  5. Create a contingency matrix for the `education` and `race` attributes. Compute the χ2 statistic using a custom function.
     - Output: χ2 value and p-value.
     - Test: Independence of `education` and `race` at a 99% confidence level.
  6. Conduct an additional test for another pair of attributes and report the results.

---

### 2. Dimensionality Reduction
- **Steps:**
  1. Combine `race` and `education` into a single attribute using Principal Component Analysis (PCA).
  2. Output 100 samples with the new single attribute.
  3. Report the variance explained by the first principal component.

**Appendix A:**
Steps for PCA Implementation:
1. Standardize the data to have zero mean.
2. Compute the covariance matrix.
3. Find eigenvalues and eigenvectors of the covariance matrix.
4. Sort eigenvalue-eigenvector pairs in descending order.
5. Select the top eigenvalues.
6. Transform original data using the eigenvectors corresponding to the top eigenvalues.

---

### 3. Graph Mining

#### 3.1 Undirected Network Analysis
- Compute the following for the network represented in `Ecoli.txt`:
  1. **Diameter**:
     - Measure: Maximum shortest path length between all reachable pairs of nodes.
     - Ignore paths where nodes are unreachable.
     - Do not use built-in diameter functions.
  2. **Degree Distribution**:
     - Plot degree (`k`) vs. probability (`P(k)`) on a log-log scale.
     - Fit a line using linear regression and report the slope.
     - Omit outliers (use judgment for a better fit).
  3. **Clustering Coefficient**:
     - For nodes with degree < 2, set the local clustering coefficient to 0.
     - Do not use built-in clustering-related functions.

#### 3.2 Directed Network Analysis 
- For the `Ecoli-directed.txt` network:
  1. Compute PageRank for each gene using the power-iteration method.
     - Use a damping factor, \( d = 0.1 \).
     - Normalize the final eigenvector to have unit length.
  2. Compute the dominant eigenvalue and eigenvector of the PageRank matrix iteratively.
  3. Output the top 10 genes by PageRank score.

**Appendix B:**
Steps for Dominant Eigenvalue and Eigenvector Calculation:
1. Initialize vector \( \mathbf{p}_0 = [1, 1, \ldots, 1] \).
2. Update vector: \( \mathbf{p}_k = M \times \mathbf{p}_{k-1} \).
3. Normalize \( \mathbf{p}_k \) by dividing each element by the largest value in \( \mathbf{p}_k \).
4. Check convergence: Stop if \( \|\mathbf{p}_k - \mathbf{p}_{k-1}\| < 0.001 \).

---

## Notes
- Built-in libraries (NumPy, csv) are allowed for data reading and parsing.
- Do NOT use built-in functions such as `cov`, `degree_distribution`, or `PageRank`.
- You may verify your results by comparing them to built-in functions but ensure the code uses custom implementations.

---
