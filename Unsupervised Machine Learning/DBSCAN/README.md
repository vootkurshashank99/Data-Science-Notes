# Personal Notes: DBSCAN Clustering

## Overview
This notebook serves as a personal reference for understanding and applying Density-Based Spatial Clustering of Applications with Noise (DBSCAN). It uses a sample retail dataset (`shopping_data.csv`) to explore the algorithm's mechanics, evaluation metrics, and hyperparameter tuning.

## Core Concepts Explored
* **Algorithm Mechanics:** Defining Core, Border, and Noise points based on Epsilon ($\epsilon$) and `MinPoints` density criteria.
* **Evaluation:** Using the Silhouette Score to measure cluster cohesion and separation:
  $$s(i) = \frac{b(i) - a(i)}{\max\{a(i), b(i)\}}$$
* **Visualizations:** Mapping features using static 2D/3D plots (`matplotlib`) and interactive 3D plots (`plotly.express`) to visually inspect noise and cluster boundaries.
* **Hyperparameter Tuning:** 
  * Implementing **Exhaustive Grid Search** to test combinations of Epsilon and `min_samples`.
  * Using the `kneed` library for **Automated Elbow Detection** on a K-Distance graph.

## Key Takeaways
* **Noise Identification:** DBSCAN is highly effective at isolating anomalous data points (labeled as `-1`).
* **Topological Limitations:** Density-based clustering struggled with this specific dataset's topology. 
  * Grid search optimization ($\epsilon = 0.1$) led to severe overfitting with hundreds of micro-clusters.
  * The Elbow method ($\epsilon \approx 0.67$) merged the majority of points into a single mass, resulting in a low Final Silhouette Score of **0.257**.
* **Next Steps:** Because DBSCAN failed to create distinct customer segments here, centroid-based approaches (like **K-Means**) should be applied next to compare partitioning effectiveness.
