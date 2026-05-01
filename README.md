# Data-Analysis-Project-Hospital-Management-Dataset
Data Analysis Project using [Hospital Managemnt Dataset](https://www.kaggle.com/datasets/kanakbaghel/hospital-management-dataset)

Tools used in this project: SQL, PGAdmin PostgreSQL

Using the Hospital Management Dataset from Kaggle, I set out to explore any relevant insights within the hospital. In addition, the use of Chatgpt was used to help create pertinent business questions. 

Q: Question  
A: Answer  
E: Explanation/thought process  

### **Patient & Operations**
Q: What were the peak admission days by Month?

```
        SELECT 
        EXTRACT(MONTH FROM treatment_date),
        treatment_date,
        COUNT(appointment_id) OVER(PARTITION BY EXTRACT(MONTH FROM treatment_date)) totalappointments
        FROM treatments
        ORDER BY totalappointments DESC
```

A: April was the month with the most admissions our of 2023. Having a total of 25 appointments. This was followed by January with 20 and March with 19.  
E: I wanted to first COUNT total appointmnets and by using a window function, I was able to create a "window" per month by use of partition by. Then I used "ORDER BY" to sort by the Months with the most appointments first.  

Q: What were the peak admission days by Day?  
