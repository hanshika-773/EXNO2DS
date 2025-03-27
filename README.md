# EXNO 2
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
dt=pd.read_csv("/content/titanic_dataset.csv")
dt
```
```
dt.info()
```
![Screenshot 2025-03-27 151941](https://github.com/user-attachments/assets/9747e0f7-2e66-4df4-8b79-cedc0d9e9103)
```
#DISPLAY NO OF ROWS AND COLUMNS
print("Number of Rows:", dt.shape[0])
print("Number of Columns:", dt.shape[1])
```
![Screenshot 2025-03-27 152024](https://github.com/user-attachments/assets/195711f7-b544-4354-b334-23f847016495)
```
#SET PASSENGER ID AS INDEX COLUMN
dt.set_index("PassengerId", inplace=True)
print(dt.head())
```
![Screenshot 2025-03-27 152107](https://github.com/user-attachments/assets/476d4266-3b17-4a96-899c-81c2fc2b9d59)
```
dt.describe()
```
![Screenshot 2025-03-27 152157](https://github.com/user-attachments/assets/58d12c58-b855-4543-93b0-aace3e512720)

## CATEGORICAL DATA ANALYSIS:
```
# USE VALUE COUNT FUNCTION AND PERFROM CATEGORICAL ANALYSIS
categorical_columns = dt.select_dtypes(include=['object']).columns

for col in categorical_columns:
    print(f"Categorical Analysis of {col}:\n")
    print(dt[col].value_counts())
    print("-" * 50)
```
![Screenshot 2025-03-27 153110](https://github.com/user-attachments/assets/a8955591-bc33-48f7-a209-aa48c9300270)

## UNIVARIATE ANALYSIS:
```
# USE COUNTPLOT AND PERFORM UNIVARIATE ANALYSIS FOR THE "SURVIVED" COLUMN IN TITANIC DATASET
plt.figure(figsize=(6,4))
sns.countplot(x=dt["Survived"], palette="coolwarm")
plt.xlabel("Survived (0 = No, 1 = Yes)")
plt.ylabel("Count")
plt.title("Univariate Analysis of Survived Column")
plt.show()
```
![image](https://github.com/user-attachments/assets/be326da5-de11-4e5c-84d2-b5e272284c1d)

```
# IDENTIFY UNIQUE VALUES IN "PASSENGER CLASS" COLUMN
unique_values = dt["Pclass"].unique()
unique_values
```
![image](https://github.com/user-attachments/assets/91db8009-9926-4fa4-abf6-481505eeef0b)

```
# RENAMING COLUMN
dt.rename(columns = {'Sex':'Gender'}, inplace = True)
dt
```
![image](https://github.com/user-attachments/assets/43733039-cf31-439e-ad61-636ce174608b)

## BIVARIATE ANALYSIS:
```
# USE CATPLOT METHOD FOR BIVARIATE ANALYSIS
sns.catplot(x="Pclass", hue="Survived", kind="count", data=dt, palette="coolwarm")
plt.xlabel("Passenger Class")
plt.ylabel("Count")
plt.title("Bivariate Analysis: Survival Rate by Passenger Class")
plt.show()
```
![image](https://github.com/user-attachments/assets/1ca8a4d6-a0a5-4a80-a5ff-467c34aea6b9)

```
fig, ax1 = plt.subplots(figsize=(8,5))
graph = sns.countplot(x="Pclass", hue="Survived", data=dt, palette="coolwarm", ax=ax1)
graph.set_xticklabels(graph.get_xticklabels())
for p in graph.patches:
    height = p.get_height()
    graph.text(p.get_x()+p.get_width()/2, height + 20.8,height ,ha="left")
```
![image](https://github.com/user-attachments/assets/8e66f632-3c00-4b7f-b641-e31a524d369f)

```
# USE BOXPLOT METHOD TO ANALYZE AGE AND SURVIVED COLUMN
plt.figure(figsize=(8,5))
sns.boxplot(x="Survived", y="Age", data=dt, palette="coolwarm")
plt.xlabel("Survived (0 = No, 1 = Yes)")
plt.ylabel("Age")
plt.title("Boxplot of Age vs. Survived")
plt.show()
```
![image](https://github.com/user-attachments/assets/a82001b1-98e9-4d0b-9c8e-6cb326bd2e0a)

## MULTIVARIATE ANALYSIS:
```
# USE BOXPLOT METHOD AND ANALYZE THREE COLUMNS(PCLASS,AGE,GENDER)
plt.figure(figsize=(8,5))
sns.boxplot(x="Pclass", y="Age", hue="Gender", data=dt, palette="coolwarm")
plt.xlabel("Passenger Class")
plt.ylabel("Age")
plt.title("Boxplot of Age vs. Passenger Class and Gender")
plt.legend(title="Gender")
plt.show()
```
![image](https://github.com/user-attachments/assets/87faa37b-9eff-4fb1-abd7-bbf86d9c239d)

```
# USE CATPLOT METHOD AND ANALYZE THREE COLUMNS(PCLASS,SURVIVED,GENDER)
sns.catplot(x="Pclass", hue="Survived", col="Gender", kind="count", data=dt, palette="coolwarm")
plt.subplots_adjust(top=0.85)
plt.suptitle("Categorical Analysis: Survival Rate by Passenger Class and Gender")
```
![image](https://github.com/user-attachments/assets/eaf30f63-927b-4eb0-95a9-1b2ee4dd99b8)

```
# IMPLEMENT HEATMAP AND PAIRPLOT FOR THE DATASET
df_numeric = dt.select_dtypes(include=["number"])  # Select only numerical columns
plt.figure(figsize=(10,6))
sns.heatmap(df_numeric.corr(), annot=True, cmap="coolwarm", linewidths=0.5)
plt.title("Heatmap of Titanic Dataset Correlations")
plt.show()
```
![image](https://github.com/user-attachments/assets/b8423243-3036-4c13-8486-214154d03810)


# RESULT:
```
Thus, successfully performed Exploratory Data Analysis on the given data set.
```
