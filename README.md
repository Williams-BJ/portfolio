# Data Science Salaries Analysis

## Table of Contents
1. [Project Overview](#project-overview)
2. [Data Source](#data-source)
3. [Tools](tools)
4. [Data Cleaning/Preparation](data-cleaning/preparation)
5. [Exploratory Data Analysis](exploratory-data-analysis)
6. [Data Analysis](data-analysis)

### Project Overview

This exploration of the Data Science Salaries Dataset examines salary trends in the field of data science. It highlights variations across job titles, locations, and experience levels, offering insights into compensation patterns. The analysis aims to inform professionals, employers, and researchers by uncovering key factors that influence data science salaries.

### Data Source

Data Science Salaries: The primary dataset used for this analysis is "DataScience_salaries_2024.csv" file.

### Tools

  1. Excel - Data Cleaning
  2. Jupyter Notebooks - Data Exploration Analysis


  ### Data Cleaning/Preparation 

  I performed the following tasks:
  1. Data Inspection
  2. Finding Missing Values
  3. Data Cleaning

### Exploratory Data Analysis


### Data Analysis

Include some intresting code I worked with

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# Load the dataset
file_path = "datascience_jobs.csv"  # Update with your dataset file path
data = pd.read_csv(file_path)

# Display the first few rows of the dataset
print(data.head())

# Display dataset information
print(data.info())

# Show basic statistics
print(data.describe())

# Check for missing values
print(data.isnull().sum())

# Summary statistics for salary
print(data[['salary', 'salary_in_usd']].describe())



plt.figure(figsize=(10, 6))
sns.histplot(data['salary_in_usd'], kde=True, color='blue')
plt.title('Distribution of Salary in USD')
plt.xlabel('Salary in USD')
plt.ylabel('Frequency')
plt.show()

# Count job titles
job_title_counts = data['job_title'].value_counts()
print(job_title_counts)

# Plot job title distribution
plt.figure(figsize=(12, 6))
sns.countplot(data=data, y='job_title', order=job_title_counts.index[:10], palette='viridis')
plt.title('Top 10 Job Titles')
plt.xlabel('Count')
plt.ylabel('Job Title')
plt.show()

# Experience level counts
experience_counts = data['experience_level'].value_counts()
print(experience_counts)

# Plot experience level distribution
plt.figure(figsize=(8, 6))
sns.countplot(data=data, x='experience_level', order=experience_counts.index, palette='magma')
plt.title('Distribution of Experience Levels')
plt.xlabel('Experience Level')
plt.ylabel('Count')
plt.show()


# Remote ratio distribution
remote_counts = data['remote_ratio'].value_counts()
print(remote_counts)

# Plot remote ratio
plt.figure(figsize=(8, 6))
sns.countplot(data=data, x='remote_ratio', order=remote_counts.index, palette='coolwarm')
plt.title('Distribution of Remote Ratio')
plt.xlabel('Remote Ratio')
plt.ylabel('Count')
plt.show()

plt.figure(figsize=(10, 6))
sns.boxplot(data=data, x='remote_ratio', y='salary_in_usd', palette='Set2')
plt.title('Salary in USD by Remote Ratio')
plt.xlabel('Remote Ratio')
plt.ylabel('Salary in USD')
plt.show()

# Count employees by residence
residence_counts = data['employee_residence'].value_counts()

# Top 10 locations
plt.figure(figsize=(12, 6))
sns.barplot(y=residence_counts.index[:10], x=residence_counts.values[:10], palette='viridis')
plt.title('Top 10 Employee Residences')
plt.xlabel('Number of Employees')
plt.ylabel('Employee Residence')
plt.show()

# Boxplot of salaries by company location
plt.figure(figsize=(12, 6))
sns.boxplot(data=data, x='company_location', y='salary_in_usd', palette='cool')
plt.title('Salary in USD by Company Location')
plt.xticks(rotation=45)
plt.xlabel('Company Location')
plt.ylabel('Salary in USD')
plt.show()

# Average salary per year
yearly_salary = data.groupby('work_year')['salary_in_usd'].mean().reset_index()

plt.figure(figsize=(10, 6))
sns.lineplot(data=yearly_salary, x='work_year', y='salary_in_usd', marker='o', color='green')
plt.title('Average Salary in USD by Work Year')
plt.xlabel('Year')
plt.ylabel('Average Salary in USD')
plt.show()

plt.figure(figsize=(8, 6))
sns.boxplot(data=data, x='experience_level', y='salary_in_usd', palette='pastel')
plt.title('Salary in USD by Experience Level')
plt.xlabel('Experience Level')
plt.ylabel('Salary in USD')
plt.show()


plt.figure(figsize=(8, 6))
sns.boxplot(data=data, x='employment_type', y='salary_in_usd', palette='Set3')
plt.title('Salary in USD by Employment Type')
plt.xlabel('Employment Type')
plt.ylabel('Salary in USD')
plt.show()

# Correlation matrix for numerical features
correlation_matrix = data[['salary', 'salary_in_usd', 'remote_ratio']].corr()

plt.figure(figsize=(8, 6))
sns.heatmap(correlation_matrix, annot=True, cmap='coolwarm', fmt='.2f')
plt.title('Correlation Heatmap')
plt.show()
```





