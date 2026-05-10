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

For this, I selected the SUM of the cost and then grouped by treatment type. I odered by the total revenue descending.

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

In this case, I just updated the previous query to include the average function, so it would show the average cost per treatment type as opposed to the total. I rounded the amount in this query as well.  

