# Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM:
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm
1. Import the necessary packages.
2. Read the given csv file and display the few contents of the data.
3. Import KMeans and use for loop to calculate the within cluster sum of squares the data.
4. Plot the wcss for each iteration, also known as the elbow method plot.
5. Predict the clusters and plot them. 

## Program:
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: Udayakumar R
RegisterNumber:  212222230163
*/
```
```python
import pandas as pd
import matplotlib.pyplot as plt
data = pd.read_csv('/content/Mall_Customers.csv')
data.head()

data.info()
data.isnull().sum()

from sklearn.cluster import KMeans
wcss = []

for i in range(1,11):
  kmeans = KMeans(n_clusters = i,init = "k-means++")
  kmeans.fit(data.iloc[:,3:])
  wcss.append(kmeans.inertia_)

plt.plot(range(1,11),wcss)
plt.xlabel("No of Clusters")
plt.ylabel("wcss")
plt.title("Elbow Method")

km = KMeans(n_clusters = 5)
km.fit(data.iloc[:,3:])

y_pred = km.predict(data.iloc[:,3:])
y_pred

data["cluster"] = y_pred
df0 = data[data["cluster"]==0]
df1 = data[data["cluster"]==1]
df2 = data[data["cluster"]==2]
df3 = data[data["cluster"]==3]
df4 = data[data["cluster"]==4]
plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"],c="red",label="cluster0")
plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"],c="black",label="cluster1")
plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"],c="blue",label="cluster2")
plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"],c="green",label="cluster3")
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],c="magenta",label="cluster4")
plt.legend()
plt.title("Customer Segments")
```

## Output:
## Data.head()
![image](https://github.com/R-Udayakumar/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/118708024/340c7efe-e8c3-4146-82e5-661c25d41502)

## Data.info()
![image](https://github.com/R-Udayakumar/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/118708024/f5fcc2cc-602f-4479-9046-a3d9136361df)

## Data.isnull().sum() 
![image](https://github.com/R-Udayakumar/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/118708024/51402416-a33c-4aa3-9061-85c0ec68333c)

## Elbow method Graph
![image](https://github.com/R-Udayakumar/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/118708024/12d18709-4308-4412-a5e9-d4383a101bdb)

## KMeans clusters
![image](https://github.com/R-Udayakumar/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/118708024/8d0fdfdf-47ef-45be-8351-4a3b0d2a5f38)

## Customer segments Graph
![image](https://github.com/R-Udayakumar/Implementation-of-K-Means-Clustering-for-Customer-Segmentation/assets/118708024/e262302e-2479-47cd-a2e8-761c35c123b8)



## Result:
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
