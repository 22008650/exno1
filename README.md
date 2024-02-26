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
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
data = pd.read_csv("/content/SAMPLEIDS.csv")
data.head()
```
![ds1](https://github.com/22008650/exno1/assets/122548204/b7d07ca3-1ef5-46af-b9fd-56cfa8b73ba3)
```
data = pd.get_dummies(data)
data.isnull().sum()
```
![ds2](https://github.com/22008650/exno1/assets/122548204/50ff47d1-6d07-4037-8488-5ee83b2f1ebf)
```
columns_with_null = data.columns[data.isnull().any()]
import seaborn as sns
plt.figure(figsize=(10,10))
sns.barplot(columns_with_null)
plt.title("NULL VALUES")
plt.show()
```
![ds3](https://github.com/22008650/exno1/assets/122548204/0930b12f-e2eb-4426-9ced-7e822e3e1283)
```
for column in columns_with_null:
    median = data[column].median()  
    data[column].fillna(median, inplace=True)
data.isnull().sum().sum()
```
![ds4](https://github.com/22008650/exno1/assets/122548204/51de8fe7-4ff1-4998-b6bb-f6d0c9e56583)
# IQR
```
import pandas as pd
import seaborn as sns
ir = pd.read_csv("/content/iris (1).csv")
ir.head()
```
![ds1](https://github.com/22008650/exno1/assets/122548204/009aaa97-adbd-4be7-bdcf-2444108fbd6c)
```
ir.describe()
```
![image](https://github.com/22008650/exno1/assets/122548204/4f897426-5528-4b41-8054-0d8502421249)
```
sns.boxplot(x='sepal_width',data=ir)
```
![ds7](https://github.com/22008650/exno1/assets/122548204/9b7ff9a5-699c-4c6b-904c-e3d91c7a89ec)
```
c1=ir.sepal_width.quantile(0.25)
c3=ir.sepal_width.quantile(0.75)
iq=c3-c1
print(c3)
```
![image](https://github.com/22008650/exno1/assets/122548204/d1f76e58-f6f1-4b75-a83f-3c8f63f95291)
```
rid=ir[((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
rid['sepal_width']
```
![image](https://github.com/22008650/exno1/assets/122548204/f0c4d13f-a8fc-4d3d-99a5-e2971cb2e47a)
```
delid=ir[~((ir.sepal_width<(c1-1.5*iq))|(ir.sepal_width>(c3+1.5*iq)))]
delid
```
![image](https://github.com/22008650/exno1/assets/122548204/b64e46a8-2118-4005-8887-a4c99eeb6d35)
```
sns.boxplot(x='sepal_width',data=delid)
```
![image](https://github.com/22008650/exno1/assets/122548204/f3c2249e-d647-4b3b-bb99-0589d94b0679)
# Z Score
```
import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
import scipy.stats as stats
dataset=pd.read_csv("/content/heights.csv")
dataset
```
![image](https://github.com/22008650/exno1/assets/122548204/09285e61-3d2a-424c-b64d-1564d8bdebfc)
```
df = pd.read_csv("heights.csv")
q1 = df['height'].quantile(0.25)
q2 = df['height'].quantile(0.5)
q3 = df['height'].quantile(0.75)
```













# Result
Thus the given data is read,cleansed and the cleaned data is saved into the file.
