# The analysis 

## 1. what are the most demand skills for  the top 3 popular data roles ?
Most In-Demand Skills for Top Data Roles

In this analysis, I identified the most in-demand skills for the top 3 most popular data job roles. First, I filtered the dataset to focus on the most frequently posted positions. Then, for each of the top 3 roles, I extracted the top 5 most required skills.

This analysis highlights the most popular job titles in the data field and the key skills associated with them. It helps clarify which skills are most valuable depending on the specific role being targeted, allowing job seekers to better focus their learning and preparation.

View my notebook with detailed step here : 
[PROJECT_1.ipynb](https://github.com/VIHAN2025/us-data-roles-analysis)


### Visualization data 
``` python 
fig, ax = plt.subplots(
    len(job_titles),
    1,
    figsize=(10, len(job_titles) * 4),  # More vertical space
    squeeze=False
)

# Professional color palette
colors = ['#08306B', '#2171B5', '#6BAED6']

for i, title in enumerate(job_titles):

    df_plot = df_skills_perc[
        df_skills_perc['job_title_short'] == title
    ].head(5)

    df_plot.plot(
        kind='barh',
        x='job_skills',
        y='skill_percent',
        ax=ax[i, 0],
        color=colors[i % len(colors)],  # Cycles through colors
        legend=False
    )


plt.show()
```
### Resultls
![Visualization of the Top Skills for Data Nerds](https://raw.githubusercontent.com/VIHAN2025/us-data-roles-analysis/main/Visualisation%20of%20the%20top%20Skill%20for%20Data%20Nerds.png)

### insights 

US Data Job Skill DemandsSQL is Essential: It is a top-two requirement across all roles, peaking at 68% for Data Engineers.Python Rules Programming: It dominates Data Science (72%) and Data Engineering (64%), far outperforming R (44%).Data Analysts Need Foundational Tools: SQL (50%) and Excel (40%) are the primary requirements.Data Engineers Need Infrastructure: This is the only role requiring Cloud (AWS 42%, Azure 32%) and Big Data (Spark 32%) skills.Data Scientists Prioritize Code: Python, SQL, and R make up the core toolkit, with minor demand for legacy tools like SAS (24%)
