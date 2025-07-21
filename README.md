# Exploratory Data Analysis on Coupon Acceptance Rates

**Assignment Notebook:** https://github.com/AILCS/Assignment5.1/blob/main/prompt_working%20(final).ipynb 



## Overview
The code uses Exploratory Data Analysis (EDA) to assess how data from the [coupons.csv](https://github.com/AILCS/Assignment5.1/blob/main/data/coupons.csv) can be used to answer the question “Will a customer accept the coupon?”. 



## Problem Statement
Explore the data using plots, statistical summaries, and visualisation using Python to distinguish drivers who accepted the coupon and those who did not. THen recommend the data columns that can be used to predict whether a driver will accept the coupon.



## Data Description
The data comes from the UCI Machine Learning repository and was collected via a survey on Amazon Mechanical Turk. The survey describes different driving scenarios including the destination, current time, weather, passenger, etc., and then asks the person whether he will accept the coupon if he is the driver. Answers that the user will drive there ‘right away’ or ‘later before the coupon expires’ are labeled as ‘Y = 1’ and answers ‘no, I do not want the coupon’ are labeled as ‘Y = 0’. There are five different types of coupons -- less expensive restaurants (under $20), coffee houses, carry out & take away, bar, and more expensive restaurants ($20 - $50).

THe values mentioned below are average values. The attributes of this data set include:

1. User attributes
   - Gender: male, female
   - Age: below 21, 21 to 25, 26 to 30, etc.
   - Marital Status: single, married partner, unmarried partner, or widowed
   - Number of children: 0, 1, or more than 1
   - Education: high school, bachelors degree, associates degree, or graduate degree
   - Occupation: architecture & engineering, business & financial, etc.
   - Annual income: less than \$12500, \$12500 - \$24999, \$25000 - \$37499, etc.
   - Number of times that he/she goes to a bar: 0, less than 1, 1 to 3, 4 to 8 or greater than 8
   - Number of times that he/she buys takeaway food: 0, less than 1, 1 to 3, 4 to 8 or greater than 8
   - Number of times that he/she goes to a coffee house: 0, less than 1, 1 to 3, 4 to 8 or greater than 8
   - Number of times that he/she eats at a restaurant with average expense less than \$20 per person: 0, less than 1, 1 to 3, 4 to 8 or greater than 8
   - Number of times that he/she goes to a bar: 0, less than 1, 1 to 3, 4 to 8 or greater than 8

2. Contextual attributes
   - Driving destination: home, work, or no urgent destination
   - Location of user, coupon and destination: we provide a map to show the geographical location of the user, destination, and the venue, and we mark the distance between each two places with time of driving.       - The user can see whether the venue is in the same direction as the destination.
   - Weather: sunny, rainy, or snowy
   - Temperature: 30F, 55F, or 80F
   - Time: 10AM, 2PM, or 6PM
   - Passenger: alone, partner, kid(s), or friend(s)

3. Coupon attributes
   - time before it expires: 2 hours or one day



## Assumptions Applied In Data Cleaning
The following assumpions were applied to derive a clean dataset:
1. 'car' column: Only rows that indicate driving customers are kept.
   - 22 rows with 'do not drive' dropped 
   - 22 rows with 'Scooter and motorcycle' dropped
2. 'Bar' column: Keep only rows with populated values.
   - 107 NaN rows dropped 
4. 'CoffeeHouse' column: Keep only rows with populated values.
   - 217 NaN rows dropped 
5. 'CarryAway' column: Keep only rows with populated values.
   - 151 NaN rows dropped 
6. 'RestaurantLessThan20' column: Keep only rows with populated values.
   - 130 NaN rows dropped 
7. 'Restaurant20To50' column: Keep only rows with populated values.
   - 189 NaN rows dropped 

**Resulting cleaned dataset has 12035 rows with all columns populated.**



## Key Findings
The EDA was performed specifically for Bar coupons and Coffee House coupons to scope the assessment. Below are the key findings:
1. Coupons are highly likely to be accepted for carry outs/take aways and cheap restaurants (74% and 71% respectively).
2. Coupons are more likely to be accepted (63%) when drivers are not heading home (51%) or to work (50%).
3. Drivers with passenger friends are more likely to accept coupons (68%).
4. Coupons have a higher acceptance rate on sunny days (60%).
5. Longer expiry (1d) coupons have a higher acceptance rate than shorter expiry (2h) coupons (63% vs 50% respectively).
6. Singles are more likely to accept coupons(61%).
7. 'Healthcare Practitioners & Technical' and 'Production Occupations' occupations have the highest coupon acceptance rates (72% and 70% respectively).
8. No material relationship between income and coupon acceptance.



## Recommendations
