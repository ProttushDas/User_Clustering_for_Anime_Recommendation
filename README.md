# User-Clustering-for-Anime-Recommendation

This repository contains a Jupyter Notebook that performs user clustering for anime recommendation. The project uses unsupervised machine learning techniques to group users based on their anime preferences, which can then be used to recommend new anime to users within the same cluster.

***

### Project Description
This project analyzes anime and user rating datasets to identify distinct user groups. It preprocesses the data to handle missing values and a large number of ratings. By converting user ratings into a user-anime matrix and applying Principal Component Analysis (PCA) to reduce dimensionality, the project visualizes user preferences in a 3D space. Finally, it uses the K-Means clustering algorithm to segment users into groups with similar tastes.

The analysis is based on two datasets:
* `anime.csv`: Contains information about various anime, including name, genre, type, episodes, rating, and number of members.
* `rating.csv`: Contains a large number of user ratings for different anime.

***

### Dependencies
The project requires the following Python libraries:
* `numpy`
* `pandas`
* `matplotlib`
* `mpl_toolkits.mplot3d`
* `sklearn` (specifically `KMeans`, `PCA`, and `silhouette_score`)
* `wordcloud`

You can install them using pip:
`pip install numpy pandas matplotlib scikit-learn wordcloud`

***

### Methodology

The notebook follows these key steps:

1.  **Data Loading and Preprocessing**: The `anime.csv` and `rating.csv` datasets are loaded. Null values in the `anime` dataset are dropped to ensure data quality. A new feature, `mean_rating`, is calculated for each user from the `rating` dataset. Users' "liked" anime are identified as those with a rating greater than or equal to their average rating. This filtered data is then merged with the anime information.

2.  **User-Anime Matrix Creation**: A cross-tabulation matrix (`user_anime`) is created where rows represent users and columns represent anime. The values indicate whether a user liked a particular anime. This matrix serves as the input for the clustering algorithm.

3.  **Dimensionality Reduction with PCA**: Principal Component Analysis (PCA) is applied to the high-dimensional user-anime matrix to reduce it to 3 principal components. This step makes the data more manageable for visualization and clustering.

4.  **Clustering with KMeans**: The K-Means algorithm is used to group users into clusters based on their PCA-transformed preferences. The optimal number of clusters is determined by evaluating both the **Elbow Method** and the **Silhouette Score**. The analysis determined that **4 clusters** provide a good balance, as indicated by the elbow point and a high silhouette score.

5.  **Cluster Analysis**: Each cluster is analyzed to understand its defining characteristics. The most liked genres and top-rated anime within each cluster are identified to provide a clear profile of each user group. This information can be used to generate personalized recommendations.
