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
