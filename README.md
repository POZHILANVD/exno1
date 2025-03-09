### Register No.: 212223240118
### Name : POZHILAN V D

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
df = pd.read_csv("SAMPLEIDS.csv")
df
```

![image](https://github.com/user-attachments/assets/9de6f037-7661-4d10-be86-86bf8ddec782)

```
df.head(5)
```

![image](https://github.com/user-attachments/assets/ff2de00a-8684-4548-8e6d-6b51352a1f20)

```
df.tail(5)
```

![image](https://github.com/user-attachments/assets/58f4f018-00db-4969-abeb-d5a8c17a200d)

```
df.isnull()
```

![image](https://github.com/user-attachments/assets/aea9e253-e448-4331-b859-e4f85eea2b82)

```
df.notnull()
```

![image](https://github.com/user-attachments/assets/10e751eb-1edb-4433-96ae-1a7d1d65f03d)

```
df.info()
```

![image](https://github.com/user-attachments/assets/800ae18d-874a-4bc9-a17e-6d80effe5e86)

```
df.describe()
```

![image](https://github.com/user-attachments/assets/0a5b7fa9-fb3e-4b59-9c5e-452e41ad5d78)

```
df.isnull().sum()
```

![image](https://github.com/user-attachments/assets/722222e8-655b-491b-aa54-122c6a8cb452)

```
df.dropna(axis=1)
```

![image](https://github.com/user-attachments/assets/6a7e0bc7-a534-4b4e-b240-420ed6fd26e8)

```
df.dropna(axis=0)
```

![image](https://github.com/user-attachments/assets/4e2115d0-62ed-4a4c-a8fb-c6875c96c1c9)

```
df.fillna(0)
```

![image](https://github.com/user-attachments/assets/06b52556-d603-44e3-bb49-1fcb813d847c)

```
df.fillna(method='ffill')
```

![image](https://github.com/user-attachments/assets/1ec5931d-57c4-4ea6-9db3-0076682e05f7)

```
df.fillna(method='bfill')
```

![image](https://github.com/user-attachments/assets/257c892b-fd86-495b-8842-09e782d822ac)

```
df.fillna({'GENDER':'MALE','NAME':'SRI','ADDRESS':'POONAMALEE','M1':'98','M2':'87','MS':'76','M4':'92','TOTAL':'305','AVG':'93.5'})
```

![image](https://github.com/user-attachments/assets/d693c3f2-816b-4173-af41-0739d9ee7fcb)

```
ir=pd.read_csv("iris.csv")
ir
```

![image](https://github.com/user-attachments/assets/5202ff99-e75a-403b-900f-0d57c72b9b76)

```
ir.describe()
```

![image](https://github.com/user-attachments/assets/31e60852-f439-4942-aeda-5df5d3d3f890)

```
ir.info()
```

![image](https://github.com/user-attachments/assets/8e92749b-f31c-4f3f-b083-aea15bf38c70)

```
import seaborn as sns
sns.boxplot(x='sepal_width',data=ir)
```

![image](https://github.com/user-attachments/assets/d48dc594-5e65-4e0d-9cc2-7ebb28f52f3a)

```
ir.isnull().sum()
```

![image](https://github.com/user-attachments/assets/cb45c5b1-9a22-42f3-8875-06077e59c669)

```
q1=ir.sepal_width.quantile(0.25)
q3=ir.sepal_width.quantile(0.75)
iqr=q3-q1
print(iqr)
```

![image](https://github.com/user-attachments/assets/37eedef6-e7e2-4245-a38f-e28a472a9a5a)

```
q2=ir.sepal_width.quantile(0.50)
print(q2)
```

![image](https://github.com/user-attachments/assets/3d3c1950-e51e-4714-851f-c52f7c3eb363)

```
rid=ir[((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
rid['sepal_width']
```

![image](https://github.com/user-attachments/assets/3f28c2a3-668d-4ae5-8104-7f08e3526c36)

```
rid=ir[~((ir.sepal_width<(q1-1.5*iqr))|(ir.sepal_width>(q3+1.5*iqr)))]
rid
```

![image](https://github.com/user-attachments/assets/54218cbf-16ab-4edb-a347-8a8ecdf32266)

```
sns.boxplot(x='sepal_width',data=rid)
```

![image](https://github.com/user-attachments/assets/cfbb82db-e817-4600-8bcb-81b6969a045f)

```
import numpy as np
import scipy.stats as stats
z=np.abs(stats.zscore(ir['sepal_width']))
z
```

![image](https://github.com/user-attachments/assets/cfb0caac-c56c-4167-a015-72eaaa4b7f2f)

```
df1=ir[z<0.8]
df1
```

![image](https://github.com/user-attachments/assets/3eb554c4-7b91-44d5-a1f5-c091d41b1adc)


# Result
Thus the given data successfully performed data cleaning and saved the cleaned data to a file.
