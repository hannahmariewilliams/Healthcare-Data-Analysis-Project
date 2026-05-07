# Patient Behavior Analysis

### Patient Retention Analysis
```sql
SELECT 
patient_id,
COUNT(*) total_appointments
FROM appointments
WHERE status = 'Completed' OR status = 'Scheduled'
GROUP BY patient_id
HAVING COUNT(*) > 1
ORDER BY total_appointments DESC
```
Result:
<img width="393" height="486" alt="image" src="https://github.com/user-attachments/assets/444253db-14c6-4ed5-ab6d-ae887456f62b" />

In this case I wanted to find which patients had come for at least two appointments (COUNT()). To begin I counted all appointments and 
grouped by patient. I filtered by either schduled or completed statuses (WHERE) and the total appointments per patient must be more than 1 (HAVING).
I inserted just the first 13 rows for the sake of space.

```sql
SELECT COUNT(*)
FROM(
SELECT 
patient_id,
COUNT(*) total_appointments
FROM appointments
WHERE status = 'Completed' OR status = 'Scheduled'
GROUP BY patient_id
HAVING COUNT(*) > 1
ORDER BY total_appointments DESC
) appointmentsrepeatperpatient
```
Result: **29 repeat patients**
I just added a subquery and counted all of the patients who had more than one appointment.

```sql
SELECT COUNT(*)
FROM appointments
WHERE status = 'Completed' OR status = 'Scheduled'
```
Result: **97 patients who had either a scheduled or completed appointment**
