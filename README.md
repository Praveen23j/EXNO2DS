# EXNO2DS
# AIM:
      To perform Exploratory Data Analysis on the given data set.
      
# EXPLANATION:
  The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.
  
# ALGORITHM:
STEP 1: Import the required packages to perform Data Cleansing,Removing Outliers and Exploratory Data Analysis.

STEP 2: Replace the null value using any one of the method from mode,median and mean based on the dataset available.

STEP 3: Use boxplot method to analyze the outliers of the given dataset.

STEP 4: Remove the outliers using Inter Quantile Range method.

STEP 5: Use Countplot method to analyze in a graphical method for categorical data.

STEP 6: Use displot method to represent the univariate distribution of data.

STEP 7: Use cross tabulation method to quantitatively analyze the relationship between multiple variables.

STEP 8: Use heatmap method of representation to show relationships between two variables, one plotted on each axis.

## CODING AND OUTPUT
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
df=pd.read_csv("/content/titanic_dataset.csv")
df
```
![313158351-4069d465-7163-4516-959e-a5927d7ed43f](https://github.com/user-attachments/assets/bb851a88-9132-4ebb-b629-74840d91e1b3)

```
df.info()
```
![313158773-336e313e-86ed-4ca9-8d6f-12c11c021a96](https://github.com/user-attachments/assets/bd15e082-5265-4c3f-9eb5-3655410e0e63)

```
df.shape
```
![313159530-e2f8a0d5-e4d7-4242-8897-135b7ba283a5](https://github.com/user-attachments/assets/ca353c01-ad28-4e2b-a81c-7223a96c0a16)
```
import pandas as pd
df=pd.read_csv("/content/titanic_dataset.csv")
df.set_index("PassengerId",inplace=True)
print(df.set_index)
```
![313160218-9d5717de-831f-47bc-b1b2-8397289f3a48](https://github.com/user-attachments/assets/b55ccf06-9af9-4d7e-9fa4-c46ab2d4dcee)

```
df.describe()
```
![313160904-f9bc25c7-4d5e-447b-8fb0-918df31c3f1c](https://github.com/user-attachments/assets/1f112d3c-1f4b-43ce-9d5b-d9c294e8c5e6)
```
df.nunique()
```
![313161336-1b777e29-4a91-45f3-89fc-253bbce4ed09](https://github.com/user-attachments/assets/448e0806-e006-4447-b7ee-5e575b7f024b)
```
df["Survived"].value_counts()
```
![313162485-55e4fb63-ee1a-4172-8b86-d2b627f2e660](https://github.com/user-attachments/assets/6e102b81-38f3-4aff-856b-de51e4ebe101)
```
per=(df["Survived"].value_counts()/df.shape[0]*100).round(2)
per
```
![313162970-7c58eb4c-b52d-4082-bd8d-f590caec9095](https://github.com/user-attachments/assets/75df0a7f-f20b-4c73-ba83-9b9b636a137b)
```
sns.countplot(data=df,x="Survived")
```
![313233823-ad4efdd2-44f9-456f-a4a6-19dee993ca72](https://github.com/user-attachments/assets/93355551-33a0-4dea-8e2c-67f202918e4e)
```
df
```
![313234132-f179e05b-9937-42a9-aa9e-248272de5ec8](https://github.com/user-attachments/assets/e89da642-6392-4ff3-8b47-5de0cb4e3f74)
```
df.Pclass.unique()
```
![313234417-30624b4f-8992-407c-89c7-da46502033d2](https://github.com/user-attachments/assets/525207a3-aad0-4f13-8843-271449d221d1)
```
df.rename(columns={'sex':'Gender'},inplace=True)
df
```
![313234716-9c114f4f-776a-4cdc-a250-37aace7fa552](https://github.com/user-attachments/assets/f0c5605e-2fc1-4292-b062-8b3596b66490)
```
import seaborn as sns
df=pd.read_csv("/content/titanic_dataset.csv")
sns.catplot(x="Sex",col='Survived',kind="count",data=df,height=5, aspect=.7)
```
![313235041-babf8cfb-be74-4702-b986-7ad16e4f3b62](https://github.com/user-attachments/assets/0ebc1530-32a1-4eeb-a753-a7821a0081b1)
```
sns.catplot(x='Survived',hue='Sex',data=df,kind='count')
```
![313235322-2123b7f7-ff04-4132-af13-36f6b6df03bf](https://github.com/user-attachments/assets/7046124e-53f9-4929-a475-9409683e679c)
```
df.boxplot(column='Age',by="Survived")
```
![313235676-78d02657-3216-4c7e-8eb8-c1a42ac69845](https://github.com/user-attachments/assets/24295ce1-41de-4008-83f9-920bd2e9a991)

```
sns.scatterplot(x=df['Age'],y=df["Fare"])
```
![313235936-566ac388-e884-432b-af8a-ffc9b6f420fb](https://github.com/user-attachments/assets/73c14301-721a-46ae-a170-bddcc6b4820e)
```
import matplotlib.pyplot as plt
fig,ax1=plt.subplots(figsize=(8,5))
pt=sns.boxplot(ax=ax1,x='Pclass',y='Age',hue='Sex',data=df)
```
![313236249-237b77f3-3576-41a2-bf27-747d58cd7e7f](https://github.com/user-attachments/assets/2205b8f8-0031-4331-9d43-27b20f1020d5)
```
sns.catplot(data=df,col='Survived',x='Sex',hue='Pclass',kind='count')
```
![313236574-c476e292-9c93-48b9-b376-5c90c1015c7b](https://github.com/user-attachments/assets/9ee5aaeb-c4a1-43bf-95f6-0dd83e0afdc1)
```
import seaborn as sns
corr=df.corr()
sns.heatmap(corr,annot=True)
```
![313236845-7edfb83b-2e25-4385-9333-011243672b41](https://github.com/user-attachments/assets/125e85f2-438e-4b81-a980-cf2f993ed3df)
```
sns.pairplot(df)
```
![313237218-81b2a985-cb2b-4fd1-9753-d8d3d054855d](https://github.com/user-attachments/assets/0a9f14d4-6e31-4742-954c-c81b51e4213b)


# RESULT
 Code are sucessfully executed.  
