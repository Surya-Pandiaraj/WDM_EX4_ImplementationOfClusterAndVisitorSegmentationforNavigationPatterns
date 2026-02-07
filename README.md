### NAME: SURYA P <br>
### REG NO: 212224230280 <br> 
### Date: 07/02/2026

## EX. No. 4 : Implementation of Cluster and Visitor Segmentation for Navigation patterns

### AIM : 
To implement Cluster and Visitor Segmentation for Navigation patterns in Python.

### DESCRIPTION :

<div align= "justify">Cluster visitor segmentation refers to the process of grouping or categorizing visitors to a website, 
  application, or physical location into distinct clusters or segments based on various characteristics or behaviors they exhibit. 
  This segmentation allows businesses or organizations to better understand their audience and tailor their strategies, marketing efforts, 
  or services to meet the specific needs and preferences of each cluster.</div>
  
### PROCEDURE :

1) Read the CSV file: Use pd.read_csv to load the CSV file into a pandas DataFrame.
2) Define Age Groups by creating a dictionary containing age group conditions using Boolean conditions.
3) Segment Visitors by iterating through the dictionary and filter the visitors into respective age groups.
4) Visualize the result using matplotlib.

### PROGRAM :

```python
import pandas as pd
import matplotlib.pyplot as plt

# read the csv file
df = pd.read_csv("C:\\Users\\admin\\Downloads\\clustervisitor.csv")

# define age-based clusters
clusters = {
    "Young": df["Age"] <= 25,
    "Middle": (df["Age"] > 25) & (df["Age"] <= 50),
    "Old": df["Age"] > 50
}

visitor_counts = []

# segment visitors and display results
for group, condition in clusters.items():
    visitors = df[condition]
    count = len(visitors)
    visitor_counts.append(count)

    print(f"\nVisitors in {group} group:")
    print("\n")
    print(visitors)
    print(f"number of visitors in {group}: {count}")
```

```python
import pandas as pd
import matplotlib.pyplot as plt
from sklearn.cluster import KMeans
from sklearn.preprocessing import StandardScaler

df = pd.read_csv("C:\\Users\\admin\\Downloads\\clustervisitor.csv")

df.columns = df.columns.str.strip().str.lower()

df['income'] = df['age'] * 2000

X = df[['age', 'income']]

scaler = StandardScaler()
X_scaled = scaler.fit_transform(X)

kmeans = KMeans(n_clusters=3, random_state=42)
df['cluster'] = kmeans.fit_predict(X_scaled)
### OUTPUT :

<img width="495" height="820" alt="image" src="https://github.com/user-attachments/assets/825a8596-ec31-4c52-95b9-97a9443007bb" />
```

### VISUALIZATION :

```python
plt.figure(figsize=(8, 6))
plt.bar(clusters.keys(), visitor_counts)
plt.xlabel("Age groups")
plt.ylabel("Number of Visitors")
plt.title("Visitor Segmentation based on Age")
plt.show()
```

```python
plt.scatter(df['age'], df['income'], c=df['cluster'])
plt.xlabel('Age')
plt.ylabel('Income')
plt.title('K-means Clustering (Age vs Income)')
plt.show()
```
### OUTPUT :

<img width="859" height="539" alt="image" src="https://github.com/user-attachments/assets/65a28eb3-6749-42f1-959b-d5a2163e6462" />
<img width="772" height="457" alt="image" src="https://github.com/user-attachments/assets/0e61b2d3-76f1-4001-8eef-37dec84289f1" />

### RESULT :
Thus the Implementation of Cluster and Visitor Segmentation for Navigation patterns in Python has been executed Successfully.
