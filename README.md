### EX4 Implementation of Cluster and Visitor Segmentation for Navigation patterns
### DATE: 07/02/2026
### AIM: To implement Cluster and Visitor Segmentation for Navigation patterns in Python.
### Description:
<div align= "justify">Cluster visitor segmentation refers to the process of grouping or categorizing visitors to a website, 
  application, or physical location into distinct clusters or segments based on various characteristics or behaviors they exhibit. 
  This segmentation allows businesses or organizations to better understand their audience and tailor their strategies, marketing efforts, 
  or services to meet the specific needs and preferences of each cluster.</div>
  
### Procedure:
1) Read the CSV file: Use pd.read_csv to load the CSV file into a pandas DataFrame.
2) Define Age Groups by creating a dictionary containing age group conditions using Boolean conditions.
3) Segment Visitors by iterating through the dictionary and filter the visitors into respective age groups.
4) Visualize the result using matplotlib.

### Program1:
python
```
cluster = {"Young":(df['Age']<=30),"Middle":((df['Age']>30)&(df['Age']<=50)),"Old":(df['Age']>50)}
count=[]
for group,condition in cluster.items():
  visitors=df[condition]
  count.append(len(visitors))
  print(f"The visitors on {group} age are")
  print(visitors)
  print("count=",len(visitors))
```
### Output:
<img width="1130" height="821" alt="image" src="https://github.com/user-attachments/assets/c56c1a18-0ae4-4417-b94b-dbff55db081f" />

### Visualization:

```
import matplotlib.pyplot as plt
plt.figure(figsize=(8,6))
plt.bar(['Young','Middle','Old'],count,color='skyblue')
plt.xlabel('Age Group')
plt.ylabel('Number of Visitors')
plt.title('Visitors Distribution Across Age Groups')
plt.show()
```

### Output:
<img width="1320" height="850" alt="image" src="https://github.com/user-attachments/assets/55e4d3d9-fde5-4f32-9788-c62f130bf312" />

### Program2:
```
from sklearn.preprocessing import StandardScaler
from sklearn.cluster import KMeans
df1=df['Age']
df2=df['Income']
df3=pd.concat([df1,df2],axis=1)
s=StandardScaler()
newdf=s.fit_transform(df3)
k=KMeans(n_clusters=4,random_state=55)
df3['cluster']=k.fit_predict(newdf)
df3
```
### Output:

<img width="958" height="812" alt="image" src="https://github.com/user-attachments/assets/3631b0f9-1939-4335-9797-151babe1a8be" />


### Visualization:
python 
```
import matplotlib.pyplot as plt
plt.figure(figsize=(8,6))
plt.scatter(x=df3['Age'],y=df3['Income'],c=df3['cluster'])
plt.xlabel('Age')
plt.ylabel('Income')
plt.title('Visitors Distribution in Different Clusters')
plt.show()
```
### Output:


<img width="1285" height="843" alt="image" src="https://github.com/user-attachments/assets/58871080-02a1-489c-be48-a1648c2b6bfe" />

### Result:
Thus the Cluster and Visitor Segmentation for Navigation patterns is implemented successfully using Python program.
