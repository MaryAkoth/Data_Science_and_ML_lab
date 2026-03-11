#README – Week 4 Day 1
#Week 4 Day 1: Data Cleaning and Exploratory Data Analysis (EDA)
#Overview
This notebook focuses on data exploration, cleaning, and feature engineering using Python. The dataset was loaded and examined to understand its structure, followed by cleaning procedures such as handling duplicates and missing values. Exploratory Data Analysis (EDA) techniques were also applied to understand data distributions and relationships.

#Libraries Used
The following Python libraries were used in this project:

import pandas as pd
import matplotlib.pyplot as plt
import numpy as np
import warnings
warnings.filterwarnings("ignore")
These libraries were used for:

Pandas → data manipulation and analysis

Matplotlib → data visualization

NumPy → numerical operations

Dataset Loading
The dataset was imported using Pandas.

df = pd.read_csv("/content/cliff.csv")
To preview the dataset:

df.head(5)
df.tail(5)
These commands help display the first and last rows of the dataset.

Dataset Exploration
Understanding the dataset structure is an important step before performing analysis.

Dataset Information
df.info()
This shows:

number of rows and columns

data types of each column

number of non-null values

Dataset Shape
df.shape
This returns the number of rows and columns in the dataset.

Descriptive Statistics
df.describe()
This provides statistical summaries such as:

mean

standard deviation

minimum and maximum values

quartiles

Distribution of Data
Histograms were used to visualize the distribution of numerical variables.

Age Distribution
plt.hist(df['Age'], bins=10, color="purple", edgecolor="black")
plt.title("Distribution of Age")
plt.xlabel("Age")
plt.ylabel("Frequency")
Height Distribution
plt.hist(df['Height'], bins=10, color="orange", edgecolor="black")
plt.title("Distribution of Height")
plt.xlabel("Height")
plt.ylabel("Frequency")
Season Distribution
plt.hist(df['Season'], bins=10, color="orange", edgecolor="black")
plt.title("Distribution of Season")
plt.xlabel("Season")
plt.ylabel("Frequency")
These histograms help visualize how the data is distributed.

#Data Cleaning
Data cleaning ensures the dataset is ready for analysis.

Checking for Duplicates
df[df.duplicated]
To confirm duplicates:

df[df["ID"] == 2449]
Removing Duplicates
df_new = df.drop_duplicates()
df_new.shape
Check again:

df_new[df_new.duplicated]
Handling Missing Values
Checking for Null Values
df_new.isnull()
Filling Missing Medal Values
df_new["Medal"] = df_new["Medal"].fillna("no_medal")
Handling Missing Age Values
Age column was converted to numeric format.

df_new['Age'] = df_new['Age'].astype('float64')
Median age was calculated and used to fill missing values.

median_age = df_new['Age'].median()
df_new['Age'] = df_new['Age'].fillna(median_age)
Handling Missing Height and Weight
Missing values were replaced using the mean.

mean_height = df_new['Height'].mean()
df_new['Height'] = df_new['Height'].fillna(mean_height)
mean_weight = df_new['Weight'].mean()
df_new['Weight'] = df_new['Weight'].fillna(median_age)
Data Type Conversion
Columns were converted to appropriate data types.

df_new['Sex'] = df_new['Sex'].astype('category')
df_new['Age'] = df_new['Age'].astype('int')
df_new['Team'] = df_new['Team'].astype('category')
df_new['Medal'] = df_new['Medal'].astype('category')
df_new['NOC'] = df_new['NOC'].astype('category')
Check data types:

df_new.dtypes
Exploratory Data Analysis (EDA)
Feature Engineering (BMI Calculation)
Height was converted from cm to meters.

df_new["Height"] = df_new["Height"] / 100
BMI was calculated using the formula:

df_new["BMI"] = df_new["Weight"] / df_new["Height"] ** 2
Group Analysis
The relationship between Sex and Medal distribution was analyzed.

df_new.groupby(df_new["Sex"])["Medal"].value_counts().to_frame()

#Conclusion
This notebook demonstrates key steps in data preprocessing and exploratory data analysis, including:

dataset exploration

distribution visualization

duplicate removal

missing value handling

feature engineering (BMI calculation)

grouped analysis

These steps are essential for preparing datasets before performing advanced analysis or machine learning.

