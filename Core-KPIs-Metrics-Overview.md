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

### Full Billing and Treatment View
```sql
SELECT
p.patient_id,
p.first_name,
p.last_name,
b.amount,
b.payment_status,
t.treatment_type
FROM patients p
FULL JOIN billing b
ON p.patient_id = b.patient_id
FULL JOIN treatments t
ON b.treatment_id = t.treatment_id
```
Result: **First 13 rows**  
<img width="723" height="394" alt="image" src="https://github.com/user-attachments/assets/99c1bfc1-55ba-49fd-9d27-cf79d89485d3" />


In this query, I joined the treatments, billng and patients tables along with a selection of relevant columns.
