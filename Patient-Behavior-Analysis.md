# Patient Behavior Analysis

### Patient Retention Analysis
```sql
SELECT 
patient_id,
COUNT(*) total_appointments
FROM appointments
WHERE status = 'Completed'
GROUP BY patient_id
HAVING COUNT(*) > 1
ORDER BY total_appointments DESC
```
Result:
<img width="260" height="260" alt="image" src="https://github.com/user-attachments/assets/94833627-ab88-4e48-90e5-4aa6e3ffeaa4" />


In this case I wanted to find which patients had come for at least two appointments (COUNT). To begin I counted all appointments and 
grouped by patient. I filtered by completed status (WHERE) and the total appointments per patient must be more than 1 (HAVING).

```sql
SELECT COUNT(*)
FROM(
SELECT 
patient_id,
COUNT(*) total_appointments
FROM appointments
WHERE status = 'Completed'
GROUP BY patient_id
HAVING COUNT(*) > 1
ORDER BY total_appointments DESC
) appointmentsrepeatperpatient
```
Result: **12 repeat patients**  
I just added a subquery and counted all of the patients who had **more** than one completed appointment (COUNT(*) > 1.

```sql
SELECT
COUNT(*)
FROM(
SELECT 
patient_id,
COUNT(*)
FROM appointments
WHERE status = 'Completed'
GROUP BY patient_id) totalpatientswithcompletedappointment
```
Result: **33 patients who had at least one completed appointment**  
COUNT of all patients with at least one completed appointment.

### Revisit Rate
```sql
WITH patient_visits AS (
    SELECT
        patient_id,
        COUNT(*) total_appointments
    FROM appointments
	WHERE status = 'Completed'
    GROUP BY patient_id
)
SELECT
 CONCAT(ROUND((SUM(CASE WHEN total_appointments > 1 THEN 1 ELSE 0 END) * 1.0 / COUNT(*)) * 100, 2), '%') revisit_rate
FROM patient_visits;
```

Result:

!!!!!!!!!!!UNDER CONSTRUCTIONNNNN
