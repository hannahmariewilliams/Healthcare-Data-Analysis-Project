# Exploratory Data Analysis Healthcare

## Executive Summary:
Using SQL, I pulled patients, doctors, and financial data from the hospital database and explored the data. As a result, I identifyied that the hospital has a high no show rate, that most scheduled appointments are check-ups and the highest grossing treatment type is X-Ray. I recommend that the hospital improves on the following:

1. Automated reminders and/or flexible re-scheduling
2. Dedicated time blocks for scheduling check-ups
3. Ensure staff, equipment, and scheduling are adequately supported for X-Ray services

### Business Problem:
The hospital is experiencing operational inefficiencies that impact both revenue and patient care quality. A high patient no-show rate leads to underutilized appointment slots. Additionally, the high volume of routine check-ups and the significant revenue contribution from X-ray services highlight a misalignment between scheduling practices and demand patterns. Without more strategic scheduling and resource allocation, the hospital risks continued revenue loss, and reduced patient access to timely care.

### Methodology:
1. SQL query to perform exploratory data analysis
   
2. Build a dashboard in Tableau that shows the visualizes key metrics *

### Skills:
SQL: Joins, aggregate functions, CTEs

Tableau: **

### Results & Business Recommendation:
The hospital is experiencing operational inefficiencies that negatively impact revenue and patient access to care. A high patient no-show rate of 26% results in underutilized appointment capacity and lost revenue opportunities. Additionally, a large share of appointments consists of routine check-ups, while X-ray services account for 28% of total revenue, indicating a misalignment between scheduling practices and revenue-driving services. Without more strategic scheduling and resource allocation, the hospital risks continued inefficiencies, reduced capacity utilization, and missed opportunities to optimize high-value services.

Because the hospital is experiencing a 26% patient no-show rate and a significant portion of revenue is concentrated in high-demand services like X-ray (28% of total revenue), I recommend several targeted operational adjustments:

1. Implement automated appointment reminders and confirmation workflows via text and email to reduce missed appointments and improve patient attendance consistency.
2. Introduce flexible self-scheduling and rescheduling options to reduce friction for patients and allow more efficient filling of canceled or unused time slots.
3. Allocate dedicated scheduling blocks for high-frequency visit types such as routine check-ups to improve patient flow and reduce scheduling congestion.
4. Ensure sufficient staffing, equipment availability, and optimized scheduling capacity for X-ray services to support consistent demand and protect high-revenue operations.

These adjustments directly target the highest-impact inefficiencies in the scheduling system, improving appointment utilization, strengthening revenue capture, and increasing overall operational efficiency.

### Next Steps
1. A/B test different patient reminder strategies (timing, frequency, and messaging tone) to determine which most effectively reduces appointment no-show rates.
2. Pilot automated confirmation and self-scheduling features to evaluate impact on appointment utilization and cancellation recovery.
3. Collaborate with operational staff to refine scheduling rules and validate feasibility of dedicated check-up time blocks.
4. Track changes in no-show rate and X-ray utilization over time to assess whether scheduling and engagement improvements translate into operational and revenue gains.

### How this Github project is organized:
This project is organized into chapters starting with an overview of the data (i.e. Chapter 1: Core KPIs) and then goes on to evaluate different categories of the data (Chapter 2: Dcotors, Chapter 3: Patients etc.). In these sections, I provide the SQL queries I used and provide explanation of the queries. Finally, I end the project with insights derived from the analysis and recommendations to the hospital this is labeled as "Chapter 5: Final Insights and Recommendations".

Data source: [Hospital Management Dataset](https://www.kaggle.com/datasets/kanakbaghel/hospital-management-dataset)

** To be added. 
