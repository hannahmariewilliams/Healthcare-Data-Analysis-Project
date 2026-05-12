# Financial Analysis

### Total Revenue by Treatment Type
```sql
SELECT 
SUM(t.cost) TotalRevenue,
t.treatment_type
FROM treatments t
INNER JOIN billing b
ON t.treatment_id = b.treatment_id
GROUP BY t.treatment_type, b.payment_status = 'Paid'
HAVING b.payment_status = 'Paid'
ORDER BY TotalRevenue DESC
```

Result:
<img width="274" height="176" alt="image" src="https://github.com/user-attachments/assets/cadc9cef-de7d-4542-bd8b-0ac2079c6340" />

For this query, I joined the treatments and billing tables as I needed the treatment type and the payment status columns. I then made a sum of the treatment cost and aggregated by treatment type. After, I filtered by only 'paid' payments. Then I ordered by the treatment type with the highest revenue first.

### Average Cost Per Treatment Type
```sql
SELECT
ROUND(Avg(t.cost), 2) AvgCost,
t.treatment_type
FROM treatments t
INNER JOIN billing b
ON t.treatment_id = b.treatment_id
GROUP BY t.treatment_type, b.payment_status ='Paid'
HAVING b.payment_status = 'Paid'
Order BY AvgCost DESC
```
Result:
<img width="248" height="180" alt="image" src="https://github.com/user-attachments/assets/f4c3806f-5389-497a-8cfd-5a4818ae0781" />

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

