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

- **Performance Score across the Company**
![](https://github.com/AnnaYuKozak/data-projects/blob/main/SQL_Projects/Employee_Productivity_Analysis/performers_count.png)

- **Performance Score across Departments**
![](https://github.com/AnnaYuKozak/data-projects/blob/main/SQL_Projects/Employee_Productivity_Analysis/department.png)

- **Performance Score across Job Titles**
![](https://github.com/AnnaYuKozak/data-projects/blob/main/SQL_Projects/Employee_Productivity_Analysis/job%20title.png)
 

### Insights & Implications
- The number of workers with the worst performance score is the highest, while the group with best performers has the lowest count.
- Engineering department has the highest average productivity score, while Marketing takes the last place.
- Workers with title `Specialist` show the highest average productivity score, while `Developers` have the lowest average productivity.
- **Implications:** These findings suggest that the company has a broad base of lower performing employees. It might be beneficial to address this imbalance by creating development programs for underperformers and strategies for achieving higher productivity levels. In addition, the company would benefit by identifying reasons for high productivity in `Engineering` department and `Specialists`, while also exploring and addressing challenges that `Developers` and `Marketing` department workers are facing, potentially these could be role ambiguity or challenges in goal-setting.

### 2. Influence of Work Hours on Productivity
1. Objective: Explore how different work hours affect the performance score.
2. Methodology:
-  Categorization of the `Work_Hours_Per_Week` column was created using `CASE WHEN` function: `Part-Time`: Less than 38 hours per week. `Normal`: Between 38 and 40 hours per week. `Overtime`: More than 40 hours per week.
-  Used the `AVG` function to calculate the average `Performance Score` (for productivity) and the average `Employee Satisfaction Score` for each work hours category; as well as `GROUP BY`,`ORDER BY`, and `DESC`.
-   **SQL Query:** `SELECT 
    CASE 
        WHEN Work_Hours_Per_Week < 38 THEN 'Part-Time'
        WHEN Work_Hours_Per_Week BETWEEN 38 AND 40 THEN 'Normal'
        WHEN Work_Hours_Per_Week > 40 THEN 'Overtime'
    END AS work_hours_category,
    AVG(Performance_Score) AS avg_productivity,
    AVG(Employee_Satisfaction_Score) AS avg_satisfaction
FROM 
    Employees
GROUP BY 
    work_hours_category
ORDER BY 
    avg_productivity DESC;
`. **Expected Outcome:** It was anticipated that the `Normal` group would show the highest average productivity and satisfaction levels.

3. Results:
   After executing the SQL query, the following results were obtained:

- **Performance and Satisfaction Scores across Work_Hour Groups**
![](https://github.com/AnnaYuKozak/data-projects/blob/main/SQL_Projects/Employee_Productivity_Analysis/workhours_prod_satis.png)

### Insights & Implications
- `Part-Time` workers have the higest average productivity score, while also being the group who takes the second place in average satisfaction score results.
- Workers with `Normal` hours are the second with an average productivity score while they have the highest satisfaction score.
- Employees who work `Overtime` have the lowest average productivity **and** satisfaction levels.
- **Implications:** These findings suggest that working excessive hours may cause burnout which negatively impacts employee's performance. It is recommended to assess workloads in order to reduce the need for overtime, while implementing regular surveys to check well-being and understand workers' needs. In addition, since `Part-Time` group are the most efficient, their productivity can be utilized in critical tasks. 

### 3. Salary and promotion as motivators
1. Objective: Explore whether salary and promotion boost worker's performance.
2. Methodology:
-  Categorizations of the `Monthly_Salary` and 'Promotion' columns were created using `CASE WHEN` function.
-  Used the `AVG` function to calculate the average `Performance Score` (for productivity) and the average `Employee Satisfaction Score` for each work hours category; as well as `GROUP BY`,`ORDER BY`, and `DESC`. **SQL Query for *Monthly Salary*:** `SELECT 
    CASE 
        WHEN Monthly_Salary BETWEEN 3850 AND 5800 THEN 'Low'
        WHEN Monthly_Salary BETWEEN 5801 AND 7400 THEN 'Moderate'
        WHEN Monthly_Salary BETWEEN 7401 AND 9000 THEN 'High'
    END AS salary_category,
    AVG(Performance_Score) AS avg_productivity,
    AVG(Employee_Satisfaction_Score) AS avg_satisfaction
FROM 
    Employees
GROUP BY 
    salary_category;`. **SQL Query for *Promotions*:** `SELECT 
    CASE 
        WHEN Promotions = 0 THEN 'No Promotions'
        WHEN Promotions = 1 THEN 'One Promotion'
        WHEN Promotions = 2 THEN 'Two Promotions'
    END AS promotion_level,
    AVG(Performance_Score) AS avg_productivity,
    AVG(Employee_Satisfaction_Score) AS avg_satisfaction
FROM 
    Employees
GROUP BY 
    promotion_level
ORDER BY  
    avg_productivity DESC,
    promotion_level;`. **Expected Outcome:** It was anticipated that employees with higher salaries and at least one promotion during their tenure would exhibit higher productivity and satisfaction levels.

3. Results:
   After executing the SQL query, the following results were obtained:

- **Performance and Satisfaction Scores across Salary categories**
![](https://github.com/AnnaYuKozak/data-projects/blob/main/SQL_Projects/Employee_Productivity_Analysis/Salary.png)

- **Performance and Satisfaction Scores across Promotion levels**
![](https://github.com/AnnaYuKozak/data-projects/blob/main/SQL_Projects/Employee_Productivity_Analysis/Promotion.png)

### Insights & Implications
- High earners are the most satisfied and productive workers, compared to other two categories. As expected, group with Low income were the least productive and satisfied with their job, which implies that salary might indeed be an important factor. Additionally, those with no promotions are the most productive workers, which can signify that the strive for a promotion might also be of importance. It is recommended for the company to provide a clear promotion pathways and employee recognition as ways to enchance productivity levels. 

### 4. Educational Background
1. Objective: Explore whether there is a correlation between employees' educational background and their productivity and satisfaction levels.
2. Methodology:
-  Used the `AVG` function to calculate the average `Performance Score` (for productivity) and the average `Employee Satisfaction Score` for each work hours category; as well as `GROUP BY`,`ORDER BY`, and `DESC`.
-  Used the COUNT function with CASE WHEN to determine the number of best performers (Performance_Score = 5) and worst performers (Performance_Score = 1) across different education levels.
-   **SQL Query for *Performer Counts*:** `SELECT 
    Education_Level, 
    COUNT(CASE WHEN Performance_Score = 5 THEN 1 END) AS best_performers, 
    COUNT(CASE WHEN Performance_Score = 1 THEN 1 END) AS worst_performers 
FROM 
    Employees 
GROUP BY 
    Education_Level 
ORDER BY 
    best_performers DESC, 
    worst_performers DESC;`. **SQL Query for *Average Productivity and Satisfaction*:** `SELECT 
    Education_Level,
    AVG(Employee_Satisfaction_Score) AS avg_satisfaction,
    AVG(Performance_Score) AS avg_productivity
FROM 
    Employees
GROUP BY 
    Education_Level
ORDER BY 
    avg_productivity DESC;`. **Expected Outcome:** It was anticipated that employees with higher education levels (Master's and PhD degrees) would exhibit higher productivity and satisfaction levels due to advanced skills and knowledge.

3. Results:
   After executing the SQL query, the following results were obtained:

- **Performer Counts across Educational Levels**
![]()

- **Performance and Satisfaction Scores across Educational Levels**
![]()

### Insights & Implications
- The analysis showed no clear correlation between education level and the number of best or worst performers. For instance: Bachelor's Degree Holders: Best Performers: 9,894 and Worst Performers: 10,127. Similar patterns were observed for High School, Master's, and PhD graduates.
- Master's Degree holders and High School graduates have the highest average productivity scores, while the second enjoy their jobs the most, with the highest average satisfaction score. Bachelor's Degree holders have the lowest average productivity score, but PhD holders are the least satisfied.
- **Implications:** These findings suggest that PhD holders may feel misaligned in their current job roles, which can be solved by ensuring that their job responsibilities match their expertise and are challenging. Bachelor holders potentially need more training and mentorship to enhance their performance scores. High School graduates demonstrate high satisfaction and solid productivity, implying that they might benefit from practical work environments. Addionally, Master's degree holders should continue tackling challenging projects and advance further to retain their high performance score. 

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
