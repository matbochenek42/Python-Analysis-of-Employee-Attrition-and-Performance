# 💼 Python Analysis of Employee Attrition & Performance

## 🔎 Project Overview

This project focuses on Python analysis of employee dataset, that includes information about employee age, attrition, education and more. 

## 📂 Data Overview

### Overview

**Data source:** [Kaggle IBM HR Analytics Employee Attrition & Performance](https://www.kaggle.com/datasets/pavansubhasht/ibm-hr-analytics-attrition-dataset) 

### Data Cleaning

The dataset was directly imported from **Kaggle** and cleaned in the [1_Data_Cleaning.ipynb](1_Data_Cleaning.ipynb) file. 

## 📈 Sample Analysis 

### 1. Gender Distribution & Employees’ Marital Status

``` python
status = df["MaritalStatus"].value_counts()

sns.set_theme(style="ticks")

fig, ax = plt.subplots(1, 2)
fig.set_size_inches((10, 10))

plt.subplot(1, 2, 1)
plt.pie(gender, labels=["Male", "Female"], autopct='%1.0f%%', startangle=90)
plt.title("Gender Distribution of Employees")

plt.subplot(1, 2, 2)
plt.pie(status, labels=["Married", "Single", "Divorced"], autopct='%1.0f%%', startangle=90)
plt.title("Employees’ Marital Status")

plt.tight_layout()
plt.show()
```

**Visualization:**

![chart1](/images/chart1.png)

See more details in the [2_Exploratory_Data_Analysis.ipynb](2_Exploratory_Data_Analysis.ipynb) file.

### 2. Salary Distributions for the Most Popular Job Roles

``` python
job_roles = df["JobRole"].value_counts().head(5).index.tolist() # top 5 roles in df (indexes converted to python list)

df_top5 = df[df["JobRole"].isin(job_roles)] # filtering df for roles in job_roles list

job_order = df_top5.groupby("JobRole")["MonthlyIncome"].median().sort_values(ascending=False).index # group by median monthly income
```
``` python
# boxplotting

sns.boxplot(data=df_top5, x="MonthlyIncome", y="JobRole", order=job_order)
sns.set_theme(style='ticks')
sns.despine()

plt.title("Salary Distributions for the Most Popular Job Roles")
plt.xlabel("Median Monthly Income")
plt.ylabel("")
plt.xlim(0, 14000) # x axis values

ticks_x = plt.FuncFormatter(lambda y, pos: f"{int(y/1000)}K") # 14000 -> 14K
plt.gca().xaxis.set_major_formatter(ticks_x)
plt.show()
```

**Visualization:**

![chart2](/images/chart2.png)

See more details in the [3_Employee_Profile_Breakdown.ipynb](3_Employee_Profile_Breakdown.ipynb) file.

## 💪 What I Learned

I learned multiple Python skills, mainly Pandas and Matplotlib skills such as: accessing data, merging dataframes, creating pivot tables, aggregation, data visualization.

## 🖥️ Technical Details

- **Python Libraries:** Pandas, Matplotlib and other
- **Environment:** Visual Studio Code
- **Data source:** [Kaggle IBM HR Analytics Employee Attrition & Performance](https://www.kaggle.com/datasets/pavansubhasht/ibm-hr-analytics-attrition-dataset) 


## ✒️ Author

- **Author:** Mateusz Bochenek
- **Mail:** matbochenek42@gmail.com
- **GitHub link:** https://github.com/matbochenek42
- **LeetCode link:** https://leetcode.com/u/SmO7BWmsiz/
