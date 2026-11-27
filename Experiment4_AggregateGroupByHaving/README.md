# Experiment 4: Aggregate Functions, Group By and Having Clause
## NAME: N V MOHANA KRISHNA
## REG NO: 212224100039

## AIM
To study and implement aggregate functions, GROUP BY, and HAVING clause with suitable examples.

## THEORY

### Aggregate Functions
These perform calculations on a set of values and return a single value.

- **MIN()** – Smallest value  
- **MAX()** – Largest value  
- **COUNT()** – Number of rows  
- **SUM()** – Total of values  
- **AVG()** – Average of values

**Syntax:**
```sql
SELECT AGG_FUNC(column_name) FROM table_name WHERE condition;
```
### GROUP BY
Groups records with the same values in specified columns.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name;
```
### HAVING
Filters the grouped records based on aggregate conditions.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
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

<img width="1227" height="842" alt="image" src="https://github.com/user-attachments/assets/3ec42b2f-f0d5-4c1b-918e-505ced79f0f3" />



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

<img width="1230" height="397" alt="image" src="https://github.com/user-attachments/assets/08979e18-4b40-4d12-a9c7-b6a303817f72" />


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

<img width="1236" height="613" alt="image" src="https://github.com/user-attachments/assets/44a193ae-06e9-43c9-984e-4bdca9803b21" />


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

<img width="1222" height="398" alt="image" src="https://github.com/user-attachments/assets/a7941e57-3900-4e4c-97f9-7d7627eae104" />



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
<img width="1237" height="402" alt="image" src="https://github.com/user-attachments/assets/c64b8958-52fa-4d41-b06e-da96f797d5ba" />



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

<img width="1235" height="396" alt="image" src="https://github.com/user-attachments/assets/77c8fe7c-1a7d-4702-abef-25e3eec5f41c" />



**Question 7**
```
Write a SQL query to return the total number of rows in the 'customer' table where the city is Noida.

Sample table: customer



 

For example:

Result
COUNT
----------
1

```

```
SELECT COUNT(*) AS COUNT
FROM customer
WHERE city = 'Noida';
```

**Output:**

<img width="1232" height="400" alt="image" src="https://github.com/user-attachments/assets/a110e3c0-8b51-4263-91a6-1a81f7813586" />



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

<img width="1237" height="690" alt="image" src="https://github.com/user-attachments/assets/1f442d26-0b6e-407b-a0c4-87c2f4f990fb" />



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

<img width="1235" height="462" alt="image" src="https://github.com/user-attachments/assets/0be3762e-5975-4b80-bb88-eedfa457e2fc" />



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

<img width="1227" height="422" alt="image" src="https://github.com/user-attachments/assets/4032aee6-9166-4133-b929-4be3dc80d41f" />



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
