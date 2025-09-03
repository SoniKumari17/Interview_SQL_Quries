| emp\_id | emp\_name | dept\_id | salary |
| ------- | --------- | -------- | ------ |
| 1       | Soni      | 1        | 40000  |
| 2       | Sakshi    | 2        | 55000  |
| 3       | Ravi      | 1        | 30000  |
| 4       | Arjun     | 3        | 70000  |
| 5       | Priya     | 2        | 45000  |
| 6       | Anjali    | 1        | 60000  |
| 7       | Raj       | 3        | 50000  |
Find all employees sorted by salary in ascending order.
```sql 
SELECT emp_name, salary
FROM Employee
ORDER BY salary ASC;
```
| emp\_name | salary |
| --------- | ------ |
| Ravi      | 30000  |
| Soni      | 40000  |
| Priya     | 45000  |
| Raj       | 50000  |
| Sakshi    | 55000  |
| Anjali    | 60000  |
| Arjun     | 70000  |
SELECT emp_name, salary
FROM Employee
ORDER BY salary DESC;
| emp\_name | salary |
| --------- | ------ |
| Arjun     | 70000  |
| Anjali    | 60000  |
| Sakshi    | 55000  |
| Raj       | 50000  |
| Priya     | 45000  |
| Soni      | 40000  |
| Ravi      | 30000  |
Q4. Orders sorted by order_date (newest first)

Dummy Orders Table
| order\_id | order\_date |
| --------- | ----------- |
| 101       | 2023-07-20  |
| 102       | 2023-08-01  |
| 103       | 2023-06-15  |
| 104       | 2023-07-25  |
SELECT order_id, order_date
FROM Orders
ORDER BY order_date DESC;
| order\_id | order\_date |
| --------- | ----------- |
| 102       | 2023-08-01  |
| 104       | 2023-07-25  |
| 101       | 2023-07-20  |
| 103       | 2023-06-15  |

Q5. Employees sorted by dept_id ascending, salary descending
SELECT emp_name, dept_id, salary
FROM Employee
ORDER BY dept_id ASC, salary DESC;
| emp\_name | dept\_id | salary |
| --------- | -------- | ------ |
| Anjali    | 1        | 60000  |
| Soni      | 1        | 40000  |
| Ravi      | 1        | 30000  |
| Sakshi    | 2        | 55000  |
| Priya     | 2        | 45000  |
| Arjun     | 3        | 70000  |
| Raj       | 3        | 50000  |
Q6. Products sorted by price, then product_name

Dummy Products Table
| product\_name | price |
| ------------- | ----- |
| Apple         | 50    |
| Banana        | 30    |
| Avocado       | 50    |
| Mango         | 40    |
| Grapes        | 30    |
SELECT product_name, price
FROM Products
ORDER BY price ASC, product_name ASC;
| product\_name | price |
| ------------- | ----- |
| Banana        | 30    |
| Grapes        | 30    |
| Mango         | 40    |
| Apple         | 50    |
| Avocado       | 50    |
Q7. Top 3 highest salaries
SELECT emp_name, salary
FROM Employee
ORDER BY salary DESC
LIMIT 3;
| emp\_name | salary |
| --------- | ------ |
| Arjun     | 70000  |
| Anjali    | 60000  |
| Sakshi    | 55000  |


#### 1️⃣ Sorting by Expressions

SQL me sirf column ke values hi nahi, calculated expressions pe bhi sorting kar sakte ho.

Expression ka matlab hai koi formula ya calculation, jaise price * 1.1.

#### Example Table: Products
| product\_name | price |
| ------------- | ----- |
| Apple         | 50    |
| Mango         | 40    |
| Banana        | 30    |

```sql
SELECT product_name, price, price * 1.1 AS discounted_price
FROM Products
ORDER BY discounted_price;
````
Explanation:

price * 1.1 calculate karta hai 10% extra (discounted price ke liye)

ORDER BY discounted_price se ye calculated column ke basis pe sorting hoti hai

#### Output (ascending):
2️⃣ Sorting NULL Values

By default:

ASC → NULLs smallest → appear first

DESC → NULLs largest → appear last

Agar chaho to control kar sakte ho with NULLS FIRST ya NULLS LAST.

Example Table: Students

| student\_name | marks |
| ------------- | ----- |
| Rohit         | 85    |
| Priya         | NULL  |
| SoniK         | 90    |
| Arjun         | NULL  |

SELECT student_name, marks
FROM Students
ORDER BY marks ASC NULLS LAST;

| student\_name | marks |
| ------------- | ----- |
| Rohit         | 85    |
| SoniK         | 90    |
| Priya         | NULL  |
| Arjun         | NULL  |

SELECT student_name, marks
FROM Students
ORDER BY marks DESC NULLS FIRST;

| student\_name | marks |
| ------------- | ----- |
| Priya         | NULL  |
| Arjun         | NULL  |
| SoniK         | 90    |
| Rohit         | 85    |

3️⃣ Sorting by Column Position

Agar column name ya expression likhna na ho, SQL me column number bhi use karke sort kar sakte ho.

Column positions start hoti hain 1 se (leftmost column = 1, next = 2, etc.)

Example Table: Products
| product\_name | price |
| ------------- | ----- |
| Apple         | 50    |
| Mango         | 40    |
| Banana        | 30    |

SELECT product_name, price
FROM Products
ORDER BY 2 DESC, 1 ASC;

Explanation:

2 DESC → 2nd column (price) descending

1 ASC → 1st column (product_name) ascending, agar prices same ho

| product\_name | price |
| ------------- | ----- |
| Apple         | 50    |
| Mango         | 40    |
| Banana        | 30    |
