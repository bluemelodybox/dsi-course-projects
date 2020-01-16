## Problem Statement

This intend of this project is to analyze **ACT** and **SAT** scores by state, as well as the student participation rates for the year 2017 and 2018 to answer the following questions:

- Data error analysis
  - To check through the entire dataset and compare with the official web
  - Correct errors if there are any spotted
- Investigate trends in data
  - Finding out states with the highest and lowest participation rates for 2017/2018 SAT/ACT
  - Finding out states with the highest and lowest mean total and composite scores for 2017/2018 SAT/ACT
  - Finding out if there are states with 100% participation on a given test have a rate change year-to-year
  - Finding out if there are states with more than 50% participation on either year
  - Finding out if there are possible relations between scores and participation rate
- Recommendations
  - Suggest how College Board might increase participation for state with low participation rates



## Executive Summary

- Errors such as extra characters appearing in mean score were found and removed
- Percentages in participation column were removed and converted to integer
- All 4 datasets are combined to form [final.csv](data/final.csv)
- State with lowest participation rates
  - 2017 ACT : **Maine** (8%)
  - 2018 ACT : **Maine** (7%)
  - 2017 SAT : **North** **Dakota** (2%)
  - 2018 SAT : **North** **Dakota** (2%)
- States with highest participation rates
  - 2017 ACT : **Colorado**, **Alabama**, **Kentucky**, **Wisconsin**, **Utah** ... (100%)
  - 2018 ACT : **Missouri**, **Alabama**, **Kentucky**, **Wisconsin**, **Utah** ... (100%)
  - 2017 SAT : **District of Columbia**, **Michigan**, **Connecticut**, **Delaware**, **New Hampshire** (100%)
  - 2018 SAT : **Colorado**, **Connecticut**, **Delaware**, **Michigan**, **Idaho** (100%)
- State with highest mean total/composite scores
  - 2017 ACT :  **New Hampshire** (25.5)
  - 2018 ACT :  **Connecticut** (25.6)
  - 2017 SAT :  **District of Columbia** (950)
  - 2018 SAT :  **District of Columbia** (977)
- State with lowest mean total/composite scores
  - 2017 ACT : **Nevada** (17.8)
  - 2018 ACT : **Nevada** (17.7)
  - 2017 SAT : **Minnesota** (1295)
  - 2018 SAT : **Minnesota** (1298)
- States with 100% participation on given test rate that changed year-to-year:  **Colorado** and **Illinois**  have around 80% increase from previous year participation rate
- States with more than 50% participation on both years : **Florida**, **Georgia**, **Hawaii**, **North Carolina, ** **South Carolina**
- Histograms, boxplots, heatmaps, scatterplots, line plots were used as visualizations
- Strong negative relationship between test participation and average test score is found. States with lower participation rates likely to see higher average scores than a state with higher participation rates on that same test.
- The distribution for ACT participation rates are skewed left and the distribution for SAT participation rates are skewed right for both years. ACT participation is higher than SAT.



## Data Description

### Data Sources

