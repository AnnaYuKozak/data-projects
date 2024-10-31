# Employee Productivity Analysis: What drives workers to perform better at work?
## Purpose and Objective of the Project
The purpose of this project is to explore the relationships between employee's performance and different work-related metrics to identify any patterns or correlations. This analysis seeks to answer the following questions:

1. Top Performers across the Company: Does performance score differ among departments? Who are the best performers? How does company seem to be doing in general?

2. Influence of Work Hours on Productivity: Does working different hours affect worker's performance score? 

3. Salary and promotion as motivators : Do promotion and high salary boost worker's productivity?

4. Educational Background: Is there a correlation between productivity and education level?

5. Tenure: Does workers' performance level raise the longer they stay in the company?

6. Remote Work: What is the perfect balance between remote and on-site work?

7. Training Hours: Is training a factor for a better productivity level?

## Dataset Description
### Source: [👩🏽‍💻 Employee Performance and Productivity Data](https://www.kaggle.com/datasets/mexwell/employee-performance-and-productivity-data)
### About the Dataset:
This dataset contains **100,000** rows of data capturing key aspects of employee performance, productivity, and demographics in a corporate environment. 

- `Employee_ID`: Unique identifier for each employee.
- `Department`: The department in which the employee works (e.g., Sales, HR, IT).
- `Gender`: Gender of the employee (Male, Female, Other).
- `Age`: Employee's age (between 22 and 60).
- `Job_Title`: The role held by the employee (e.g., Manager, Analyst, Developer).
- `Hire_Date`: The date the employee was hired.
- `Years_At_Company`: The number of years the employee has been working for the company.
- `Education_Level`: Highest educational qualification (High School, Bachelor, Master, PhD).
- `Performance_Score`: Employee's performance rating (1 to 5 scale).
- `Monthly_Salary`: The employee's monthly salary in USD, correlated with job title and performance score.
- `Work_Hours_Per_Week`: Number of hours worked per week.
- `Projects_Handled`: Total number of projects handled by the employee.
- `Overtime_Hours`: Total overtime hours worked in the last year.
- `Sick_Days`: Number of sick days taken by the employee.
- `Remote_Work_Frequency`: Percentage of time worked remotely (0%, 25%, 50%, 75%, 100%).
- `Team_Size`: Number of people in the employee's team.
- `Training_Hours`: Number of hours spent in training.
- `Promotions`: Number of promotions received during their tenure.
- `Employee_Satisfaction_Score`: Employee satisfaction rating (1.0 to 5.0 scale).
- `Resigned`: Boolean value indicating if the employee has resigned.

## Data Cleaning & Preparation
**Boolean Standardization**: To facilitate analysis, boolean values in the column `Resigned` were standardized from `TRUE/FALSE` to `1/0`.

## Analysis Methodology
### 1. Top Performers across the Company
1. Objective: Explore performance score across the company, different departments and job titles. *In this analysis, the `Performance_Score` is used as a proxy for employee productivity, with higher scores indicating higher productivity levels.*
2. Methodology:
- to find out the number of workers with varying scores `SUM` function was used. The query calculated the number of employees for each performance score. **SQL Query**: `SELECT 
    SUM(Performance_Score = 5) AS best_performers,
    SUM(Performance_Score = 4) AS top_performers,
    SUM(Performance_Score = 3) AS mid_performers,
    SUM(Performance_Score = 2) AS low_performers,
    SUM(Performance_Score = 1) AS worst_performers
FROM 
    Employees;`. **Expected Outcome:** It was anticipated that `mid_performance` group would contain the highest number of workers.
-  to explore productivity across departments and job titles functions `AVG`(for calculating the average productivity), `GROUP BY`, `ORDER BY`, `DESC` were used. **SQL Query for *Departments*:** `SELECT Department, AVG(Performance_Score) as avg_productivity from Employees
GROUP BY Department
ORDER BY avg_productivity DESC;`. **SQL Query for *Job Titles*:** `SELECT Job_Title, AVG(Performance_Score) as avg_productivity from Employees 
GROUP BY Job_Title 
ORDER BY avg_productivity DESC;`. **Expected Outcome:** It was anticipated that there might be a difference in productivity levels across specific departments and job functions.
3. Results:
   After executing the SQL query, the following results were obtained:


### Insights & Implications
- The number of workers with the worst performance score is the highest, while the group with best performers has the lowest count.
- Engineering department has the highest average productivity score, while Marketing takes the last place.
- Workers with title `Specialist` show the highest average productivity score, while `Developers` have the lowest average productivity.
- **Implications:** These findings suggest that the company has a broad base of lower performing employees. It might be beneficial to address this imbalance by creating development programs for underperformers and strategies for achieving higher productivity levels. In addition, the company would benefit by identifying reasons for high productivity in `Engineering` department and `Specialists`, while also exploring and addressing challenges that `Developers` and `Marketing` department workers are facing, potentially these could be role ambiguity or challenges in goal-setting.

### 2. Influence of Work Hours on Productivity
1. Objective: ...
2. Methodology:
-  to explore ... `FUNCTIONS` were used. **SQL Query for *...*:** `...`. **SQL Query for *...*:** `...`. **Expected Outcome:** It was anticipated that ...
### Insights & Implications
- ...
- ...
- ...
- **Implications:** These findings suggest ...

### 3. Salary and promotion as motivators
1. Objective: ...
2. Methodology:
-  to explore ... `FUNCTIONS` were used. **SQL Query for *...*:** `...`. **SQL Query for *...*:** `...`. **Expected Outcome:** It was anticipated that ...
### Insights & Implications
- ...
- ...
- ...
- **Implications:** These findings suggest ...

### 4. Educational Background
1. Objective: ...
2. Methodology:
-  to explore ... `FUNCTIONS` were used. **SQL Query for *...*:** `...`. **SQL Query for *...*:** `...`. **Expected Outcome:** It was anticipated that ...
### Insights & Implications
- ...
- ...
- ...
- **Implications:** These findings suggest ...

### 5. Tenure
1. Objective: ...
2. Methodology:
-  to explore ... `FUNCTIONS` were used. **SQL Query for *...*:** `...`. **SQL Query for *...*:** `...`. **Expected Outcome:** It was anticipated that ...
### Insights & Implications
- ...
- ...
- ...
- **Implications:** These findings suggest ...

### 6. Remote Work
1. Objective: ...
2. Methodology:
-  to explore ... `FUNCTIONS` were used. **SQL Query for *...*:** `...`. **SQL Query for *...*:** `...`. **Expected Outcome:** It was anticipated that ...
### Insights & Implications
- ...
- ...
- ...
- **Implications:** These findings suggest ...

### 7. Training Hours
1. Objective: ...
2. Methodology:
-  to explore ... `FUNCTIONS` were used. **SQL Query for *...*:** `...`. **SQL Query for *...*:** `...`. **Expected Outcome:** It was anticipated that ...
### Insights & Implications
- ...
- ...
- ...
- **Implications:** These findings suggest ...

# Conclusions
