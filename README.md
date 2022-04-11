# Ex-04-EDA-EXPLORATORY DATA ANALYSIS

## AIM:
To perform Exploratory Data Analysis on the given data set.

## EXPLANATION:
The primary aim with exploratory analysis is to examine the data for distribution, outliers and anomalies to direct specific testing of your hypothesis.

## ALGORITHM:
### STEP 1:
Import the required packages to perform Data Cleansing,Removing Outliers and Exploratory Data Analysis.

### STEP 2:
Use boxplot method to analyze the outliers of the given dataset.

### STEP 3:
Remove the outliers using Inter Quantile Range method.

### STEP 4:
Use Countplot method to analyze in a graphical method for categorical data.

### STEP 5:
Use displot method to represent the univariate distribution of data.

### STEP 6:
Use cross tabulation method to quantitatively analyze the relationship between multiple variables.

### STEP 7:
Use heatmap method of representation to show relationships between two variables, one plotted on each axis.

## CODE:
```
import pandas as pd
import numpy as np
import seaborn as sns
df=pd.read_csv("supermarket.csv")
df.info()
df.isnull().sum()
df.boxplot()
Q1 = df.quantile(0.25)
Q3 = df.quantile(0.75)
IQR = Q3 - Q1
df = df[~((df < (Q1 - 1.5 * IQR)) |(df > (Q3 + 1.5 * IQR))).any(axis=1)]
df.boxplot()
df["City"].value_counts()
df["Customer type"].value_counts()
df["Gender"].value_counts()
df["Product line"].value_counts()
df["Payment"].value_counts()
df["Branch"].value_counts()
sns.countplot(x="Branch",data=df)
sns.countplot(x="Gender",data=df)
sns.countplot(x="Product line",data=df)
sns.countplot(x="Payment",data=df)
sns.countplot(x="Gender",hue="Product line",data=df)
sns.countplot(x="Customer type",hue="City",data=df)
sns.displot(df[df["Branch"]=="A"]["Gender"])
sns.displot(df["Branch"])
sns.displot(df[df["Product line"]=="Electronic accessories"]["Gender"])
sns.displot(df[df["Payment"]=="Credit card"]["Branch"])
pd.crosstab(df["Gender"],df["Branch"])
pd.crosstab(df["City"],df["Customer type"])
df.corr()
sns.heatmap(df.corr(),annot=True)
```

## OUTPUT
### EXAMINING THE DATA:
![162758075-29f81f79-29e5-40d0-88ad-7a30af27708a](https://user-images.githubusercontent.com/93427278/162784495-491a8284-dcae-441b-aefb-b485600266c2.png)

### BOXPLOT METHOD TO ANALYZE OUTLIERS:
![162758201-9c7dfe5a-c7ea-4467-b9b2-d37d5726013e](https://user-images.githubusercontent.com/93427278/162784596-65b42ede-dfb6-43b8-8338-cd1d956b8240.png)

### REMOVING OUTLIERS USING IQR METHOD:
![162758329-2e08357d-c01f-4752-b4b0-14424826b05b](https://user-images.githubusercontent.com/93427278/162784686-be925cc9-75a8-4501-a1ae-120aa41c4c51.png)

### COUNTPLOT METHOD FOR DATA ANALYSIS:
![162758438-377a5b64-bf16-4bb9-b47e-ddc9db889c45](https://user-images.githubusercontent.com/93427278/162784801-781473af-7466-49a2-b130-b13d8e590ac8.png)
![162758484-5c4c5224-004b-454d-a9fb-07476d638255](https://user-images.githubusercontent.com/93427278/162784829-845a69c8-e44e-4ea9-b1bb-598053d0e397.png)
![162758516-7889eeff-2843-45ec-a03e-d6ec90e54289](https://user-images.githubusercontent.com/93427278/162784863-76578575-b5e7-4c89-9ddd-9615f1c97e39.png)

### DISPLOT METHOD FOR DATA ANALYSIS:
![162758681-a5c1192e-34ef-431c-82d6-47a821eb4ec7](https://user-images.githubusercontent.com/93427278/162784924-ed2284e0-58ad-46d7-a2f8-3ab550b0b3ff.png)
![162758713-5920e387-ef09-43dc-81b0-44d3661c97d4](https://user-images.githubusercontent.com/93427278/162784971-d059aa18-c5f2-4080-b7f0-dee95a5cf718.png)

### COUNTPLOT METHOD TO COMPARE TWO ENTITIES:
![162758888-e4907048-c0bb-49b3-af8e-95c276853349](https://user-images.githubusercontent.com/93427278/162785081-b9a831c8-539d-4b0a-87a2-a12cc2bebc3b.png)

### CROSS TABULATION FOR DATA ANALYSIS:
![162759041-4ff0ca5d-097b-4350-a663-c68ff318d5aa](https://user-images.githubusercontent.com/93427278/162785135-0a06553d-2536-42e8-b491-5530d16b4f43.png)

### CORRELATION METHOD:
![162759166-7a0db8b3-8a6c-4864-be9e-9f225be5a52c](https://user-images.githubusercontent.com/93427278/162785198-bc35d8e3-4ace-4823-9a85-42ab94072b82.png)

## INFERENCE:
1. More customers visited the supermarket from the city Yangon.
2. The most purchased department in the supermarket is Fashion accessories.
3. Cash and E-wallet is the most preferred payment mode by the customers.
4. Maximum number of customers visited the Branch A of supermarket.
5. Male customers are highest visitors of supermarket in Branch B.

## RESULT:
Hence the given data set has undergone data cleansing and outlier removal.Later Exploratory data analysis is done to get inferences from the given data set.
