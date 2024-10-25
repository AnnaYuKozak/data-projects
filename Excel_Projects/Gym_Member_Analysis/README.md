# Gym Member Analysis: Exploring Metrics and Workout Habits
## Purpose and Objective of the Project:
The purpose of this project is to explore the relationships between different metrics and workout habits of gym members to identify any patterns or correlations. This analysis seeks to answer the following questions:

1. **Correlation between Fat Percentage and Workout Frequency:** Does workout frequency influence body fat percentage? Is there a correlation between how often one goes to the gym and their body fat estimate?

2. **BMI Group, Workout Type, and Session Duration:** What types of workouts do people in different BMI groups prefer, and how long do they tend to spend on each workout?

3. **Calories Burned, Workout Type, Age Group, and Gender:** Which types of workouts burn the most calories, and how are calories burned affected by age or gender?

4. **Analysis of Gender, Age Groups, and Workout Frequency:** Which demographics are the most frequent gym visitors?

5. **Water Intake, Calories Burned, Workout Type, and Gender:** Does increased water intake impact calories burned, and does workout type affect this relationship across genders?

## Dataset Description
### Dataset Source: [https://www.kaggle.com/datasets/valakhorasani/gym-members-exercise-dataset]
**About the Dataset:**
This dataset provides a detailed overview of gym members' exercise routines, physical attributes, and fitness metrics. It includes 973 entries with key performance indicators such as heart rate, calories burned, and workout duration. Demographic data and experience levels allow for a comprehensive analysis of fitness patterns, athletic progression, and health trends.

**Key Features:**

- `Age:` Age of the gym member.
- `Gender:` Gender of the gym member (Male or Female).
- `Weight (kg):` Member’s weight in kilograms.
- `Height (m):` Member’s height in meters.
- `Max_BPM:` Maximum heart rate (beats per minute) during workout sessions.
- `Avg_BPM:` Average heart rate during workout sessions.
- `Resting_BPM:` Heart rate at rest before workout.
- `Session_Duration (hours):` Duration of each workout session in hours.
- `Calories_Burned:` Total calories burned during each session.
- `Workout_Type:` Type of workout performed (e.g., Cardio, Strength, Yoga, HIIT).
- `Fat_Percentage:` Body fat percentage of the member.
- `Water_Intake (liters):` Daily water intake during workouts.
- `Workout_Frequency (days/week):` Number of workout sessions per week.
- `Experience_Level:` Level of experience, from beginner (1) to expert (3).
- `BMI:` Body Mass Index, calculated from height and weight.

**New Columns Created:**
- `Age_Group:` Age ranges for more effective grouping and comparison.
- `Water_Intake_Group:` Grouped levels of daily water intake.
- `BMI_Group:` Categorized BMI ranges for analyzing workout trends across different BMI levels.

## Analysis Methodology

### 1. Data Cleaning
To clean and standardize the dataset:

- `Column Formatting:` Formats were standardized to `Text` and `Number` for consistency.
- `Fat_Percentage Standardization:` The `Fat_Percentage` column values were divided by 100 to convert them to percentage units and formatted as `%`.
  
### 2. Data Preparation
To facilitate analysis, new columns were created:
`Age_Group`, `Water_Intake_Group`, and `BMI_Group` were generated using the `IF` formula to categorize members by age ranges, water intake levels, and BMI categories.

### 3. Data Analysis
The following key analyses were performed using `PivotTables`:

1. **Correlation between Fat Percentage and Workout Frequency:** Examining the relationship between workout frequency and body fat percentage.
2. **BMI Group, Workout Type, and Session Duration:** Analyzing workout type and session duration across different BMI groups.
3. **Calories Burned, Workout Type, Age Group, and Gender:** Exploring calorie burn by workout type, age group, and gender.
4. **Analysis of Gender, Age Groups, and Workout Frequency:** Determining which demographic groups visit the gym most frequently.
5. **Water Intake, Calories Burned, Workout Type, and Gender:** Investigating the influence of water intake on calories burned, factoring in workout type and gender.

