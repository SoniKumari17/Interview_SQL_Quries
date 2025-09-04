### Replace Employee Id With Unique Identifier
```sql
select name , unique_id 
from Employees left join EmployeeUNI
on Employees.id = EmployeeUNI.id;
```
### Product Analysis 1
```sql
select year ,price, product_name
from Sales left join Product 
on Product.product_id = Sales.product_id;
```
### Customer Who Visited But Did Not Any Transaction
```sql
select v.customer_id, count(v.visit_id) as count_no_trans
from Visits v left join Transactions t 
on v.visit_id = t.visit_id
where t.visit_id is null 
group by v.customer_id;
```
### Rsing Temperater
```sql
SELECT w1.id
FROM Weather w1
JOIN Weather w2
  ON w1.recordDate = DATE_ADD(w2.recordDate, INTERVAL 1 DAY)
WHERE w1.temperature > w2.temperature;
```
### Not Boring Movies
```sql
select id ,movie,description,rating from Cinema
where id%2 != 0 and description != 'boring' 
order by rating desc;
```

### PROJECT EMPLOYEE 1
```sql
-- Project ke hisaab se employees ka average experience nikalna
SELECT 
    p.project_id,                          -- project id
    ROUND(AVG(e.experience_years), 2) AS average_years  -- 2 decimal tak average
FROM Project AS p
LEFT JOIN Employee AS e                   -- Project aur Employee ko join karna
    ON p.employee_id = e.employee_id      -- join condition: dono ka employee_id match
GROUP BY p.project_id;                    -- har project ke liye ek result row
```
### Average Selling Price
```sql
# Write your MySQL query statement below
SELECT 
    p.product_id,
    ROUND(
        IFNULL(SUM(u.units * p.price) / SUM(u.units), 0),
        2
    ) AS average_price
FROM Prices p
LEFT JOIN UnitsSold u
    ON p.product_id = u.product_id
   AND u.purchase_date BETWEEN p.start_date AND p.end_date
GROUP BY p.product_id;
```
### Number Of Unique Subjetcs Taught By Each Teacher
```sql
select teacher_id,count(distinct subject_id) as cnt from Teacher
group by teacher_id;
```
