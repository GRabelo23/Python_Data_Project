# The Analysis

##  1. What are the most demanded for the top 3 most popular data roles?

To find the most demanded skills for the top 3 most puopular data roles, I filtered out those positions by which ones were the most popular, and got top 5 skills for these top 3 roles. This query highlights the most popular job titles and their top skills, showing which skills I should pay attention to depending on the my target role.

View my notebook whit detailed steps there:
[2_Skill_Demand.ipynb](2_Skills_Demand.ipynb)

### Visualize Data

```python

fig, ax = plt.subplots(len(job_titles),1)

for i, job_title in enumerate(job_titles):
    df_plot = df_skills_perc[df_skills_perc['job_title_short'] == job_title].head(5)
    sns.barplot(data=df_plot, x='skill_perc', y='job_skills', ax=ax[i], hue='skill_perc', palette='dark:b_r')

plt.show()
```

### Results 

![Visualization of Top Skills for Data Jobs](Images/skill_demang.png)

### Insights:

- Python is a versatile skill, highly demanded across all three roles, but most prominently for Data Scientists (72%) and Data Engineers(65%). 
- SQL is the most required skill for Data Analysts and Data Engineers, with in over half of the job postings for both roles. 
- Data Engineers require more specialized technical skills (AWS, Azure, Spark) compared to Data Analysts and Data Scientists who are expected to be proficient in more general data management and  analysis tools (Excel, Tableau).

## 2. How are in-demand skills trending for Data Analysts?

To find how skills are trending in 2023 for Data Analysts, I filtered data analyst positions and grouped the skills by the month of the job postings. This got me the top 5 skills of data analysts by month, showing how popular skills were throughout 2023.

View my notebook with detailed steps here: [3_Skills_Trend](3_Skills_Trend.ipynb).

```python 

from matplotlib.ticker import PercentFormatter

df_plot = df_DA_US_perc.iloc[:, :5]
sns.lineplot(data=df_plot, dashes=False, palette='tab10')
plt.gca().yaxis.set_major_formatter(PercentFormatter(decimals=0))

plt.show()

```

### Results

![Trending Skills for Data Analysts in the US](Images/trending_skills.png)

### Insights:

- SQL remains the most consistently demand skill throughout the year, although it shows a gradual decrease in demand. 
- Both Python and Tableau show relatively stable demand throughout the year with some fluctuations but remain essential skills for Data Analysts.