## Insights
1. **Correlation between Fat Percentage and Workout Frequency**.

![Fat Percentage vs. Workout Frequency](https://github.com/AnnaYuKozak/data-projects/blob/main/Fat%25%26Freq.png?raw=true)

A clear correlation was found between workout frequency and body fat percentage. Members who went to the gym 4–5 days per week had an increasingly lower average body fat percentage, reaching as low as `14%`. However, no consistent trend was observed among those who worked out 2–3 days per week. This suggests that working out more than 4 days per week may help in achieving a lower body fat percentage.

2. **BMI Group, Workout Type, and Session Duration**.

![BMI Group, Workout Type, and Session Duration](https://github.com/AnnaYuKozak/data-projects/blob/main/Ses%26BMI.png?raw=true)


Analysis showed that individuals with a `Normal Weight BMI` tend to work out the longest on average and show a preference for `HIIT` workouts. Following this:

- `Overweight` members spend the most time on `Yoga`.
- `Obesity Class 1` members also prefer `HIIT` workouts.
- `Underweight` members engage most in `Cardio` workouts.
- `Obesity Class 3` members lean toward `Yoga` **and** `HIIT`.
- `Obesity Class 2` members spend the most time on `Cardio`.
These findings suggest that members with a Normal Weight BMI engage in longer sessions, averaging `1 hour and 30 minutes`. However, *no definitive trend* was identified between specific workout types and BMI categories.

3. **Calories Burned, Workout Type, Age Group, and Gender**.

![Calories Burned, Workout Type, Age Group, and Gender](https://github.com/AnnaYuKozak/data-projects/blob/main/Calories%26G.png?raw=true)


`Yoga` was found to significantly increase calories burned among `women aged 26–35`.
`HIIT` workouts were the most effective for calorie burning in `men`.
`Older women` (especially those **over 45**) gravitate toward `Strength` workouts, **while** `older men` prefer `Cardio`.
`Younger women (18–25)` tend to prefer `Cardio`, **while** `young men` of the same age group are more inclined towards `HIIT` and `Strength` workouts.

4. **Analysis of Gender, Age Groups, and Workout Frequency**.

![Gender, Age Groups, and Workout Frequency](https://github.com/AnnaYuKozak/data-projects/blob/main/G%26Freq.png?raw=true)


The top three most frequent gym-goers were:

- Women aged 26–36 (average **3.5** days per week),
- Women aged 56–65,
- Men aged 36–45.

Interestingly, `older men (56–65)` were the **least** frequent gym-goers, suggesting that gym frequency tends to be higher in certain age and gender groups.

5. **Water Intake, Calories Burned, Workout Type, and Gender**.

![Water Intake](https://github.com/AnnaYuKozak/data-projects/blob/main/Water.png?raw=true)


Remarkably, females generally did **not** drink more than 3 liters of water during workouts. The data indicates that `those who consumed 2–3 liters` burned **more** calories, regardless of workout type. A similar correlation was observed in men, *with the exception of HIIT workouts*. This suggests that `drinking 2–3 liters` of water may **enhance calorie burn** during workouts across various types.

## Conclusion
This analysis provided valuable insights into the workout habits and health metrics of gym members. 

Key findings include:
- `Workout Frequency and Fat Percentage`: Members who worked out 4–5 days per week tended to have a notably lower body fat percentage, suggesting a possible positive impact of frequent workouts on body composition.
- `BMI and Workout Type`: Normal-weight members spent more time on HIIT workouts, while those in higher BMI categories engaged more in Yoga and Cardio.
- `Calories Burned by Workout Type, Age, and Gender`: Women aged 26–35 burned more calories in Yoga, while men showed the highest calorie burn with HIIT workouts. This insight indicates how different demographics may benefit more from specific workout types.
- `Gym Attendance by Demographics`: The most frequent gym-goers were women aged 26–36 and 56–65, along with men aged 36–45, highlighting age and gender patterns in workout frequency.
- `Water Intake and Calorie Burn`: Both male and female members who consumed 2–3 liters of water during workouts tended to burn more calories, showing a potential link between hydration and energy expenditure.
