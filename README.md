# EXP-10 Implementation-of-K-Means-Clustering-for-Customer-Segmentation

## AIM :
To write a program to implement the K Means Clustering for Customer Segmentation.

## Equipments Required :
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm :
1. Start
2. Data Preparation: Load and explore customer data.
3. Determine Optimal Clusters: Use the Elbow Method to find the best number of clusters.
4. Apply K Means Clustering: Perform clustering on customer data.
5. Visualize Segmented Customers: Plot clustered data to visualize customer segments.
6. End

## Program :
```
/*
Program to implement the K Means Clustering for Customer Segmentation.
Developed by: NITHYA D
RegisterNumber: 212223240110
*/
```
```
import pandas as pd
import matplotlib.pyplot as plt
data=pd.read_csv("Mall_Customers.csv")
data
data.head()
data.info()
data.isnull().sum()
from sklearn.cluster import KMeans
wcss=[]
for i in range(1,11):
  Kmeans=KMeans(n_clusters = i,init = "k-means++")
  Kmeans.fit(data.iloc[:,3:])
  wcss.append(Kmeans.inertia_)
plt.plot(range(1, 11), wcss[:10])
plt.xlabel("No. of Clusters")
plt.ylabel("WCSS")
plt.title("Elbow Method")
plt.show()
km=KMeans(n_clusters = 5)
km.fit(data.iloc[:,3:])
y_pred=km.predict(data.iloc[:,3:])
y_pred
data["cluster"]=y_pred
df0=data[data["cluster"]==0]
df1=data[data["cluster"]==1]
df2=data[data["cluster"]==2]
df3=data[data["cluster"]==3]
df4=data[data["cluster"]==4]
plt.scatter(df0["Annual Income (k$)"],df0["Spending Score (1-100)"],c="red",label="cluster0")
plt.scatter(df1["Annual Income (k$)"],df1["Spending Score (1-100)"],c="black",label="cluster1")
plt.scatter(df2["Annual Income (k$)"],df2["Spending Score (1-100)"],c="blue",label="cluster2")
plt.scatter(df3["Annual Income (k$)"],df3["Spending Score (1-100)"],c="green",label="cluster3")
plt.scatter(df4["Annual Income (k$)"],df4["Spending Score (1-100)"],c="magenta",label="cluster4")
plt.legend()
plt.title("Customer Segments")
```

## Output :
![image](https://github.com/user-attachments/assets/24da0dea-4f68-480f-be7b-eb3845180ad5)
![image](https://github.com/user-attachments/assets/e46f55b1-f48a-4946-9b43-725421cb2d77)

## Result :
Thus the program to implement the K Means Clustering for Customer Segmentation is written and verified using python programming.
