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

<img width="540" height="194" alt="image" src="https://github.com/user-attachments/assets/7d84d345-0557-44fa-a846-f1e8a80794e6" />

```
df.info()
```

<img width="434" height="370" alt="image" src="https://github.com/user-attachments/assets/95f2aefb-b885-4446-9127-7104297c5d12" />

~~~
df.shape
~~~

<img width="110" height="40" alt="image" src="https://github.com/user-attachments/assets/7aac514a-b9f0-4425-a20b-e4ef2332363b" />


Categorical data Analysis

~~~
df.nunique()
~~~

<img width="167" height="238" alt="image" src="https://github.com/user-attachments/assets/31389f04-c452-43fd-a066-859e641e490e" />

~~~
df["Survived"].value_counts()
~~~

<img width="320" height="94" alt="Screenshot 2026-05-13 160542" src="https://github.com/user-attachments/assets/b3212960-449b-4d92-8dbd-d36b14988dcf" />

~~~
per=(df["Survived"].value_counts()/df.shape[0]*100).round(2)
per
~~~

<img width="285" height="81" alt="image" src="https://github.com/user-attachments/assets/fa275275-7136-4c5e-a2d8-66e97930f7fc" />

~~~
import seaborn as sns
sns.countplot(data=df,x='Survived')
~~~

<img width="538" height="409" alt="image" src="https://github.com/user-attachments/assets/08b086a8-e8b2-40fb-824e-784076de324d" />

~~~
df
~~~

<img width="532" height="207" alt="image" src="https://github.com/user-attachments/assets/ba4ccb6c-ebd2-4aab-8600-d9700bbd655b" />

~~~
df.Pclass.unique()
~~~

<img width="265" height="41" alt="image" src="https://github.com/user-attachments/assets/525da28b-2477-4fc5-abed-054bb4fe5f13" />

~~~
df.rename(columns={'Sex':'Gender'},inplace=True)

df
~~~
<img width="535" height="220" alt="image" src="https://github.com/user-attachments/assets/644cf478-937d-4497-8519-d4e348e34bc3" />

~~~
sns.catplot(x="Gender",col="Survived",kind="count",data=df,height=5,aspect=.7)
~~~
<img width="506" height="345" alt="image" src="https://github.com/user-attachments/assets/0f606ffa-eb86-4bf6-bb23-117660017cee" />


~~~
df.boxplot(column="Age",by="Survived")
~~~
<img width="511" height="426" alt="image" src="https://github.com/user-attachments/assets/5952fd0b-7688-48d3-a781-6aec118eba96" />

~~~
sns.scatterplot(x=df["Age"],y=df["Fare"])
~~~
<img width="496" height="375" alt="image" src="https://github.com/user-attachments/assets/f6b70758-6712-4079-97a6-e4e547b29576" />

~~~
sns.jointplot(x="Age",y="Fare",data=df)
~~~
<img width="494" height="496" alt="image" src="https://github.com/user-attachments/assets/2347529b-300f-4b60-920e-f6cff2131782" />

Multivariate Analysis
~~~
import matplotlib.pyplot as plt
fig,ax1=plt.subplots(figsize=(8,5))
plt=sns.boxplot(ax=ax1,x='Pclass',y='Age',hue='Gender',data=df)

~~~
<img width="528" height="345" alt="image" src="https://github.com/user-attachments/assets/8ed49df9-4a64-44e3-848d-71f9cc961d3b" />

~~~
sns.catplot(data=df,col="Survived",x="Gender",hue="Pclass",kind="count")
~~~
<img width="536" height="263" alt="image" src="https://github.com/user-attachments/assets/7fe2ae59-55f1-47fb-9263-0220ce8c03b2" />

~~~
import numpy as np
#Select only numeric columns before calculating correlation 
numeric_df=df.select_dtypes(include=np.number)

#Calculate correlation for numeric columns only
corr=numeric_df.corr()

#Generate the heatmap
sns.heatmap(corr, annot=True)

~~~
<img width="538" height="433" alt="image" src="https://github.com/user-attachments/assets/b9965ed1-52ef-43b4-8640-c989a8cea123" />

~~~
sns.pairplot(df)

~~~
<img width="539" height="544" alt="image" src="https://github.com/user-attachments/assets/262cf67f-1aa0-4b30-894d-54c99df07b3d" />













# RESULT
~~~
    Thus exploratory data analysis on the given data set is executed successfully.
~~~
