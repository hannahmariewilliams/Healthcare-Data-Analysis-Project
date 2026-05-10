# Financial Analysis

### Total Revenue by Treatment Type
```sql
SELECT
SUM(cost) TotalRevenue,
treatment_type
FROM treatments
GROUP BY treatment_type
Order BY TotalRevenue DESC
```

Result:
<img width="276" height="178" alt="image" src="https://github.com/user-attachments/assets/5407059f-988b-428e-92e3-fd5bd40608da" />

For this, I selected the SUM of the cost and then grouped by treatment type. Then, I ordered by the total revenue descending.

### Average Cost Per Treatment Type
```sql
SELECT
ROUND(Avg(cost), 2) AvgCost,
treatment_type
FROM treatments
GROUP BY treatment_type
Order BY AvgCost DESC
```
Result:
<img width="251" height="179" alt="image" src="https://github.com/user-attachments/assets/f3038b5f-cf59-4688-9855-6e681f3614e7" />

In this case, I just updated the previous query to include the average function, so it would show the average cost per treatment type instead of SUM/total. I rounded the amount in this query as well.  

### Total Revenue by Payment Method
```sql
SELECT
SUM(amount) Revenue,
payment_method
FROM billing
WHERE payment_status = 'Paid'
GROUP BY payment_method
ORDER BY Revenue DESC
```
Result: 

<img width="263" height="122" alt="image" src="https://github.com/user-attachments/assets/6cd960d4-5918-4829-80bf-122fce589e53" />  
  
I queried the billing table and made a SUM of the cost of treatments but made sure to filter by paid status only. I grouped by the payment method so the total revenue of treatments was organized by payment method. Lastly, it was ordered to have the highest revenue by payment method first.

