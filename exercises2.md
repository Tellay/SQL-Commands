## 1 - Use the select command to view the current date

```sql
SELECT now()
```

## 2 - Display the current date using the format ‘DD-MM-YYYY’

```sql
SELECT date_format(now(), "%d/%m/%Y")
```

## 3 - Show current time in the format 'HH24:MI:SS'

```sql
SELECT date_format(now(), "%H:%I:%S")
```

## 4 - Show students with their birthdate in the format ’January,12 of 1998’

```sql
SELECT stu_name, date_format(stu_bdate, "%M, %d of %Y")
FROM student
```

## 5 - Display students that were born in 1994 (regardless of the date format on the server)

```sql
SELECT *
FROM student
WHERE date_format(stu_bdate, "%Y") = "1994"
```

## 6 - Display students born after 1-1-1997 (regardless of the date format on the server)

```sql
SELECT *
FROM student
WHERE date_format(stu_bdate, "%Y-%m-%d") > "1997-01-01"
```

## 7 - Display student’s name in capital letters

```sql
SELECT upper(stu_name), stu_place, stu_email
FROM student
```

## 8 - Display student’s name in lowercase

```sql
SELECT lower(stu_name), stu_place, stu_email
FROM student
```

## 9 - Display students whose first name is João (regardless of uppercase or lowercase letters)

```sql
SELECT *
FROM student
WHERE lower(stu_name) LIKE ("joão %")
```

## 10 - Display the student’s email, and if student doesn’t have email, show ‘no email available’

```sql
SELECT stu_name, ifnull(stu_email, "no email available")
FROM student
```

## 11 - Display student names and their courses knowing that : 1 - GAD, 2 - GD, 3 - CT, 4 - PH

```sql
SELECT stu_name,
	CASE
	    WHEN stu_cour_id = 1 THEN "GAD"
        WHEN stu_cour_id = 2 THEN "GD"
        WHEN stu_cour_id = 3 THEN "CT"
        WHEN stu_cour_id = 4 THEN "PH"
    END curso
FROM student
```

## 12 - Replace ‘ã’ or ‘Ã’ characters to ‘A’ in student’s name

```sql
SELECT stu_name, replace(upper(stu_name), "Ã", "A") nome, replace(stu_name, lower("ã"), "A") nome
FROM student
```

## 13 - Display the first 3 letters of the student’s name using the substr function

```sql
SELECT substr(stu_name, 1, 3) nome, stu_name
FROM student
```

## 14 - Calculate student’s age. (you will need age and extract functions)

```sql
SELECT stu_name, stu_bdate, timestampdiff(YEAR, stu_bdate, now()) Age
FROM student
```

## 15 - Display the students that are more than 27 years old

```sql
SELECT stu_name, stu_bdate, timestampdiff(YEAR, stu_bdate, now()) Age
FROM student
WHERE timestampdiff(YEAR, stu_bdate, now()) > 27
```
