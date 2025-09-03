Employees Table

| emp\_id | emp\_name | dept    | salary |
| ------- | --------- | ------- | ------ |
| 1       | Soni      | HR      | 40000  |
| 2       | Ravi      | IT      | 50000  |
| 3       | Priya     | HR      | 45000  |
| 4       | Arjun     | IT      | 55000  |
| 5       | Sakshi    | Finance | 60000  |
| 6       | Anjali    | IT      | 52000  |
| 7       | Raj       | HR      | 43000  |
Query: Count total employees

SELECT COUNT(*) AS total_employees
FROM Employees;


Output:

total_employees
7

Query: Count employees in each department

SELECT dept, COUNT(*) AS total_employees
FROM Employees
GROUP BY dept;

2️⃣ SUM() – Sum of numeric column

Query: Total salary of all employees

SELECT SUM(salary) AS total_salary
FROM Employees;

Query: Total salary per department

SELECT dept, SUM(salary) AS dept_salary
FROM Employees
GROUP BY dept;

3️⃣ AVG() – Average of numeric column

Query: Average salary of all employees

SELECT AVG(salary) AS avg_salary
FROM Employees;
| avg\_salary |
| ----------- |
| 50714.29    |

Query: Average salary per department

SELECT dept, AVG(salary) AS avg_salary
FROM Employees
GROUP BY dept;
| dept    | avg\_salary |
| ------- | ----------- |
| HR      | 42666.67    |
| IT      | 52333.33    |
| Finance | 60000       |

4️⃣ MAX() – Maximum value

Query: Highest salary in the company

SELECT MAX(salary) AS highest_salary
FROM Employees;
| highest\_salary |
| --------------- |
| 60000           |

Query: Highest salary per department

SELECT dept, MAX(salary) AS max_salary
FROM Employees

| dept    | max\_salary |
| ------- | ----------- |
| HR      | 45000       |
| IT      | 55000       |
| Finance | 60000       |


GROUP BY dept;
| dept    | max\_salary |
| ------- | ----------- |
| HR      | 45000       |
| IT      | 55000       |
| Finance | 60000       |

| highest\_salary |
| --------------- |
| 60000           |

5️⃣ MIN() – Minimum value

Query: Lowest salary in the company

SELECT MIN(salary) AS lowest_salary
FROM Employees;
| lowest\_salary |
| -------------- |
| 40000          |

Query: Lowest salary per department

SELECT dept, MIN(salary) AS min_salary
FROM Employees
GROUP BY dept;
| dept    | min\_salary |
| ------- | ----------- |
| HR      | 40000       |
| IT      | 50000       |
| Finance | 60000       |
