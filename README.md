APPROACH:
1. Count funded savings and investment plans per user.
2. Sum all deposits by user.
3. Filter users who meet both conditions and rank them by total deposits.


CHALLENGES:
Issue: Users with only one plan type (either savings or investment) were being included initially.
Solution: Used conditional aggregation (CASE WHEN) to count only funded plans by type. Filtered the final results to only include users with both funded savings and investment plans using WHERE.

Issue: Missing deposits for some users led to NULL values.
Solution: Applied COALESCE() on deposit sums to convert NULL to 0.
