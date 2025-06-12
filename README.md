# 🎬 Movie Recommendation System

This project implements a **Content-Based Movie Recommendation System** that suggests similar movies based on **genre, popularity, and user ratings**. By leveraging **K-Means Clustering**, the system groups movies into clusters of similar characteristics and returns recommendations from the same cluster.

## 🚀 Features

- 🔍 Parses and processes complex genre metadata from the TMDb dataset
- 🧮 Encodes genres using `MultiLabelBinarizer`
- 📊 Scales numerical features like `vote_average` and `popularity`
- 📈 Determines the **optimal number of clusters** using Elbow and Silhouette methods
- 🧠 Applies **K-Means clustering** to segment similar movies
- 🎯 Returns **top-N recommendations** based on a relevance score:
  \[
  \text{Score} = \text{vote\_average} \times \log(1 + \text{popularity})
  \]

## 📦 Tech Stack

- **Language**: Python
- **Libraries**: 
  - `pandas`, `numpy` for data processing
  - `matplotlib`, `seaborn` for visualization
  - `scikit-learn` for clustering and preprocessing
  - `ast` for safe parsing of stringified lists

## 🗂 Dataset

- 📁 `movies_metadata.csv`  
  From [The Movies Dataset - TMDb](https://www.kaggle.com/datasets/rounakbanik/the-movies-dataset)

## 🔧 Workflow

1. **Load & Clean Data**  
   Drop null values in critical columns and parse genres.

2. **Feature Engineering**  
   - One-hot encode genres  
   - Normalize `vote_average` and `popularity` using MinMaxScaler  
   - Combine all features into a final matrix

3. **Optimal Cluster Selection**  
   - Run KMeans for k = 2 to 20  
   - Use **Elbow Method** and **Silhouette Score** to choose best k

4. **Clustering and Labeling**  
   - Fit KMeans with optimal k  
   - Assign each movie to a cluster

5. **Recommendation Logic**  
   - Get the cluster of the input movie  
   - Recommend top-N from same cluster using combined score

