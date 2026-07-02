# REVIEWER 1 - SAMPLE QUERIES

1. CREATE TABLE QuarantineLog (
  log_id INT PRIMARY KEY NOT NULL,
  quarantine_reason VARCHAR(100) NOT NULL
);
3. INSERT INTO Athletes (athlete_id, full_name, university) VALUES ('ATH-21','Simon Jones','Yale University');
4. ALTER TABLE Vessels ADD COLUMN gross_tonnage INT NOT NULL;
5. ALTER TABLE Athletes DROP COLUMN academic_year;
6. UPDATE SportsEvents SET status = 'Postponed' WHERE event_id = 'EVT-05';
7. SELECT athlete_id, award_count * 1.1 AS amplified_awards FROM Athletes;
8. SELECT * FROM MedalStandings WHERE TIME(award_timestamp) > '18:00:00';
9. SELECT * FROM Athletes WHERE first_name REGEXP '^[A-D]';
10. SELECT * FROM Athletes WHERE university IN ('Harvard','Yale');
11. SELECT * FROM Athletes WHERE university NOT IN ('Curtis');
12. SELECT * FROM Athletes WHERE athlete_id <= 'ATH-03' ORDER BY athlete_id DESC;
13. SELECT SUM(weight_kg) as TotalYardWeight FROM CargoContainers;
14. SELECT declared_status, COUNT(*) as Status_Count from CustomsClearance GROUP BY declared_status;
15. SELECT shift_date, COUNT(worker_id) AS workers_scheduled from ShiftSchedules GROUP BY shift_date HAVING COUNT(worker_id) > 2;

