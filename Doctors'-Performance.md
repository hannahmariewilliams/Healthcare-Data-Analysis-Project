# Doctor's Performance

### Patients per Doctor
```sql
SELECT
COUNT(DISTINCT a.patient_id) patientsperdoctor,
d.doctor_id,
d.first_name,
d.last_name
FROM doctors d
LEFT JOIN appointments a
ON d.doctor_id = a.doctor_id
GROUP BY d.doctor_id, d.first_name, d.last_name
ORDER BY patientsperdoctor DESC;
```
Result 
<img width="260" height="166" alt="image" src="https://github.com/user-attachments/assets/e353576b-73fe-4376-aa26-0a61a63a3128" />
The doctor with the most patients is Sarah Taylor with 23. I used a join to ensure that all doctors, even those without patient appointments were included. In this case, all doctors had appointments. 
I also used the Count distinct to ensure no patient duplicates were included and ordered by doctors with the most patients first.
