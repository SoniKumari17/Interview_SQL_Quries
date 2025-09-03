GROUP BY in SQL

The GROUP BY clause is used to group rows that have the same values in one or more columns.

It’s mostly used with aggregate functions like COUNT, SUM, AVG, MAX, MIN.
Example Table: Employees
| emp\_id | emp\_name | dept    | salary |
| ------- | --------- | ------- | ------ |
| 1       | Soni      | HR      | 40000  |
| 2       | Ravi      | IT      | 50000  |
| 3       | Priya     | HR      | 45000  |
| 4       | Arjun     | IT      | 55000  |
| 5       | Sakshi    | Finance | 60000  |

SELECT dept, AVG(salary) AS avg_salary
FROM Employees
GROUP BY dept;
Explanation:

GROUP BY dept → rows grouped by dept

AVG(salary) → calculates average salary for each department
| dept    | avg\_salary |
| ------- | ----------- |
| HR      | 42500       |
| IT      | 52500       |
| Finance | 60000       |
2️⃣ Grouping by Multiple Columns

Sometimes you want more detailed grouping.

Query:
SELECT dept, emp_name, salary
FROM Employees
GROUP BY dept, emp_name, salary;
Explanation:

Here, grouping is hierarchical: first by dept, then emp_name, then salary

Useful when you want to see unique combinations
3️⃣ Using HAVING with GROUP BY

WHERE filters rows before grouping

HAVING filters groups after aggregation

Example: Average salary > 50000

SELECT dept, AVG(salary) AS avg_salary
FROM Employees
GROUP BY dept
HAVING AVG(salary) > 50000;

| dept    | avg\_salary |
| ------- | ----------- |
| IT      | 52500       |
| Finance | 60000       |
✅ Only departments with average salary > 50000 are shown.
4️⃣ GROUP BY with ORDER BY

You can sort the grouped results using ORDER BY
SELECT dept, COUNT(*) AS total_employees
FROM Employees
GROUP BY dept
ORDER BY total_employees DESC;
| dept    | total\_employees |
| ------- | ---------------- |
| HR      | 2                |
| IT      | 2                |
| Finance | 1                |
5️⃣ Aggregate Functions with GROUP BY
| Function | Example         | Description             |
| -------- | --------------- | ----------------------- |
| COUNT    | `COUNT(emp_id)` | Number of rows in group |
| SUM      | `SUM(salary)`   | Total salary in group   |
| AVG      | `AVG(salary)`   | Average salary in group |
| MAX      | `MAX(salary)`   | Highest salary in group |
| MIN      | `MIN(salary)`   | Lowest salary in group  |

6️⃣ Practice Questions
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

Count employees in each department

SELECT dept, COUNT(*) AS total_employees
FROM Employees
GROUP BY dept;
| dept    | total\_employees |
| ------- | ---------------- |
| HR      | 3                |
| IT      | 3                |
| Finance | 1                |


Maximum salary in each department

SELECT dept, MAX(salary) AS max_salary
FROM Employees
GROUP BY dept;
| dept    | max\_salary |
| ------- | ----------- |
| HR      | 45000       |
| IT      | 55000       |
| Finance | 60000       |


Departments where average salary > 50000

SELECT dept, AVG(salary) AS avg_salary
FROM Employees
GROUP BY dept
HAVING AVG(salary) > 50000;
| dept    | avg\_salary |
| ------- | ----------- |
| IT      | 52333.33    |
| Finance | 60000       |


Count employees in each department and sort by count descending

SELECT dept, COUNT(*) AS total_employees
FROM Employees
GROUP BY dept
ORDER BY total_employees DESC;
| dept    | total\_employees |
| ------- | ---------------- |
| HR      | 3                |
| IT      | 3                |
| Finance | 1                |
