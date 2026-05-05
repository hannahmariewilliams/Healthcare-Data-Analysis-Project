# Core KPIs Overview Metrics

### Total Appointments
```sql
SELECT 
COUNT(*) total_appointments
FROM appointments
```
200 Total appointments

### Total Appointments by Status
```sql
SELECT 
COUNT(*),
Status
FROM appointments
GROUP BY status
```
51 Scheduled, 52 No Shows, 46 Completed, and 51 Cancelled

### No Show Rate
```sql
SELECT 
	ROUND(COUNT(CASE WHEN status = 'No-show' THEN 1 END) * 1.0 / COUNT(*), 2) no_show_rate
FROM appointments
```
For this, first I used a case statement to only account for No-show appointments by assigning them to "1". Then I used COUNT() funciton to count them up. I multiplied by 1.0 as PostgreSQL will round up to the nearest integer if it's not considered numeric (able to handle decimals). After this, I divided by the total appointments which gives us the No-Show rate. I also used the ROUND() function to give us a clean **0.26 or 26% No-show rate** accross all appointmnets.

### Total Revenue
```sql
SELECT 
SUM(amount)
FROM billing
WHERE payment_status = 'Paid'
```
In this case, I used the SUM() function to add together all of the payments to the hospital and filtered it by "Paid" as there are also "Failed" and "Pending" payments. **Total revenue is $173,424.90**

### Payment Status Breakdown
```sql
SELECT 
	payment_status,
	COUNT(*) count,
	SUM(amount) TotalRevenue
FROM billing
GROUP BY payment_status
```
COUNT() of total payments grouped by status. **Paid: 64, Failed: 67, Pending 69** 

SUM() by status which gives total revenue by status. **Paid: $173,424.90, Failed: $193,212.94, Pending: $184612.01**
