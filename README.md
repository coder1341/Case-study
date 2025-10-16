1. Number of hospital visits per day over the period 
SELECT 
    DATE(created_at) AS visit_date,
    COUNT(*) AS number_of_visits
FROM hospital_visits
GROUP BY DATE(created_at)
ORDER BY visit_date;
2. Number of patients attended to per doctor per month showing their names
   SELECT
    d.doctor_name,
    DATE_TRUNC('month', v.created_at) AS month,
    COUNT(DISTINCT v.patient_id) AS number_of_patients
FROM hospital_visits v
JOIN doctors d
    ON v.doctor_id = d.doctor_id
GROUP BY d.doctor_name, DATE_TRUNC('month', v.created_at)
ORDER BY d.doctor_name, month;
