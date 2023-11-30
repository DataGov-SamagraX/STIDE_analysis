## Introduction 
Analysis required to calculate the drop out rates for students from college 
 The analysis was carried out [here](https://colab.research.google.com/drive/13TfDJ94UwWiFQ1zycXdYwR31GrIp5Pja?usp=sharing)

## 10th grade drop outs : 

If students who were in tenth grade in pre matriculation data table and if they are not present in the post matriculation tables for the years '2022-23', '2023-2024'; then they are considered as dropped out.  


## Drop outs after post-matriculation : 

### Introduction
This document explains the logic used to calculate dropout rates for students across various courses. Data is available for 3  academic years. 
### Defintion:  

A student in the data who attended a non-final year of college in 2021 or 2022 and didn't attend in the years after that. Only students joining the course after 2021 are considered.


### Calculation: 
#### Maximum Course Year Calculation for each course : 
For each course, the maximum year (course length of a course) a student can be in is determined. 


### Dropout calculation (without considering course change as dropout) :  


 - Eligible students - Removing students who joined before 2021
  
 - Eligible students - Filtering by Academic Year : Students in the last academic year (2022-23) are excluded, as their dropout status cannot be determined with the available data.

- Eligible students - Excluding Final Year Students : They cannot be considered for dropout analysis as they have reached last year and there is no next year to drop out.

-  Considering 'last eligible year' for student :  For the eligible students, the last academic year (amongs eligible years) is considered so that only record per student is present.  If they have both 1st and 2nd year, then only 2nd year's record is considered as only this is required for dropout. If 2nd and 3rd year is present, then only 3rd year is considered etc.  

- Calculating the 'last attended year' for eligible student :  This is the last academic year they attended college is calculated (without considering eligible years)

- If 'last attended year' is higher than 'last eligible' year for a student, that means they continued without dropping out. If it is the same, it means they dropped out.

### Dropout calculation ( considering course change as dropout) :  

This will be same as above except last year is calculated as student course level instead of student level. The below line only will change. 

- Calculating the 'last attended year' for eligible student :  The last academic year they attended college **for that course** is calculated (without considering eligible years)


### Dropout calculation ( considering institute change as dropout) :  

This will be same as above except last year is calculated as student institute level instead of student level. The below line only will change. 

- Calculating the 'last attended year' for eligible student :  The last academic year they attended college **for that institute** is calculated (without considering eligible years)


### Test cases : 

1. Student has taken a 2 year course (2021-2023). He attends both years and data is there for both years.
Only first year row is considered as 'eligible'. 'Last attended year' 2022 is more than 'last eligible year' 2021. They didnt drop out. He is considered as **non drop out** 

2.  Student has taken a 3 year course (2020-2023). he is there for first 2 years and not there for last year.
He is eligible for first 2 years and 2nd year is considered as 'last eligible year'. 'Last attended year' is the same as he is considered **dropped out**

3. Student has taken a 5 year course (2019-2024) : He is there for all 3 years.  Last eligible year :  2022, Last attended year :  2023. He is **non drop out**

4. Student attended 1st year and 3rd year for a 3 year course. Last eligible year :  2021, Last attended year :  2023. He is **non drop out**




## Drop outs after from Bachelors to Masters : 
 

Only students from a predefined Bachelor's course list<sup>[1]</sup>  in their last year in either 2021/2022 are considered as eligible students. Only latest Bachelors is considered (in the unlikely event students have attended two final year bachelor programs) 

Its checked if these 'eligible students' have enrolled in any Masters programs (based on a predefined Masters course list <sup>[2]</sup>  )



### Grouping :  
The total number of students and the number of students who have not dropped out are calculated for each gender group.
The number of students who dropped out is derived by subtracting the number of students who have not dropped out from the total number of students.
Dropout rates are calculated as a percentage of the total number of students.





## Appendix 


[1] Bachelors courses :  
List of Bachelors courses are : 
'B. Ed.',
'B. Sc. Technical/Professional',
'BVA ( Bachelor in Visual Art )',
'Bachelor of Business Administration (BBA)',
'Bachelor of Computer Application (BCA)',
'Plus 3',
'Integrated BED',
'Integrated BED-MED',
'Integrated Bachler in Science',
'Integrated M.Sc.',
'Integrated MBA',
'Integrated MCA',
'Integrated Master in Science',
'Interior Design',
'Journalism',
'Law',
'Management',
'Agriculture & Allied Sciences',
'Animal Husbandary',
'Applied Art & Craft',
'Architecture',
'Ayurvedic',
'Engineering - B.Tech Course',
'Fashion Design',
'Fashion Technology',
'Fishery',
'Forestry',
'Homeopathy',
'Hotel Management',
'Hotel Management (PG)',
'Dental',
'Medical',
'Multimedia and Animation',
'Nursing',
'Occupational Therapy',
'Para-Medical',
'Performing Arts',
'Pharmacy',
'Physical Education',
'Physiotherapy',
'Prosthetics and Orthotics',
'Public Health',
'Social Works',
'Textile Design',
'Tourism/Travel',
'Tourism/Travel Management'



[2] Masters courses  :  
List of masters courses are : 
'M. A.',
'M. Com.',
'M. Ed.',
'M. Phill',
'M. Sc.',
'M. Sc. Technical/Professional',
'M. Tech.',
'Master in Computer Application (MCA)',
'Master in Finance & Control (MFC)',
'Master in Social Work ( MSW)/ Master in Social Management',
'Master in Visual Arts',
'Master of Business Administration (MBA)'
