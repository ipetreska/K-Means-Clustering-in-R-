# K-Means-Clustering-in-R-
My Process foK-Means Clustering in R to identify workforce segments that are most at risk for attrition

# STEP 1: Install & Load necessary packages
install.packages("factoextra")
install.packages("cluster")

library(factoextra)
library(cluster)

# STEP 2: Run K-Means for K = 3 and K = 4
set.seed(123)
km3 <- kmeans(Attrition_Practice_Copy, centers = 3, nstart = 25)
km4 <- kmeans(Attrition_Practice_Copy, centers = 4, nstart = 25)

# STEP 3: Visualize Clusters (PCA Plot)
fviz_cluster(km3, data = Attrition_Practice_Copy, geom = "point", ellipse.type = "norm", main = "K = 3 Clusters") 
fviz_cluster(km4, data = Attrition_Practice_Copy, geom = "point", ellipse.type = "norm", main = "K = 4 Clusters")

# STEP 4: Compare Silhouette Scores
# For K = 3
sil3 <- silhouette(km3$cluster, dist(your_data))
fviz_silhouette(sil3)

# For K = 4
sil4 <- silhouette(km4$cluster, dist(your_data))
fviz_silhouette(sil4)

# NOTE: If you also ran K = 3, compare its silhouette width, if it’s lower than 0.56 or has more overlap, K = 4 is the better choice. 
