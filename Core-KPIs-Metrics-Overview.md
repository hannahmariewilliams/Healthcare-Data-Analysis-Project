# Core KPIs Overview Metrics

### Total Appointments
```sql
SELECT 
COUNT(*) total_appointments
FROM appointments
```
Result: **200 Total appointments**

### Total Appointments by Status
```sql
SELECT 
COUNT(*),
Status
FROM appointments
GROUP BY status
```
Result: **51 Scheduled, 52 No Shows, 46 Completed, and 51 Cancelled**

### No Show Rate
```sql
SELECT 
	ROUND(COUNT(CASE WHEN status = 'No-show' THEN 1 END) * 1.0 / COUNT(*), 2) no_show_rate
FROM appointments
```
Result: **26% No-show rate**

For this, first I used a case statement to only account for No-show appointments by assigning them to "1". Then I used COUNT() funciton to count them up. I multiplied by 1.0 as PostgreSQL will round up to the nearest integer if it's not considered numeric (able to handle decimals). After this, I divided by the total appointments which gives us the No-Show rate. I also used the ROUND() function to give us a clean 0.26 across all appointments.

### Total Revenue
```sql
SELECT 
SUM(amount)
FROM billing
WHERE payment_status = 'Paid'
```
Result: **Total revenue is $173,424.90**

In this case, I used the SUM() function to add together all of the payments to the hospital and filtered it by "Paid" as there are also "Failed" and "Pending" payments.

### Payment Status Breakdown
```sql
SELECT 
	payment_status,
	COUNT(*) count,
	SUM(amount) TotalRevenue
FROM billing
GROUP BY payment_status
```
Result: **64 payments for a total of $173,424.90, 67 failed payments totaling $193,212.94 and 69 pending payments for a total of $184,612.01**

 I used COUNT() of total payments grouped by status and SUM() also grouped by status which provided total revenue.
