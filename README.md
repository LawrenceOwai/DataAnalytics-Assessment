QUESTION 1: Customers with Savings and Investment Plans

Approach:
I joined the user table with savings and investment plan tables. Then, I counted how many of each type (savings and investment) each user had, and summed up their confirmed deposits.

Challenges:
Some users didn’t have both savings and investment plans, which could distort the count or produce incorrect results.

Solution:
I used LEFT JOIN to include all users, and then grouped by user. I also used COALESCE to handle any nulls in the deposit amount.


QUESTION 2: Categorizing Customers by Transaction Frequency

Approach:
I merged all transactions from savings and plans, grouped them by user and month, and then calculated each user's average number of monthly transactions. Based on the result, I assigned a frequency category: High, Medium, or Low.

Challenges:
Combining different transaction types and handling date formatting consistently across both tables was tricky.

Solution:
I used UNION ALL to combine the data, DATE_FORMAT() to standardize the date by month, and CASE to assign frequency levels based on calculated averages.



QUESTION 3: Identifying Inactive Users

Approach:
I pulled the most recent transaction (from either savings or plans) for each user, then calculated how many days have passed since that transaction. Users inactive for a year or more were flagged.

Challenges:
Finding the latest transaction across two different sources (savings and plans) required careful handling to avoid duplicates or missing values.

Solution:
I used ROW_NUMBER() to rank each user's latest transaction across both sources, then filtered for those with inactivity of 365 days or more.


QUESTION 4: Estimating Customer Lifetime Value (CLV)

Approach:
I calculated the number of months each user has been with the platform, the total number of transactions, and estimated profits based on transaction amounts. Then, I used a formula to project CLV.

Challenges:
The profit margin was assumed (0.1%), and users without transactions could cause division by zero errors.

Solution:
I wrapped the CLV formula in a CASE condition to avoid dividing by zero and used COALESCE to fill missing values with 0. The final CLV is shown only for active customers.
