# Experiment 3: DML Commands
## NAME: N V MOHANA KRISHNA
# REG NO: 212224100039

## AIM
To study and implement DML (Data Manipulation Language) commands.

## THEORY

### 1. INSERT INTO
Used to add records into a relation.
These are three type of INSERT INTO queries which are as
A)Inserting a single record
**Syntax (Single Row):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES (value_1, value_2, ...);
```
**Syntax (Multiple Rows):**
```sql
INSERT INTO table_name (field_1, field_2, ...) VALUES
(value_1, value_2, ...),
(value_3, value_4, ...);
```
**Syntax (Insert from another table):**
```sql
INSERT INTO table_name SELECT * FROM other_table WHERE condition;
```
### 2. UPDATE
Used to modify records in a relation.
Syntax:
```sql
UPDATE table_name SET column1 = value1, column2 = value2 WHERE condition;
```
### 3. DELETE
Used to delete records from a relation.
**Syntax (All rows):**
```sql
DELETE FROM table_name;
```
**Syntax (Specific condition):**
```sql
DELETE FROM table_name WHERE condition;
```
### 4. SELECT
Used to retrieve records from a table.
**Syntax:**
```sql
SELECT column1, column2 FROM table_name WHERE condition;
```
**Question 1**
```
How many patients have expired insurance coverage for each insurance company?

Sample table:Insurance Table



For example:

Result
InsuranceCompany  TotalExpiredPatients
----------------  --------------------
ABC Insurance     1
DEF Insurance     1
GHI Insurance     1
JKL Insurance     1
MNO Insurance     1
PQR Insurance     1
STU Insurance     1
VWX Insurance     1
XYZ Insurance     1
YZA Insurance     1

```

```
SELECT InsuranceCompany,COUNT(PatientID) AS TotalExpiredPatients
FROM Insurance
GROUP BY InsuranceCompany;
```

**Output:**

<img width="1236" height="875" alt="image" src="https://github.com/user-attachments/assets/973f5f9b-7be2-422a-b9f4-f9992b1b65a2" />


**Question 2**
```
What is the most common diagnosis among patients?

Sample table:MedicalRecords Table



For example:

Result
Diagnosis              DiagnosisCount
---------------------  --------------
Childhood vaccination  3

```

```
SELECT
    Diagnosis,
    COUNT(*) AS DiagnosisCount
FROM 
    MedicalRecords
GROUP BY 
    Diagnosis
ORDER BY
    DiagnosisCount DESC
LIMIT 1;
```

**Output:**

<img width="1237" height="430" alt="image" src="https://github.com/user-attachments/assets/52d637ce-d770-4111-9f23-f202593be6f4" />

**Question 3**
```
How many prescriptions were written in each frequency category (e.g., once daily, twice daily)?

Sample tablePrescriptions Table



For example:

Result
Frequency      TotalPrescriptions
-------------  ------------------
Every 3 weeks  1
Every 6 hours  1
Once           1
Once daily     4
Once daily at  1
Pending        1
Twice daily    1


```

```
select frequency, count(prescriptionid) as TotalPrescriptions from prescriptions group by frequency;
```

**Output:**

<img width="1243" height="655" alt="image" src="https://github.com/user-attachments/assets/ed1be5f9-71e8-4851-97b3-ffc684defee2" />



**Question 4**

```
Write a SQL query to find the minimum purchase amount.

Sample table: orders

ord_no      purch_amt   ord_date    customer_id  salesman_id

----------  ----------  ----------  -----------  -----------

70001       150.5       2012-10-05  3005         5002

70009       270.65      2012-09-10  3001         5005

70002       65.26       2012-10-05  3002         5001

 

For example:

Result
MINIMUM
----------
65.26


```
```
select min(purch_amt) as MINIMUM
from orders;
```

**Output:**

<img width="1235" height="431" alt="image" src="https://github.com/user-attachments/assets/5c7acd34-c905-4389-b03c-b565b00c1033" />



**Question 5**
```
Write a SQL query to find Who has the highest income among employee living in California?

Table: employee

name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER
For example:

Result
name        max(income)
----------  -----------
Adam        5000000


```

```
SELECT name, max(income)
FROM employee
WHERE city = 'California';
```

**Output:**

<img width="1237" height="437" alt="image" src="https://github.com/user-attachments/assets/e1a5af47-5bf5-43a6-954d-18896d22015c" />


**Question 6**
```
Write a SQL query to find the average length of email addresses (in characters):

Table: customer

name        type
----------  ----------
id          INTEGER
name        TEXT
city        TEXT
email       TEXT
phone       INTEGER
For example:

Result
avg_email_length
----------------
15.0

```

```
SELECT AVG(LENGTH(email)) AS avg_email_length
FROM customer;
```

**Output:**

<img width="1237" height="432" alt="image" src="https://github.com/user-attachments/assets/30a316ea-3ae5-49b1-aa79-63b508f321ad" />

**Question 7**
---
Write a SQL query to return the total number of rows in the 'customer' table where the city is Noida.

Sample table: customer



 

For example:

Result
COUNT
----------
1


```
SELECT COUNT(*) AS COUNT
FROM customer
WHERE city = 'Noida';
```

**Output:**

<img width="1238" height="428" alt="image" src="https://github.com/user-attachments/assets/ba1045b4-3d51-467f-ae23-e788d452836d" />



**Question 8**
```
Which cities (addresses) in the "customer1" table have an average salary lesser than Rs. 15000

Sample table: customer1



For example:

Result
address     AVG(salary)
----------  -----------
Ahmedabad   2000.0
Bhopal      8500.0
Delhi       1500.0
Hyderabad   4500.0
Indore      10000.0
Kota        2000.0
Mumbai      6500.0

```

```
SELECT address, AVG(salary)
FROM customer1
GROUP BY address
HAVING AVG(salary) < 15000;
```

**Output:**

<img width="1235" height="723" alt="image" src="https://github.com/user-attachments/assets/e4beea77-bb2c-4772-bcaf-3686b3109341" />



**Question 9**
```
Write the SQL query that accomplishes the grouping of data by joining date (jdate), calculates the total work hours for each date, and excludes dates where the total work hour sum is not greater than 40.

Sample table: employee1



For example:

Result
jdate       SUM(workhour)
----------  -------------
2004.0      46
2006.0      46

```

```
select jdate,SUM(workhour)
from employee1
group by jdate
having SUM(workhour)>40;
```

**Output:**


<img width="1233" height="503" alt="image" src="https://github.com/user-attachments/assets/9bba855c-bd10-4455-a00a-2d7e319b546c" />


**Question 10**
```
Write the SQL query to find how many patients have more than 3 medical records?.

Sample table: MedicalRecords

name        type
----------  ----------
RecordID    INTEGER
PatientID   INTEGER
DoctorID    INTEGER
Date        DATE
Diagnosis   TEXT
Treatment   TEXT
Medication  TEXT
For example:

Result
PatientID   TotalRecords
----------  ------------
1           4


```

```
SELECT PatientID, COUNT(RecordID) AS TotalRecords
FROM MedicalRecords
GROUP BY PatientID
HAVING COUNT(RecordID) > 3;
```

**Output:**


<img width="1242" height="451" alt="image" src="https://github.com/user-attachments/assets/0f9c99fd-5ff0-4035-a3ea-c23c3b0ec45f" />


## RESULT
Thus, the SQL queries to implement DML commands have been executed successfully.
