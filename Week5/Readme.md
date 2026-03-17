GitHub README
## Titanic Dataset Analysis – Data Cleaning and Visualization
# Lab Title
Exploratory Data Analysis and Visualization of the Titanic Dataset

# Objective
The objective of this lab was to perform Exploratory Data Analysis (EDA) on the Titanic dataset to understand passenger characteristics, handle missing data, and visualize survival patterns.

Through this lab, I practiced data cleaning, statistical analysis, and data visualization using Python.

# Tools Used
Python

Pandas

NumPy

Seaborn

Matplotlib

Jupyter Notebook

# Dataset
The dataset used is the Titanic passenger dataset, which contains information about passengers such as:

Passenger class

Age

Gender

Ticket fare

Cabin

Embarkation port

Survival status

The dataset was loaded directly from an online source.

url = "https://raw.githubusercontent.com/datasciencedojo/datasets/master/titanic.csv"
titanic = pd.read_csv(url)
Step 1: Data Exploration
To understand the dataset structure, the first few rows were displayed.

titanic.head()
Dataset information was then examined.

titanic.info()
This step helped identify:

Data types

Missing values

Number of observations

Summary statistics were also generated.

titanic.describe()
This provided information such as:

Mean

Standard deviation

Minimum and maximum values

Step 2: Handling Missing Values
Missing values were identified using:

titanic.isnull().sum()
A heatmap visualization was also used to observe missing data patterns.

sns.heatmap(titanic.isnull(), cbar=False)
Data Cleaning Steps
Missing values were handled as follows:

Fill missing Age values using the median:

titanic['Age'].fillna(titanic['Age'].median(), inplace=True)
Fill missing Embarked values using the most frequent value:

titanic['Embarked'].fillna(titanic['Embarked'].mode()[0], inplace=True)
Drop the Cabin column due to excessive missing values:

titanic.drop(columns='Cabin', inplace=True)
Step 3: Data Visualization
Several visualizations were created to understand survival patterns and passenger distribution.

Survival Count Plot
sns.countplot(x='Survived', data=titanic)
This chart shows the number of passengers who survived versus those who did not.

Passenger Class Distribution
Visualization was used to understand how passengers were distributed across different ticket classes.

Age Distribution
Histograms were used to examine the distribution of passenger ages.

Correlation Analysis
Correlation between numerical features was explored to identify relationships between variables.

Key Observations
Many passengers had missing Age values which were filled using the median.

The Cabin column contained too many missing values and was removed.

Survival patterns varied depending on passenger characteristics.

Data visualization helped reveal patterns that are difficult to see in raw tables.

Lessons Learned
Through this lab, I gained practical experience in:

Data loading and inspection

Handling missing values

Data cleaning

Exploratory Data Analysis (EDA)

Creating meaningful visualizations

These skills are essential for preparing data before building machine learning models.



Copied from: Assignment Instructions Guide - <https://chatgpt.com/c/699767c4-cac0-8333-81d5-b36d59e00653>
