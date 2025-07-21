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
   - Remaining rows reflect driving customers and the 'car' column is no longer required and can be dropped.
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
The coupon acceptance rate was analysed against a few columns . Below are the key findings:
1. Coupons are highly likely to be accepted for carry outs/take aways and cheap restaurants (74% and 71% respectively).
   <img width="726" height="751" alt="stacked bar - coupon type" src="https://github.com/user-attachments/assets/e9fa6c03-ac59-4c38-9d7a-819978a1d1e8" />

2. Drivers with passenger friends are more likely to accept coupons (68%).
3. Coupons have a highest coupon acceptance rate on sunny days (60%) and lowest coupon acceptance rate on rainy days (46%).
4. Coupon acceptance rate rises in the morning, peaks at 2PM (66%) before falling at night.
   <img width="640" height="480" alt="stacked bar - time" src="https://github.com/user-attachments/assets/cb240e1c-310d-4318-9b67-3cab709459a9" />

5. Longer expiry (1d) coupons have a higher acceptance rate than shorter expiry (2h) coupons (63% vs 50% respectively).
6. Male drivers are slightly more likely to accept coupons than female drivers (59% vs 55% respectively).
7. Younger drivers are more likely to accept coupons than older ones (63% for age < 21 vs 51% for age > 50).
   <img width="640" height="480" alt="stacked bar - age" src="https://github.com/user-attachments/assets/537aa6a4-f0dd-48c7-94c5-8e65abea5fd1" />

8. Singles are most likely to accept coupons(61%) while widows are least likely (47%).
9. Drivers with kids are less likely (54%) to accept coupons than drivers without kids (59%).
10. High school students are most likely (72%) to accept coupons while postgraduates are least likely (53%).
11. 'Healthcare Practitioners & Technical' and 'Production Occupations' occupations have the highest coupon acceptance rates (72% and 70% respectively) while retirees have the lowest coupon acceptance rates (46%).
    <img width="578" height="742" alt="stacked bar - occupation" src="https://github.com/user-attachments/assets/20ddb48e-aae3-46ef-8916-a88997174ce4" />

12. No material relationship between income and coupon acceptance.
    <img width="725" height="691" alt="stacked bar - income" src="https://github.com/user-attachments/assets/728e5289-5ebe-4832-948c-b4893fb4df4a" />

A deeper dive was performed specifically for Bar coupons and Coffee House coupons to scope the assessment. Below are the key findings:


## Recommendations and Next Steps
