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
