## Introduction 
Analysis required to calculate the drop out rates for students from college 
 The analysis was carried out [here](https://colab.research.google.com/drive/13TfDJ94UwWiFQ1zycXdYwR31GrIp5Pja?usp=sharing)

## 10th grade drop outs : 



## Drop outs after post-matriculation : 

### Introduction
This document explains the logic used to calculate dropout rates for students across various courses. Data is available for 3  academic years. 
### Defintion:  

A student in the data who attended a non-final year in 2021 or 2022 and didnt attend the years after that. 

#### Maximum Course Year Calculation for each course : 
For each course, the maximum year (course length of a course) a student can be in is determined.


### Dropout calculation (without considering course change as dropout) :  

 - Eligible students - Filtering by Academic Year :
Students in the last academic year (2022-23) are excluded, as their dropout status cannot be determined with the available data.

- Eligible students - Excluding Final Year Students : They cannot be considered for dropout analysis as they have reached last year and there is no next year to drop out.

-  Considering 'last eligible year' for student :  For the eligible students, the last academic year (amongs eligible years) is considered so that only record per student is present.  If they have both 1st and 2nd year, then only 2nd year's record is considered as only this is required for dropout. If 2nd and 3rd year is present, then only 3rd year is considered etc.  

- Calculating the 'last attended year' for eligible student :  This is the last academic year they attended college is calculated (without considering eligible years)

- If 'last attended year' is higher than 'last eligible' year for a student, that means they continued without dropping out. If it is the same, it means they dropped out.

### Dropout calculation ( considering course change as dropout) :  

This will be same as above except last year is calculated as student course level instead of student level

 - Eligible students - Filtering by Academic Year :
Students in the last academic year (2022-23) are excluded, as their dropout status cannot be determined with the available data.

- Eligible students - Excluding Final Year Students :
Further filtering excludes students who are in their final course year. They cannot be considered for dropout analysis as they have reached or are about to complete their courses.

-  Considering 'last eligible year' for student :  For the eligible students, the last academic year (amongs eligible years) **for that course** is considered so that only record per student is present.  If they have both 1st and 2nd year, then only 2nd year's record is considered as only this is required for dropout. If 2nd and 3rd year is present, then only 3rd year is considered etc.  

- Calculating the 'last attended year' for eligible student :  The last academic year they attended college **for that course** is calculated (without considering eligible years)

- If 'last attended year' is higher than 'last eligible' year for a student, that means they continued without dropping out. If it is the same, it means they dropped out.


### Grouping :  
The total number of students and the number of students who have not dropped out are calculated for each gender group.
The number of students who dropped out is derived by subtracting the number of students who have not dropped out from the total number of students.
Dropout rates are calculated as a percentage of the total number of students.


### Test cases : 

1. Student has taken a 2 year course (2021-2023). He attends both years and data is there for both years.
Only first year row is considered as 'eligible'. 'Last attended year' 2022 is more than 'last eligible year' 2021. They didnt drop out. He is considered as **non drop out** 

2.  Student has taken a 3 year course (2020-2023). he is there for first 2 years and not there for last year.
He is eligible for first 2 years and 2nd year is considered as 'last eligible year'. 'Last attended year' is the same as he is considered **dropped out**

3. Student has taken a 5 year course (2019-2024) : He is there for all 3 years.  Last eligible year :  2022, Last attended year :  2023. He is **non drop out**

4. Student attended 1st year and 3rd year for a 3 year course. Last eligible year :  2021, Last attended year :  2023. He is **non drop out**
