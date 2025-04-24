# Exno:1
Data Cleaning Process

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output
```
Name : HEMANTH KUMAR S
Reg No : 212224040115
```
```
import pandas as pd
df=pd.read_csv("/content/SAMPLEIDS (1).csv")
df
```
![image](https://github.com/user-attachments/assets/d62f9ba7-68f1-40a4-8b85-eb0457b16917)
```
df.shape
```
![image](https://github.com/user-attachments/assets/735c3645-190a-4a63-888f-20922cb717d8)
```
df.describe()
```
![image](https://github.com/user-attachments/assets/2975f10a-4799-4344-8e05-80635dff4899)
```
df.info()
```
![image](https://github.com/user-attachments/assets/ab3586b3-43eb-4a0d-ad3f-dcd6174f6c62)
```
df.head(10)
```
![image](https://github.com/user-attachments/assets/f1166ad9-4599-4b7a-ba37-b9167dffbfc3)
```
df.tail(10)
```
![image](https://github.com/user-attachments/assets/b88a5131-09fc-4f8d-9ddb-57e605cfa0ad)
```
df.isna().sum()
```
![image](https://github.com/user-attachments/assets/1b3c4924-cf53-490b-ab2b-8fac7d1843ed)
```
df.dropna(how='any').shape
```
![image](https://github.com/user-attachments/assets/0bdd13f7-e468-4537-9cd0-283f36a5f87e)
```
df.dropna(how='any')
```
![image](https://github.com/user-attachments/assets/32dee7c6-5575-465d-a8c0-6898a69c2d26)
```
mean=df.TOTAL.mean()
mean
```
![image](https://github.com/user-attachments/assets/8b016e80-f74e-4985-87d4-cf00a957f75a)
```
df.TOTAL.fillna(mean,inplace=True)
df
```
![image](https://github.com/user-attachments/assets/e8cba06e-b726-4578-bc68-2196981b1751)
```
df.isnull().sum()
```
![image](https://github.com/user-attachments/assets/a34a6cd5-fac8-443a-883f-23591d62fd78)
```
df.M1.fillna(method='ffill',inplace=True)
df
```
![image](https://github.com/user-attachments/assets/b9098b2d-a227-462b-b69c-e3794f790d8b)
```
df.isnull().sum()
```
![image](https://github.com/user-attachments/assets/f1bbd7b0-43cd-481f-8c5f-2609ded8485a)
```
df.M2.fillna(method='ffill',inplace=True)
df
```
![image](https://github.com/user-attachments/assets/227dd31b-bf39-43b8-b3e1-643aa13d36d8)
```
df.isna().sum()
```
![image](https://github.com/user-attachments/assets/b1a0336f-6e18-458e-a148-d8fc29df63ca)
```
df.M3.fillna(method='ffill',inplace=True)
df
```
![image](https://github.com/user-attachments/assets/212da724-e203-4bb2-b842-edf8e01aae68)
```
df.isnull().sum()
```
![image](https://github.com/user-attachments/assets/6e223f52-89e5-44fc-b43a-2d1b648ede4b)
```
df.duplicated()
```
![image](https://github.com/user-attachments/assets/7949a9dd-e891-49a6-baf8-662211b12197)
```
df.drop_duplicates(inplace=True)
df
```
![image](https://github.com/user-attachments/assets/d757d0ca-c750-47c3-b7f5-f76efe3f576c)

```
df.duplicated()
```
![image](https://github.com/user-attachments/assets/a43f473f-07db-481e-8daf-96d78e317c83)
```
df['DOB']
```
![image](https://github.com/user-attachments/assets/116de1f3-fcfd-44f4-8322-ac4ae652a86b)
```
import seaborn as sns
sns.heatmap(df.isnull(),yticklabels=False,annot=True)
```
![image](https://github.com/user-attachments/assets/5fc8756a-8c0a-4f19-9216-9dd93eec3039)
```
df.dropna(inplace=True)
sns.heatmap(df.isnull(),yticklabels=False,annot=True)
```
![image](https://github.com/user-attachments/assets/683d3765-9413-4112-a180-217ad007b96e)
```
age=[1,3,28,27,25,92,30,39,40,50,26,24,29,94]
df=pd.DataFrame(age)
df
```
![image](https://github.com/user-attachments/assets/1f646b8b-caa3-4127-a931-21492deef134)
```
sns.boxplot(data=df)
```
![image](https://github.com/user-attachments/assets/1affe173-3754-457c-abae-cef1f029b72a)
```
sns.scatterplot(data=df)
```
![image](https://github.com/user-attachments/assets/81a72a97-93cc-4364-b293-423ee248008f)
```
q1=df.quantile(0.25)
q2=df.quantile(0.5)
q3=df.quantile(0.75)
iqr=q3-q1
iqr
```
![image](https://github.com/user-attachments/assets/d38d1bf8-db34-4659-801c-c62fe36283e1)
```
import numpy as np
Q1=np.percentile(df,25)
Q3=np.percentile(df,75)
IQR=Q3-Q1
IQR

```
![image](https://github.com/user-attachments/assets/5ab29fce-d480-4420-b1c4-d950454e29ac)
```
lower_bound=Q1-1.5*IQR
upper_bound=Q3+1.5*IQR
lower_bound

```
![image](https://github.com/user-attachments/assets/d98d93ad-08eb-40e6-90f6-2dbc9cbac65c)
```
upper_bound
```
![image](https://github.com/user-attachments/assets/4ce9858c-8b47-4613-8e13-a89fd4507363)
```
outliers=[x for x in age if x<lower_bound or x>upper_bound]
print("Q1:",Q1)
print("Q3:",Q3)
print("IQR:",IQR)
print("Lower Bound:",lower_bound)
```
![image](https://github.com/user-attachments/assets/72ef5147-4b19-4f25-914c-75eba5398be7)
```
print("Upper Bound:",upper_bound)
print("Outliers:",outliers)
```
![image](https://github.com/user-attachments/assets/5e31152c-80e0-44e6-a2e2-4d0a44ae2c5f)
```
df=df[((df>=lower_bound)&(df<=upper_bound))]
df
```
![image](https://github.com/user-attachments/assets/8051c99c-cad8-4474-94ea-d907acc5d74b)
```
df=df.dropna()
df
```
![image](https://github.com/user-attachments/assets/d010a9c5-5739-452a-97d2-49741bd257a6)
```
sns.boxplot(data=df)
```
![image](https://github.com/user-attachments/assets/9697034b-e143-4723-8bca-6a8bbfed7140)
```
sns.scatterplot(data=df)
```
![image](https://github.com/user-attachments/assets/e2d21cf1-d900-44b9-bf65-b353abeb3dd9)
```
data=[1,2,2,2,3,1,1,15,2,2,2,3,1,1,2]
mean=np.mean(data)
std=np.std(data)
print('mean of the dataset is',mean)
print('std.deviation is',std)
```
![image](https://github.com/user-attachments/assets/da6242be-5063-447c-9744-9f003c3ee07c)
```
threshold=3
outlier=[]
for i in data:
  z=(i-mean)/std
  if z>threshold:
    outlier.append(i)
print('outlier in dataset is',outlier)
```
![image](https://github.com/user-attachments/assets/c6ed162a-8681-4af9-88e7-19c1529f15a9)
```
import pandas as pd
import numpy as np
import seaborn as sns
from scipy import stats
data={'weight':[12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,
66,69,202,72,75,78,81,84,232,87,90,93,96,99,258]}
df=pd.DataFrame(data)
df
```
![image](https://github.com/user-attachments/assets/0fbb2164-fba2-4ab5-a1f3-c72d8e0eacac)
```
z=np.abs(stats.zscore(df))
print(df[z['weight']>3])
```
![image](https://github.com/user-attachments/assets/de0edd9e-3e78-450f-8ec8-e8b28851f2c7)





# Result
Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score method.
