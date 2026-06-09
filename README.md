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


##  2.How are in - demand skills trending for Data Analysts ?

``` python 
import matplotlib.pyplot as plt
import seaborn as sns

sns.set_theme(style="whitegrid")

# Remove Total row
df_clean = df_DA_US_percent.drop(index='Total', errors='ignore')

skills = ['sql', 'excel', 'tableau', 'python', 'power bi']

plt.figure(figsize=(11, 6))

for skill in skills:
    plt.plot(
        df_clean.index,
        df_clean[skill],
        linewidth=2.5,
        marker='o',
        label=skill
    )

plt.title('Trending Skills for Data Analysts in US', fontsize=16, fontweight='bold')
plt.xlabel('Job Posted Month')
plt.ylabel('Likelihood in Job Posting (%)')

plt.legend(title='Job Skills')

sns.despine()
plt.tight_layout()
plt.show()

```
### Result 

![Trending Skills for Data Analysts in US][def]

### Insights
## 📈 Key Insights: Trending Skills for Data Analysts (US)

* **SQL is the Dominant Requirement**: SQL consistently ranks as the most in-demand skill, maintaining a presence in over **55% to 62%** of job postings throughout the entire year.
* **Excel Experienced Volatility**: Excel demand fluctuated significantly, peaking in **August at over 45%** before dropping sharply to its lowest level of the year in **October (~34%)**.
* **Tableau and Python Neck-and-Neck**: Tableau and Python closely track each other all year, staying within the **27% to 35%** demand range. Python briefly overtook Tableau in **June and December**.
* **Power BI Tracks at the Bottom**: Power BI remains the least demanded tool among the five, staying flat and never breaking past **25%** likelihood in postings.
* **Year-End Q4 Dip & Recovery**: Most skills saw a noticeable dip in demand between **September and November**, followed by a sharp recovery in **December** (especially for Excel and Python).




## 3. How well do jobs and skill pay for data Analysts ?


### salary Analysis for data Nerd 

``` python 

sns.boxplot(data=df_US_top6, x='salary_year_avg', y='job_title_short',order = job_order)

sns.set_theme(style='ticks')


plt.title('Salary Distributions in the United States')
plt.xlabel('Yearly Salary (USD)')
plt.ylabel("")

plt.xlim(0, 600000)

ticks_x = plt.FuncFormatter(lambda y, pos: f'${int(y/1000)}K')
plt.gca().xaxis.set_major_formatter(ticks_x)

plt.show()

```

### Result 


![Salary Analysis for Data Nerds](https://raw.githubusercontent.com/VIHAN2025/us-data-roles-analysis/main/salary%20Analysis%20for%20Data%20Nerds.png)

#### Insights 

## 📊 Key Insights: US Data Salary Distribution

An analysis of the box plot reveals several critical trends regarding compensation across data professions in the United States:

### 📈 1. Seniority and Role Hierarchy
* **Top Earners:** Senior Data Scientists and Senior Data Engineers command the highest compensation.
* **Median Benchmark:** Both senior technical roles share a median salary sitting between **$150K and $175K**.
* **The Analyst Gap:** Data Analysts sit at the lowest tier, with a median salary slightly below **$100K**.

### 🚀 2. Career Progression Impact
* **Analyst Growth:** Transitioning from junior to Senior Data Analyst yields a modest median bump to around **$110K–$120K**.
* **The Tech Leap:** Moving from Senior Data Analyst to a standard Data Scientist/Engineer role offers a much larger financial leap than internal analyst promotion.

### 🎯 3. Extreme Outliers & Earning Potential
* **High Caps:** Every single role displays significant high-end outliers well past the upper whiskers.
* **Peak Salaries:** Data Scientist and Data Engineer positions feature the most extreme outliers, with top individual earners reaching between **$500K and $600K**.
* **Market Premium:** The high volume of outliers in Data Science indicates a massive premium for specialized skill sets or specific high-paying industries (e.g., Big Tech, FinTech).

### 🔍 4. Data Spread & Variance
* **Science vs. Analytics:** Data Scientist roles exhibit a wider overall distribution (IQR) and more volatile high-end variance compared to more tightly bounded Analyst roles.


[def]: https://raw.githubusercontent.com/VIHAN2025/us-data-roles-analysis/main/Trending%20Skills%20for%20Data%20Analysts%20in%20US.png



## 4. What is the most optimal skill to learn for 

#### Insights 
## Key Insights from the Skills Analysis

The scatter plot below explores the trade-off between **Market Demand (Job Postings)** and **Financial Value (Median Annual Salary)** for top Data Analyst skills in the United States.

### 1. High Demand, Moderate Pay (The Industry Baselines)
* **SQL & Excel**: These represent the foundation of data analytics. **SQL** dominates the chart with the highest demand (>2,500 postings) but settles at a mature median salary of ~$91K.


### 2. Niche Mastery (High Pay, Low Volume)
* **Oracle & SQL Server**: These specialized database management skills feature lower job posting frequencies (<500 postings) but command strong premium salaries. **Oracle** spikes near the absolute top of the salary bracket at ~$97K, showing that enterprise-specific mastery is highly rewarded despite fewer raw openings.

### 3. Oversaturated / Support Skills
* **Word & PowerPoint**: These general business tools populate the bottom-left quadrant. They offer significantly lower specialized economic value (~$81K–$85K) and low standalone job posting counts, signaling they serve strictly as baseline corporate expectations rather than core data skill drivers.


#### Result 
![Most Optimal Skills for Data Analysis in the US](https://raw.githubusercontent.com/VIHAN2025/us-data-roles-analysis/main/Most%20Optimal%20Skills%20for%20Data%20Analysis%20%20in%20the%20Us.png)
