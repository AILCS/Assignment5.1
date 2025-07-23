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
### Findings across all coupons
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

13. There are more datapoints on the coupons at higher temperatures rather than at low temperatures, as evident from the histogram below.
    <img width="640" height="480" alt="hist - temperature" src="https://github.com/user-attachments/assets/bbdfd089-4211-4dda-bcc6-7e0f24b2f0c4" />


### Investigating Bar Coupons and Coffee House Coupons

A deeper dive was performed specifically for Bar coupons and Coffee House coupons. Below are the key findings:
1. **What proportion of bar/coffee house coupons were accepted?**  
   Bar: 41%  
   Coffee House: 50%  

3. **Compare the acceptance rate between those who went to a bar/coffee house 3 or fewer times a month to those who went more.**  
     
   **Visit Frequency:** Drivers who visit the Bar/Coffee House 3 or more times per month are more likely to accept the respective coupons than those who visit the venue less. This is more evident for Bar coupons    (76%) than for Coffee House coupons.
   <img width="640" height="480" alt="bar - bch category 3" src="https://github.com/user-attachments/assets/e25b7a57-ac73-4e3f-94ff-b5c5c1c10fc8" />
  
4. **Compare the acceptance rate between drivers who go to a bar/coffee house once or more a month and are over the age of 25 to the all others. Is there a difference?**  
  
   **Visit Frequency + Age:** Drivers aged >25 and who visit the Bar/Coffee House once or more per month are more likely to accept the respective coupons. This is more evident for Bar coupons (69%) than for         Coffee House coupons.
   <img width="640" height="480" alt="bar - bch category 4" src="https://github.com/user-attachments/assets/15a0399f-5fe0-41bc-aedd-20783d55c845" />
  
5. **Compare the acceptance rate between drivers who go to bars/coffee houses more than once a month and had passengers that were not a kid and had occupations other than farming, fishing, or forestry.**  
  
   **Visit Frequency + Passenger Type + Occupation:** Drivers who met the condition are more likely to accept the respective coupons. This is more evident for Coffee House coupons than for Bar coupons (71%).
   <img width="640" height="480" alt="bar - bch category 5" src="https://github.com/user-attachments/assets/652b009d-12af-4c6e-ae5a-8b0ed3351113" />
  
6. **Compare the acceptance rates between those drivers who:**  
   **- go to bars/coffee houses more than once a month, had passengers that were not a kid, and were not widowed OR**  
   **- go to bars/coffee houses more than once a month and are under the age of 30 OR**  
   **- go to cheap restaurants more than 4 times a month and income is less than 50K.**
   **Based on these observations, what do you hypothesize about drivers who accepted the bar coupons?**
     
   **Visit Frequency + Passenger Type + Marital Status / Visit Frequency + Age / Cheap Restaurant Visit Frequency + Income:** Drivers who met the condition are more likely to accept the respective coupons. This     is more evident for Coffee House coupons (64%) than for Bar coupons (57%).
     
   Given the higher Bar/Coffee House coupon acceptance rates for drivers who met the conditions, my hypothesis is that young drivers who probably just started working, have limited liabilities, and enjoy going      to bars/coffee houses are more likely to accept the coupons.
   
## Recommendations and Next Steps
Based on the EDA done on selected columns of the dataset, we can conclude that Bar/Coffee House visit frequencies, together with the columns describing the profile of the driver (e.g age, income, marital status, occupation, passenger type) are useful indicators of whether the driver is likely to accept the Bar/Coffee House coupon. 
  
These columns can be used as inputs to the Bar/Coffee House coupon acceptance prediction model.  
  
Further EDA can be performed on other columns to extend the set of useful inputs for the model.

