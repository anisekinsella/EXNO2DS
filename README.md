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
df=pd.read_csv('titanic_dataset.csv')
df
```

<img width="1247" height="446" alt="Screenshot 2026-05-13 161628" src="https://github.com/user-attachments/assets/afdc690a-7e73-4ab8-a830-c0aef9f36dc2" />


```
df.info()

```

<img width="440" height="407" alt="image" src="https://github.com/user-attachments/assets/7315ecaf-0969-45b0-9700-c67c5f1dd2d3" />


```
df.shape

```

<img width="113" height="41" alt="image" src="https://github.com/user-attachments/assets/51625434-46a1-40d9-91f7-1a27cf34ed71" />


```
df.set_index('PassengerId',inplace=True)
df.describe()

```

<img width="652" height="307" alt="image" src="https://github.com/user-attachments/assets/d4d0a186-53f3-49d7-9a5c-ab377f8a9e53" />


```
df.shape

```

<img width="102" height="40" alt="image" src="https://github.com/user-attachments/assets/387a1974-cf04-4c17-8cc2-26651672036a" />


Categorical Data analysis
```
df.nunique()

```

<img width="166" height="267" alt="image" src="https://github.com/user-attachments/assets/54874cf7-b34a-4c13-ac14-b13716b76c78" />


```
df["Survived"].value_counts()

```

<img width="283" height="80" alt="image" src="https://github.com/user-attachments/assets/539460d0-b18a-4788-84ff-f89ed019f085" />


```
per=(df["Survived"].value_counts()/df.shape[0]*100).round(2)
per

```

<img width="323" height="73" alt="image" src="https://github.com/user-attachments/assets/b7e9250e-6b0a-4b2a-9145-d89b98b0531a" />



```
import seaborn as sns
sns.countplot(data=df,x='Survived')

```

<img width="737" height="576" alt="image" src="https://github.com/user-attachments/assets/26d3ad89-8c72-4b50-bdd7-2c811c337087" />


```
df

```

<img width="1217" height="477" alt="image" src="https://github.com/user-attachments/assets/bb46051c-f9dc-4870-82d6-0099bdad04f5" />


```
df.Pclass.unique()

```

<img width="300" height="36" alt="image" src="https://github.com/user-attachments/assets/fd582f68-d26b-4357-85cd-1873af8e4268" />


```
df.rename(columns={'Sex':'Gender'},inplace=True)

df
```
<img width="1213" height="482" alt="image" src="https://github.com/user-attachments/assets/b844993b-f55d-433d-8008-85757c87b5ad" />



Bivariate Analysis
```
sns.catplot(x="Gender",col="Survived",kind="count",data=df,height=5,aspect=.7)

```

<img width="945" height="650" alt="image" src="https://github.com/user-attachments/assets/3b1de711-91f8-4c5f-8f06-4366224dce4e" />


```
df.boxplot(column="Age",by="Survived")

```
<img width="740" height="612" alt="image" src="https://github.com/user-attachments/assets/5cd7ce18-0e01-4c98-a1b6-7d03f1d7b89f" />


```
sns.scatterplot(x=df["Age"],y=df["Fare"])

```
<img width="742" height="575" alt="image" src="https://github.com/user-attachments/assets/711612fb-4ec1-4af3-9dcc-31c82cd2a0ba" />


```
sns.jointplot(x="Age",y="Fare",data=df)

```

<img width="746" height="758" alt="image" src="https://github.com/user-attachments/assets/fffa1e6c-d1cd-40e3-a648-b22d495579d3" />


Multivariate Analysis
```
import matplotlib.pyplot as plt
fig,ax1=plt.subplots(figsize=(8,5))
plt=sns.boxplot(ax=ax1,x='Pclass',y='Age',hue='Gender',data=df)

```


<img width="762" height="480" alt="image" src="https://github.com/user-attachments/assets/3df5084a-6864-400a-8ad3-47f1e4ed549e" />


```
sns.catplot(data=df,col="Survived",x="Gender",hue="Pclass",kind="count")

```

<img width="763" height="396" alt="image" src="https://github.com/user-attachments/assets/7e7b224a-6c2b-4c43-9a7f-9cc656be22be" />


```
import numpy as np
#Select only numeric columns before calculating correlation 
numeric_df=df.select_dtypes(include=np.number)

#Calculate correlation for numeric columns only
corr=numeric_df.corr()

#Generate the heatmap
sns.heatmap(corr, annot=True)

```

<img width="675" height="567" alt="image" src="https://github.com/user-attachments/assets/2d5c6a68-0ea3-46ac-bec3-24adb454fefc" />


```
sns.pairplot(df)

```
<img width="746" height="770" alt="image" src="https://github.com/user-attachments/assets/0d7b533b-ab13-4461-9b8f-e735f0c9391d" />



# RESULT
        <<INCLUDE YOUR RESULT HERE>>
