## 1 - View student’s email, name and gender (by this order)

```sql
SELECT stu_email, stu_name, stu_gender
FROM student
```

## 2 - Repeat the previous query change the stu_name header to “Full Name”

```sql
SELECT stu_email, stu_name "Full Name", stu_gender
FROM student
```

## 3 - Get all student numbers and apply the formula: stu_id\*1000+stu_cour_id

```sql
SELECT stu_id*1000+stu_cour_id "number", stu_name "Full Name"
FROM student
```

## 4 - Build this sentence for all the students: “The student stu_name is enrolled in the course stu_cour_id”

```sql
SELECT concat("The student ", stu_name, " is enrolled in the course ", stu_cour_id) "sentence"
FROM student
```

## 5 - Display student’s location and gender (without duplicates)

```sql
SELECT DISTINCT stu_place, stu_gender
FROM student
```

## 6 - View all the students ordered by: date of birth (descending)

```sql
SELECT *
FROM student
ORDER BY stu_bdate DESC
```

## 7 - View all the students ordered by: gender (ascending) and name (descending)

```sql
SELECT *
FROM student
ORDER BY stu_gender ASC, stu_name DESC
```

## 8 - View only the student name and email but ordered by date of birth

```sql
SELECT stu_name, stu_email
FROM student
ORDER BY stu_bdate ASC
```

## 9 - Using the same formula as in question 3 show name and number, ordered by that formula

```sql
SELECT stu_id*1000+stu_cour_id "num", stu_name
FROM student
ORDER BY stu_id*1000+stu_cour_id DESC
```

## 10 - Show only female students (gender = ‘F’)

```sql
SELECT * FROM student
WHERE stu_gender = "F"
```

## 11 - Show all the students born between 1996 and 1998

```sql
SELECT *
FROM student
WHERE stu_bdate >= "1996-01-01" <= "1998-12-31"
```

## 12 - Show all the students born before 1996 or that are enrolled in course 2

```sql
SELECT *
FROM student
WHERE stu_bdate < "1996-01-01" OR stu_cour_id = 2
```

## 13 - View male students from course 1 and female students from course 2

```sql
SELECT *
FROM student
WHERE (stu_gender = "M" AND stu_cour_id = 1) OR (stu_gender = "F" and stu_cour_id = 2)
```

## 14 - Show students born between 1996 and 1998 that are from courses 1, 2 or 4

```sql
SELECT *
FROM student
WHERE (stu_bdate BETWEEN "1996-01-01" AND "1998-12-01") AND stu_cour_id IN (1,2,4)
```

## 15 - Show students that were not born between 1996 and 1998

```sql
SELECT *
FROM student
WHERE stu_bdate NOT BETWEEN "1996-01-01" AND "1998-12-01"
```

## 16 - Show students whose name starts by letter J

```sql
SELECT *
FROM student
WHERE stu_name LIKE ("J%")
```

## 17 - Show students whose last name contains 5 letters

```sql
SELECT *
FROM student
WHERE stu_name LIKE ("% _____")
```

## 18 - Show students with an email account from sapo

```sql
SELECT *
FROM student
WHERE stu_email LIKE ("%sapo.pt")
```

## 19 - Show students with the address attribute

not filled.

```sql
SELECT *
FROM student
WHERE stu_place IS NULL
```
