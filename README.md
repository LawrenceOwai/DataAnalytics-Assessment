✅ Question 1: High-Value Customers with Multiple Products...
Approach: I identified users with at least one funded savings and investment plan, then summed their total deposits and ranked them.

Challenges: Some users had only one type of plan; some had no deposits, which returned nulls.

Solutions: Applied filters for both funded plan types and used COALESCE to replace null deposit values with 0.

✅ Question 2: User Deposit Frequency and Volume...
Approach: I joined users with their savings records, counted the number of deposits, and summed the amounts.

Challenges: Users with no deposits were excluded using an inner join.

Solutions: Switched to a left join and used COALESCE to ensure all users were included with 0s where applicable.

✅ Question 3: Dormant Users (No Activity in 6 Months)...
Approach: I selected users who made neither deposits nor withdrawals in the last 6 months.

Challenges: Handling date intervals across SQL dialects and filtering users who did either action.

Solutions: Used standard interval syntax and combined two subqueries with NOT IN to exclude active users.

✅ Question 4: Average Funding Time...
Approach: I calculated the number of days between plan creation and the first deposit, then averaged the result.

Challenges: Some plans had no deposits; date subtraction syntax varies by SQL dialect.

Solutions: Filtered out unfunded plans and used MIN() to get the first deposit date, ensuring consistent date difference calculation.
