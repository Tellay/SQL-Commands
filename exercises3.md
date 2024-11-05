## 1 - How many students exist ?

```sql
SELECT count(*)
FROM student
```

## 2 - How many students exist, using the email ? (and why do we have this difference ?)

R: Because there are null values

```sql
SELECT count(stu_email)
FROM student
```

## 3 - How many different places exist?

```sql
SELECT count(distinct stu_place)
FROM student
```

## 4 - How many courses, with students, exist?

```sql
SELECT count(distinct stu_cour_id) "Courses with Students"
FROM student
```

## 5 - What is the higher student ID (stud_id)?

```sql
SELECT max(stu_id) "Highest Student ID"
FROM student
```

## 6 - What is the age of the youngest student? (regardless of the date format on the server)

```sql
SELECT min(timestampdiff(YEAR, stu_bdate, now())) "Age of youngest"
FROM student
```

## 7 - What is the average age of the students?

```sql
SELECT avg(timestampdiff(YEAR, stu_bdate, now())) "Average Age"
FROM student
```

## 8 - How many students have no email?

```sql
SELECT count(*) "Stundents without email"
FROM student
WHERE stu_email IS NULL
```

## 9 - How many male students are from Lisboa (don’t forget we have also lisboa)

```sql
SELECT count(*) "Male students from Lx"
FROM student
WHERE stu_gender = "M" AND stu_place = lower("lisboa")
```

## 10 - How many students do we have, by gender?

```sql
SELECT stu_gender, count(*)
FROM student
GROUP BY stu_gender
```

## 11 - How many students do we have, by location (place)? (lisboa …)

```sql
SELECT lower(stu_place), count(*)
FROM student
WHERE stu_place IS NOT NULL
GROUP BY stu_place
```

## 12 - How many students do we have, by course?

```sql
SELECT stu_cour_id, count(*)
FROM student
GROUP BY stu_cour_id
```

## 13 - How many students do we have, by year of birth?

```sql
SELECT year(stu_bdate), count(*)
FROM student
GROUP BY year(stu_bdate)
```

## 14 - The highest number of students we have in one single course? (only the number)

```sql
SELECT max(stu_cour_id)
FROM (
    SELECT stu_cour_id, count(stu_cour_id)
    FROM student
    GROUP BY stu_cour_id
) subquery;
```
