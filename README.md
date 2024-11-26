# Comprehensive Analysis of Smartphone Sensor Data Using Machine Learning Techniques

## Introduction
This project provides a comprehensive analysis of smartphone sensor data collected from volunteers performing various activities. The analysis encompasses:
- Preprocessing steps such as outlier reduction and dimensionality reduction using Principal Component Analysis (PCA).
- Clustering analysis performed using K-means and Density-Based Spatial Clustering of Applications with Noise (DBSCAN).

The objective is to uncover meaningful patterns and structures in the data to gain insights into human activity recognition through smartphone sensors.

---

## Dataset Explanation
The dataset consists of sensor readings captured from smartphones worn by 30 volunteers aged 19-48 while performing six activities:
- WALKING
- WALKING_UPSTAIRS
- WALKING_DOWNSTAIRS
- SITTING
- STANDING
- LAYING

### Data Collection
- **Device:** Samsung Galaxy S II positioned on the waist.
- **Sensors:** 3-axial linear acceleration and 3-axial angular velocity at 50Hz.
- **Preprocessing:**
  - Signals were preprocessed to separate gravitational and body motion components.
  - Noise filters and fixed-width windows (2.56 seconds with 50% overlap, 128 readings per window) were applied.
  - A Butterworth low-pass filter (0.3 Hz cutoff frequency) separated gravitational forces from body motion components.

### Feature Extraction
Feature vectors were extracted from each window by calculating variables from the time and frequency domains, representing aspects of human activity like acceleration, velocity, and frequency components.

---

## Data Preprocessing
### Outlier Reduction
- Identified and removed using the z-score method to improve data quality and reduce noise.

### Dimensionality Reduction with PCA
- PCA was used to:
  - Reduce the number of features while preserving data variance.
  - Address multicollinearity.
  - Improve computational efficiency.
- The cumulative explained variance ratio determined the optimal number of principal components to retain.

---

## Clustering Analysis
### K-means Clustering
- **Method:** Applied to PCA-transformed data to identify distinct clusters.
- **Evaluation:**
  - Elbow Method and Silhouette Score determined the optimal number of clusters.
  - Cluster centroids analyzed for relevance to human activities.

### DBSCAN Clustering
- **Method:** Clustered the preprocessed data based on density.
- **Parameters:** Optimal `eps` and `min_samples` determined using the k-distance plot and Silhouette Score.
- **Results:**
  - Identified clusters of varying shapes and sizes.
  - Highlighted potential noise points for further investigation.

---

## Results and Discussion
### K-means Clustering Results
- Produced clusters based on data variance.
- Optimal number of clusters: **3**.
- Cluster characteristics:
  - **Cluster 0:** Activities involving high linear acceleration (e.g., walking, walking upstairs, walking downstairs).
  - **Cluster 1:** Stationary activities (e.g., sitting, standing).
  - **Cluster 2:** Complex movements indicating transitions between postures or activities.

### DBSCAN Clustering Results
- Identified clusters based on density.
- Highlights:
  - Effective in detecting clusters with irregular shapes or varying densities.
  - Identified **499 noise points**, indicating potential outliers or anomalous behaviors.

### Outlier Reduction
- Improved the quality and robustness of clustering results by mitigating noise impact using the z-score method.

---

## Conclusion
The comprehensive analysis of smartphone sensor data using PCA, K-means, and DBSCAN yielded valuable insights into human activity recognition. Future work could explore:
- Advanced feature engineering techniques.
- Refinement of clustering algorithms.
- Validation using additional datasets.

---

## How to Run the Notebook
1. **Dependencies:** Ensure the following Python libraries are installed:
   ```
   numpy
   pandas
   matplotlib
   seaborn
   sklearn
   ```
2. **Run the Notebook:** Open and execute the cells sequentially in a Jupyter Notebook environment.
3. **Input Data:** Ensure the dataset is located in the specified directory within the notebook.

---

## Acknowledgments
This project utilizes smartphone sensor data collected from volunteers for research purposes in human activity recognition.
