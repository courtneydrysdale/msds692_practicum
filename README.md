# Colorado School District Achievement Factors
#### Courtney Drysdale
##### Regis University - MSDS 692 Practicum I Fall 2025

In this project, I looked at Colorado School District data to see which factors can be used to predict future student achievement. 
I pulled together multiple datasets from the Colorado Department of Education statistics website to combine them to get all the different 
variables in one dataset. I used data at at the district level, but this algorithm could potentially be used on similar datasets at different 
levels (state, articulation areas within a district, or by individual school). I used classification algorithms to classify a district’s likely 
achievement level (below or above average) based on the variables. 

## Research Question
Which factors can be used to determine future student achievement in Colorado school districts?

## Dataset Introduction

For this project, I started with 2024-2025 Colorado Measures of Academic Success (CMAS) scores for students that met or exceeded standards from the Colorado 
Department of Education (CDE) at the district level for all grades in two subject areas: English Language Arts and Mathematics. Each district had a
percentage score for ELA and Math, along with the district code and the district name.

With the CMAS scores, I combined 10 other spreadsheets of district level data using a pandas dataframe. The original spreadsheets are linked at the bottom
of this README, and the simplified exported csv files are available in this repository.

All data was merged on the District Code. This resulted in an initial dataset with 161 rows and 19 columns, 2025_data_cleaned.csv

### Full Feature List and Descriptions
   - District Code: A unique number to identify the school district
   - ELA: the percentage of students in the district that met or exceeded the ELA standards
   - Math: the percentage of students in the district that met or exceeded the Math standards
   - Attendance Rate: the district overall attendance rate percentage for all students
   - Truancy Rate: the district overall truancy rate percentage for all students
   - PK-12 Count: the number of total students enrolled in the district
   - Teacher FTE: the number of teachers (full time equivalent) employed by the district
   - Percent Minority: the percentage of students in a district that are a racial minority
   - Percent Female: the percentage of students in a district that are female
   - Percent Male: the percentage of students in a district that are male
   - Percent Non-Binary: the percentage of students in a district that are non-binary
   - Average Teacher Salary: the average annual salary for teachers (non-charter school) in the district
   - Percent Teacher Minority: the percentage of teachers in a district that are a racial minority
   - Staff Turnover Rate: the turnover rate for all staff employed by the district
   - Federal Funding Per Pupil: the dollar amount the federal government provides per pupil
   - State/Local Funding Per Pupil: the dollar amount the state/local government provides per pupil
   - Student Teacher Ratio: a new feature created by dividing the PK-12 Count by the Teacher FTE
   - Total Funding Per Pupil: a new feature created by adding together the federal and state/local funding

After merging all data, the dataset was cleaned and all columns were prepared for machine learning.

Since this data will be used for two different outcome variables, I create two separate Jupyter notebooks for working with the data,
one for ELA and one for Math. In each one, I created a new column for the "ELA Score" or "Math Score" which placed a 0 in the column if
the district's score was below the average and a 1 in the column if it was above average.

## Data Visualizations
I started with looking at the class distribution for both ELA scores and Math Scores by creating bar charts for both.

<IMG SRC = "https://github.com/courtneydrysdale/msds692_practicum/blob/main/Visualizations/ELA%20Scores.png" width="500"> <IMG SRC = "https://github.com/courtneydrysdale/msds692_practicum/blob/main/Visualizations/Math%20Scores.png" width="500">

I also created boxplots for some of the features for students, teachers, and financial information since they shared similar ranges.
While this did reveal some outliers, I chose not to remove them from the dataset since the number of rows is so small already.

<IMG SRC = "https://github.com/courtneydrysdale/msds692_practicum/blob/main/Visualizations/Student%20Info%20Boxplot.png" width="500"><IMG SRC = "https://github.com/courtneydrysdale/msds692_practicum/blob/main/Visualizations/Teacher%20Info%20Boxplot.png" width="500">
<IMG SRC = "https://github.com/courtneydrysdale/msds692_practicum/blob/main/Visualizations/Financial%20Info%20Boxplot.png" width="500">

## Classification Models
I fit the data to 6 different classification models. First to three that did not need data scaled: decision tree, random forest, and Naive Bayes.
After this, I scaled the data using the StandardScaler and then fit models for logistic regression, artificial neural network, and K-nearest neighbors.

The model that performed the best for ELA scores was logistic regression.

The models that performed the best for Math scores were logistic regression and random forest.

## Conclusion


## Resources and References
### Datasets Combined
   - [2025 CMAS Math and ELA State Summary Results (XLS)](https://www.cde.state.co.us/assessment/2025_cmas_ela_math_statesummaryachievementresults)
      - [2024-25 Race/Ethnicity and Gender Membership by LEA (XLSX)](https://www.cde.state.co.us/cdereval/2024-25raceethnicityandgenderbylea)
      - [Student Teacher Ratios by LEA (XLSX)](https://www.cde.state.co.us/cdereval/2025_staffstatistics_studentteacherratio-bylea)
      - [Average Teacher Salary (XLSX)](https://www.cde.state.co.us/cdereval/2025_staffstatistics_averageteachersalary)
      - [2024-25 Race/Ethnicity and Percent Minority Membership by LEA (XLSX)](https://www.cde.state.co.us/cdereval/2024-25raceethnicityandpercentminoritymembershipbylea)
      - [2024-2025 Attendance and Truancy Rates by LEA (XLSX)](https://www.cde.state.co.us/cdereval/2025_attendance_districtattendanceandtruancy)
      - [Teachers by Race/Ethnicity and Gender (XLSX)](https://www.cde.state.co.us/cdereval/2025_staffstatistics_teachers-race-eth-gender)
      - [Personnel Turnover Rate by District and Position Categories (XLSX)](https://www.cde.state.co.us/cdereval/2025_staffstatistics_personnelturnoverrate_districtandposition)
      - [Funding per pupil: District Level Data File](https://www.cde.state.co.us/cdefinance/ft_fy2024_distdatafile)
