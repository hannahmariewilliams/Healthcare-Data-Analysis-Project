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
Result:  
<img width="260" height="166" alt="image" src="https://github.com/user-attachments/assets/e353576b-73fe-4376-aa26-0a61a63a3128" />

The doctor with the most patients is Sarah Taylor with 23. I used a join to ensure that all doctors, even those without patient appointments were included. In this case, all doctors had appointments. 
I also used the COUNT() DISTINCT to ensure no patient duplicates were included and ordered by doctors with the most patients first.

### Appointments per Doctor
```sql
--Appointments per doctor
SELECT COUNT(a.appointment_id) total_appoointments,
d.doctor_id,
d.first_name,
d.last_name
FROM doctors d
LEFT JOIN appointments a
ON a.doctor_id = d.doctor_id
WHERE status = 'Completed'
GROUP BY d.doctor_id, d.first_name, d.last_name
ORDER BY COUNT(a.appointment_id) DESC;
```
Result:  
<img width="260" height="166" alt="image" src="https://github.com/user-attachments/assets/9eb56d11-415e-465c-a445-60df543b5c5e" />

In this case I used a LEFT JOIN to include all doctors, even if they had no appointments. Then I used COUNT() function to add together all appointments and grouped them by doctor. In this case I only wanted completed appointments by doctor, so I filtered by WHERE and Ordered by the doctors with the most completed appointments first.

### Workload by Specialization
```sql
SELECT 
COUNT(appointment_id) totalappointments,
d.specialization
FROM appointments a
LEFT JOIN doctors d
ON a.doctor_id = d.doctor_id
WHERE status = 'Completed'
GROUP BY d.specialization
```
Result: **22 Pediatrics appointments, 14 Dermatology and 10 in Oncology.**

I first needed to count up all appointments using COUNT() in the appointments table, filtered by those that were completed (WHERE). Then, I used GROUP BY to put appointments into specilizations buckets which were found in the doctors table hence using a LEFT JOIN.
