#### Q1. Find all employees whose name starts with 'A'.
```sql
SELECT emp_name 
FROM Employee 
WHERE emp_name LIKE 'A%';
```
#### Q2. Find all employees whose name ends with 'n'.
````sql
SELECT emp_name 
FROM Employee 
WHERE emp_name LIKE '%n';
Example Matches: Arun, Kiran
````
#### Q3. Find all employees whose name contains 'sh' anywhere.
```sql
SELECT emp_name 
FROM Employee 
WHERE emp_name LIKE '%sh%';
Example Matches: Suresh, Ashok
````
#### Q4. Find all employees whose name is exactly 5 letters long and starts with 'S'.
````sql
SELECT emp_name 
FROM Employee 
WHERE emp_name LIKE 'S____';
Example Matches: SoniK, Sonam
(Each _ = exactly one character)
````
#### Q5. Find all products whose name starts with 'A' and ends with 'e'.
```sql
SELECT product_name 
FROM Products 
WHERE product_name LIKE 'A%e';
Example Matches: Apple, Axe
````
#### Q6. Find all customers whose phone number contains '999'.
```sql
SELECT customer_name 
FROM Customer 
WHERE phone LIKE '%999%';
````
## IN OPERATOR
#### Q1.Find all employees who work in departments 1, 3, or 5.
```sql
SELECT emp_name 
FROM Employee 
WHERE dept_id IN (1, 3, 5);
```
#### Q2.Find all customers whose names are either 'Soni', 'Sakshi', or 'Ravi'.
```sql
SELECT name 
FROM Customer 
WHERE name IN ('Soni', 'Sakshi', 'Ravi');
````
#### Q3.Find all products whose price is either 100, 200, or 500.
```sql
SELECT product_name 
FROM Products 
WHERE price IN (100, 200, 500);
```
#### Q4.Find students who are in the CS or IT branch.
```sql
SELECT student_name 
FROM Students 
WHERE branch IN ('CS', 'IT');
```
#### Q5.Find orders placed by customers with id 2, 4, or 6.
```sql
SELECT order_id 
FROM Orders 
WHERE customer_id IN (2, 4, 6);
```
### (Nested IN)

#### Q6.Find employees who belong to departments where location = 'Delhi'.
```sql
SELECT emp_name 
FROM Employee 
WHERE dept_id IN (
    SELECT dept_id 
    FROM Department 
    WHERE location = 'Delhi'
);
````
#### Q7.Find employees who are NOT in departments 2 or 4.
```sql
SELECT emp_name 
FROM Employee 
WHERE dept_id NOT IN (2, 4);
```
#### Q8.Find all users whose email provider is either gmail.com, yahoo.com, or outlook.com.
```sql
SELECT email 
FROM Users 
WHERE email LIKE '%@gmail.com'
   OR email LIKE '%@yahoo.com'
   OR email LIKE '%@outlook.com';
```
##### Using IN with functions:
```sql
SELECT email 
FROM Users 
WHERE RIGHT(email, 9) IN ('@gmail.com', '@yahoo.com', '@outlook.com');
````
##### IN is short for multiple OR.
##### WHERE dept_id IN (1, 2, 3) = WHERE dept_id = 1 OR dept_id = 2 OR dept_id = 3.

## Between Operator


| emp_id | emp_name | dept_id | salary  | join_date  |
|--------|----------|---------|---------|------------|
| 1      | Soni     | 1       | 40000   | 2023-01-10 |
| 2      | Sakshi   | 2       | 55000   | 2023-06-15 |
| 3      | Ravi     | 1       | 30000   | 2023-03-20 |
| 4      | Arjun    | 3       | 70000   | 2024-01-05 |
| 5      | Priya    | 2       | 45000   | 2023-11-25 |
| 6      | Anjali   | 1       | 60000   | 2024-02-18 |
| 7      | Raj      | 3       | 50000   | 2023-08-30 |

### Q1. Employees with salary between 40000 and 50000
```sql
SELECT emp_name, salary
FROM Employee
WHERE salary BETWEEN 40000 AND 50000;
```
| emp\_name | salary |
| --------- | ------ |
| Soni      | 40000  |
| Priya     | 45000  |
| Raj       | 50000  |

#### Q2. Employees who joined between 2023-06-01 and 2023-12-31
```sql
SELECT emp_name, join_date
FROM Employee
WHERE join_date BETWEEN '2023-06-01' AND '2023-12-31';
```
| emp\_name | join\_date |
| --------- | ---------- |
| Sakshi    | 2023-06-15 |
| Priya     | 2023-11-25 |
| Raj       | 2023-08-30 |

#### Q3. Employees NOT having salary between 40000 and 60000
```sql
SELECT emp_name, salary
FROM Employee
WHERE salary NOT BETWEEN 40000 AND 60000;
```
| emp\_name | salary |
| --------- | ------ |
| Ravi      | 30000  |
| Arjun     | 70000  |


BETWEEN includes both ends (inclusive).
Equivalent to:
```sql
column BETWEEN a AND b
-- same as
column >= a AND column <= b
```
### Null
Basics

IS NULL → check karta hai ki column me NULL value hai ya nahi.

IS NOT NULL → check karta hai ki column me NULL value nahi hai.
⚠️ Important: = NULL kaam nahi karega, hamesha IS NULL use karna hai.

Basics

## Column alias:

SELECT column_name AS alias_name
FROM table_name;


Output me column ka naam alias_name ho jata hai.

Table alias:

SELECT t.column_name
FROM table_name AS t;


Table ko short name (alias) diya → easier join aur query likhna.

## 🔹 Practice Questions
#### Q1. Column alias
##### Find all employees and rename the emp_name column as Employee.
```sql
SELECT emp_name AS Employee
FROM Employee;
```
#### Q2. Column alias with calculation
##### Find all employees and display salary + bonus as Total_Pay.
```sql
SELECT emp_name, (salary + bonus) AS Total_Pay
FROM Employee;
```
#### Q3. Table alias
##### Find all employees from Department 1, using table alias e.
```sql
SELECT e.emp_name, e.salary
FROM Employee AS e
WHERE e.dept_id = 1;
```
#### Q4. Join with table alias
##### Get all employees and their department names. Use alias e for Employee, d for Department.
```sql
SELECT e.emp_name, d.dept_name
FROM Employee AS e
JOIN Department AS d
ON e.dept_id = d.dept_id;
```
#### Q5. Column alias with aggregate
##### Count number of employees in each department and show as Total_Employees.
```sql
SELECT dept_id, COUNT(*) AS Total_Employees
FROM Employee
GROUP BY dept_id;
```
#### Q6. Multiple aliases
##### Find all employees and show salary as Salary, bonus as Bonus, total as Total_Pay.
```sql
SELECT emp_name AS Employee, salary AS Salary, bonus AS Bonus, (salary+bonus) AS Total_Pay
FROM Employee;
````
##### 🔹 Quick Tips for Interview

Column alias → AS alias_name

Optional AS bhi likh sakte ho: SELECT emp_name Employee

But AS makes it clearer.

Table alias → FROM table_name AS t

Especially useful in joins or self-joins.

Aliases do not change actual table/column names, sirf query ke result me show hota hai.