- [2017 ACT Scores](https://www.act.org/content/dam/act/unsecured/documents/cccr2017/ACT_2017-Average_Scores_by_State.pdf) | [2017 SAT Scores](https://blog.collegevine.com/here-are-the-average-sat-scores-by-state/) | | [2018 ACT Scores](https://www.act.org/content/dam/act/unsecured/documents/cccr2018/Average-Scores-by-State.pdf) | [2018 SAT](https://blog.prepscholar.com/average-sat-scores-by-state-most-recent)

- [US State Code Dictionary](https://gist.github.com/mshafrir/2646763)

  

### Data Dictionary

| Feature                      | Type      | Dataset   | Description                                                  |
| ---------------------------- | --------- | --------- | ------------------------------------------------------------ |
| **state**                    | *object*  | ACT / SAT | The states in the United States of America                   |
| **act_2017_participation**   | *int64*   | ACT       | The percentage of students that took ACT 2017 ranging from 0 to 100 |
| **act_2017_english**         | *float64* | ACT       | Mean ACT 2017 English score of each state ranging from 1 to 36 |
| **act_2017_math**            | *float64* | ACT       | Mean ACT 2017 Math score ranging from 1 to 36                |
| **act_2017_reading**         | *float64* | ACT       | Mean ACT 2017 Reading score ranging from 1 to 36             |
| **act_2017_science**         | *float64* | ACT       | Mean ACT 2017 Science score ranging from 1 to 36             |
| **act_2017_composite**       | *float64* | ACT       | Mean composite score calculated by averaging the 4 other ACT 2017 scores ranging from 1 to 36 |
| **sat_2017_participation**   | *int64*   | SAT       | The percentage of students that took SAT 2017 ranging from 0 to 100 |
| **sat_2017_reading_writing** | *int64*   | SAT       | Mean SAT 2017 Reading and Writing score ranging from 200 to 800 |
| **sat_2017_math**            | *int64*   | SAT       | Mean SAT 2017 Math score ranging from 200 to 800             |
| **sat_2017_total**           | *int64*   | SAT       | Total score calculated by adding the other 2 SAT 2017 scores ranging from 400 to 1600 |
| **act_2018_participation**   | *int64*   | ACT       | The percentage of students that took ACT 2018 ranging from 0 to 100 |
| **act_2018_english**         | *float64* | ACT       | Mean ACT 2018 English score of each state ranging from 1 to 36 |
| **act_2018_math**            | *float64* | ACT       | Mean ACT 2018 Math score ranging from 1 to 36                |
| **act_2018_reading**         | *float64* | ACT       | Mean ACT 2018 Reading score ranging from 1 to 36             |
| **act_2018_science**         | *float64* | ACT       | Mean ACT 2018 Science score ranging from 1 to 36             |
| **act_2018_composite**       | *float64* | ACT       | Mean composite score calculated by averaging the 4 other ACT 2018 scores ranging from 1 to 36 |
| **sat_2018_participation**   | *int64*   | SAT       | The percentage of students that took SAT 2018 ranging from 0 to 100 |
| **sat_2018_reading_writing** | *int64*   | SAT       | Mean SAT 2018 Reading and Writing score ranging from 200 to 800 |
| **sat_2018_math**            | *int64*   | SAT       | Mean SAT 2018 Math score ranging from 200 to 800             |
| **sat_2018_total**           | *int64*   | SAT       | Total score calculated by adding the other 2 SAT 2018 scores ranging from 400 to 1600 |
| **state_code**               | *object*  | ACT / SAT | Code of the states in United States of America.              |



## Outside Research

- Colorado students' participation for ACT decreased 70% from 100% in 2017 to 30 % in 2018. These students went to take SAT and the SAT participation rate for Colorado increased 89% from 11% in 2017 to 100% in 2018. This is due to new contract acquired by SAT. This also result in decrease in the mean SAT total score, from 1201 to 1025 as well as an increase in the composite ACT score, from 20.8 to 23.9 from year 2017 to 2018.
- Similarly for Illinois students' participation for ACT decreased 53% from 93% in 2017 to 40 % in 2018. These students went to take SAT and the SAT participation rate increased 90% from 9% in 2017 to 99% in 2018. This is due to the new contract acquired by SAT, similar to Colorado. This also result in decrease in the mean SAT total score, from 1115to 1019 as well as an increase in the composite ACT score, from 21.4 to 23.9 from year 2017 to 2018.
- Florida is the only state to show net decrease in both SAT and ACT. It rejects replacing Florida State Assessment with ACT or SAT
- Florida, Georgia, Hawaii students have almost equal amount of students participating in SAT and ACT
- Rhode Island also has increase in SAT participation rates, from 71% to 97%
- Utah has a huge drop in SAT mean score, from 1238 to 1010. Because there is very little participants for SAT, the mean score will change drastically.





## Conclusion and Recommendations

There is a strong competition between SAT and ACT test. In addition, state department of education have a large impact on the SAT and ACT participation rates. They can impact the participation rates by providing subsidies to students for test or making test compulsory for all students. Illinois and Colorado are examples   to it. Hence, collaboration with state education departments and colleges would lead to the increase in SAT participation rates.

There are states with equal amount of students participating in SAT and ACT such as Florida, Georgia and Hawaii. These states are recommended to look into for for increase in SAT participation rates.



#### Source:

https://www.washingtonpost.com/education/2018/10/23/sat-reclaims-title-most-widely-used-college-admission-test/



