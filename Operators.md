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
