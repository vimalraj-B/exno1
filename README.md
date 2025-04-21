![Screenshot 2025-04-21 180032](https://github.com/user-attachments/assets/896f58c0-127e-476d-bc02-d3290f4388a5)![Screenshot 2025-04-21 174756](https://github.com/user-attachments/assets/8e5e1330-7cd0-4e0e-90a5-a9b775a59dd4)![Screenshot 2025-04-21 174512](https://github.com/user-attachments/assets/9b6846fb-4687-4133-80fd-2301ae075190)# Exno:1
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
df=pd.read_csv("/content/SAMPLEIDS (1).csv")
df
```
![Screenshot 2025-04-21 132352](https://github.com/user-attachments/assets/f09e1419-28e2-456c-a808-17946c6500bc)

```
df.describe()
```
![Screenshot 2025-04-21 173411](https://github.com/user-attachments/assets/ca8a9843-20c2-4128-966e-7f52ab5f055d)

```
df.info()
```

![Screenshot 2025-04-21 173450](https://github.com/user-attachments/assets/77aec8a4-09cb-4c29-8f12-231a2331d679)

```
df.shape[0]
```
![Screenshot 2025-04-21 173545](https://github.com/user-attachments/assets/67f5903a-8784-42bf-8d57-8238e419f309)

```
df.shape
```
![Screenshot 2025-04-21 173607](https://github.com/user-attachments/assets/42f31758-c3a2-4994-81a0-2ec3518a1d92)

```
df.head(10)
```
![Screenshot 2025-04-21 173637](https://github.com/user-attachments/assets/18b3e566-55b5-4c96-b34b-dccb2651c14c)

```
df.tail(10)
```
![Screenshot 2025-04-21 173707](https://github.com/user-attachments/assets/3e27fbb5-a967-44fe-90a0-b422fbd4e243)

```
df.isna().sum()
```
![Screenshot 2025-04-21 173759](https://github.com/user-attachments/assets/cb5dbc21-7b1d-4190-a0eb-61a78b6d28a8)

```
df.dropna(how='any').shape
```
![Screenshot 2025-04-21 173826](https://github.com/user-attachments/assets/9d6472b3-0823-477a-a94d-28c32afe28d1)

```
x=df.dropna(how='any')
x
```
![Screenshot 2025-04-21 173909](https://github.com/user-attachments/assets/3319fb97-858b-4229-9cca-fe64c738c91c)

```
mn=df.TOTAL.mean()
mn
```
![Screenshot 2025-04-21 173946](https://github.com/user-attachments/assets/6ffb2662-1d6d-4fd7-a259-090e95d11248)

```
df.TOTAL.fillna(mn,inplace=True)
df
```
![Screenshot 2025-04-21 174050](https://github.com/user-attachments/assets/f2b60fd1-3a0d-4000-837f-14452a1d39c5)

![Screenshot 2025-04-21 174121](https://github.com/user-attachments/assets/e9d90c58-e8ad-4e3c-9f1f-2e3450c2658f)

```
df.isnull().sum()
```
![Screenshot 2025-04-21 174201](https://github.com/user-attachments/assets/b7cd1c54-fe52-48ed-8fe1-0dc2e716bbfe)

```
df.M1.fillna(method='ffill',inplace=True)
df
```
![Screenshot 2025-04-21 174248](https://github.com/user-attachments/assets/c5bd3277-d21b-4d8b-b2fe-b6047eacc876)

![Screenshot 2025-04-21 174306](https://github.com/user-attachments/assets/8e21873c-d8e8-4fc6-a7cc-e2448608a443)

```
df.duplicated()
```
![Screenshot 2025-04-21 174405](https://github.com/user-attachments/assets/b8f1aa38-a506-4856-ad48-c39e55d11918)

```
df.drop_duplicates(inplace=True)
df
```
![Screenshot 2025-04-21 174437](https://github.com/user-attachments/assets/f8498284-1334-4b1f-9b00-c3b47392d7ad)

```
df['DOB']
```
![Screenshot 2025-04-21 174512](https://github.com/user-attachments/assets/849cea36-9b83-4231-ac03-49f602bc04ea)

```
import seaborn as sns
sns.heatmap(df.isnull(),yticklabels=False,annot=True)
```
![Screenshot 2025-04-21 174607](https://github.com/user-attachments/assets/c08ab7e6-5b61-4b07-8de0-ebc9f9b017ec)

```
df.dropna(inplace=True)
sns.heatmap(df.isnull(),yticklabels=False,annot=True)
```

![Screenshot 2025-04-21 174650](https://github.com/user-attachments/assets/9f7e3d2c-99eb-4e61-80e7-609545d6bff8)

```
age=[1,3,28,27,25,92,30,39,40,50,26,24,29,94]
df=pd.DataFrame(age)
df
```

![Screenshot 2025-04-21 174730](https://github.com/user-attachments/assets/79659b2e-f555-4245-9331-0a2edd097cc0)

```
sns.boxplot(data=df)
```

![Screenshot 2025-04-21 174756](https://github.com/user-attachments/assets/53aa5407-1f78-4e4b-9a7d-456a5f0ccfe8)

```
sns.scatterplot(data=df)
```

![Screenshot 2025-04-21 174922](https://github.com/user-attachments/assets/60842fdb-d847-4103-a259-3e0b97ed1a1c)

```
q1=df.quantile(0.25)
q2=df.quantile(0.5)
q3=df.quantile(0.75)
iqr=q3-q1
iqr
```
![Screenshot 2025-04-21 175005](https://github.com/user-attachments/assets/121688d0-3a8e-42fa-8b16-16616ace2582)

```
import numpy as np
Q1=np.percentile(df,25)
Q3=np.percentile(df,75)
IQR=Q3-Q1
IQR
```
![Screenshot 2025-04-21 175138](https://github.com/user-attachments/assets/7a0158ce-fe5a-477f-bb7a-5e623a0b7e56)

```
lower_bound=Q1-1.5*IQR
upper_bound=Q3+1.5*IQR
lower_bound
upper_bound
```

![Screenshot 2025-04-21 175219](https://github.com/user-attachments/assets/2d08f40d-1c6e-4502-a141-5c58f36752d2)

```
outliers=[x for x in age if x<lower_bound or x>upper_bound]
print("Q1:",Q1)
print("Q3:",Q3)
print("IQR:",IQR)
print("Lower Bound:",lower_bound)
print("Upper Bound:",upper_bound)
print("Outliers:",outliers)
```

![Screenshot 2025-04-21 175305](https://github.com/user-attachments/assets/193f6429-dd1e-4b22-9ef8-d8945e31697e)

```
df=df[((df>=lower_bound)&(df<=upper_bound))]
df
```
![Screenshot 2025-04-21 175338](https://github.com/user-attachments/assets/098863f6-532c-47b3-b925-8e0a613fe133)

```
df=df.dropna()
df
```
![Screenshot 2025-04-21 175407](https://github.com/user-attachments/assets/d4806840-96a5-4c74-8aa7-892388bb29f4)

```
sns.boxplot(data=df)
```
![Screenshot 2025-04-21 175438](https://github.com/user-attachments/assets/a8bd8a30-4e5f-413b-ac5e-48de133ae2cf)

```
sns.scatterplot(data=df)
```
![Screenshot 2025-04-21 175505](https://github.com/user-attachments/assets/24b4a097-7f75-4fc7-a3be-bc4050f530e2)

```
data=[1,2,2,2,3,1,1,15,2,2,2,3,1,1,2]
mean=np.mean(data)
std=np.std(data)
print('mean of the dataset is',mean)
print('std.deviation is',std)
```
![Screenshot 2025-04-21 175637](https://github.com/user-attachments/assets/ceab5ae2-1df0-4816-9a63-89b3c0785759)

```
threshold=3
outlier=[]
for i in data:
z=(i-mean)/std
if z>threshold:
outlier.append(i)
print('outlier in dataset is',outlier)
```
![Screenshot 2025-04-21 175722](https://github.com/user-attachments/assets/dd68ce33-f4e8-4619-b732-c26801cd6c6b)

```
import pandas as pd
import numpy as np
import seaborn as sns
from scipy import stats
data={'weight':[12,15,18,21,24,27,30,33,36,39,42,45,48,51,54,57,60,63,66,69,202,72,75,78,81,84,232,87,90,93,96,99,258]}
df=pd.DataFrame(data)
df
```
![Screenshot 2025-04-21 175914](https://github.com/user-attachments/assets/a2e077ae-940e-4c48-a696-83ec829e4fc4)
![Screenshot 2025-04-21 175920](https://github.com/user-attachments/assets/cebd368b-bed9-4cdd-a285-a8a36af8ff5f)

```
z=np.abs(stats.zscore(df))
print(df[z['weight']>3])
```
![Screenshot 2025-04-21 180032](https://github.com/user-attachments/assets/56ac36ad-3c95-40c2-8f11-bbf41f6e74c5)


# Result

```
Thus we have cleaned the data and removed the outliers by detection using IQR and Z-score.
```
