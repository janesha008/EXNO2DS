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

# CODING AND OUTPUT

### Importing Libraries
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt 
import seaborn as sns
```
### Load Dataset
```
df=pd.read_csv("titanic_dataset.csv")
```
### Analyze Outliers
```
sns.boxplot(x=df['Fare'])
```

<img width="520" height="432" alt="image" src="https://github.com/user-attachments/assets/df613699-6f93-4872-89f0-9f40b69c3220" />

### Data Cleaning
```
df.dropna(inplace=True)
q1 = df['Fare'].quantile(0.25)
q3 = df['Fare'].quantile(0.75)
IQR = q3 - q1
lower = q1 - 1.5 * IQR
upper = q3 + 1.5 * IQR
df=df[(df['Fare'] >= lower) & (df['Fare'] <= upper)]
```
### Count Plot
```
sns.countplot(data=df,x='Survived')
plt.title('Survival Distribution')
```

<img width="563" height="453" alt="image" src="https://github.com/user-attachments/assets/6d13d269-af84-41ab-9b3f-9c0c89abaa04" />

### Distribution Plot
```
sns.histplot(df['Fare'])
plt.show()
```

<img width="563" height="432" alt="image" src="https://github.com/user-attachments/assets/432d884a-7fb9-46d1-8d29-f509cb7118a1" />

### Cross Tabulation
```
pd.crosstab(df['Survived'],df['Pclass'])
```

<img width="145" height="151" alt="image" src="https://github.com/user-attachments/assets/b98ec6b2-6927-4737-b319-c3c6011a2656" />

### Heatmap
```
sns.heatmap(df.corr())
```

<img width="597" height="488" alt="image" src="https://github.com/user-attachments/assets/a3b46ecb-da70-4916-bf6e-7e2142f8fcd9" />

# RESULT
Exploratory Data Analysis on the given data set is performed successfully.
