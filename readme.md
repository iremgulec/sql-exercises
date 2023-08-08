# Unfinished Parts [Tesla SQL Interview Question]
https://datalemur.com/questions/tesla-unfinished-parts

```
SELECT
part, 
assembly_step 
FROM parts_assembly
WHERE finish_date IS NULL;
```
# Pharmacy Analytics (Part 1)[CVS Health SQL Interview Question]
https://datalemur.com/questions/top-profitable-drugs

```
SELECT 
drug,
(total_sales-cogs) as total_profit
FROM pharmacy_sales
ORDER BY total_profit DESC LIMIT 3;
```

# Pharmacy Analytics (Part 2)[CVS Health SQL Interview Question]
https://datalemur.com/questions/non-profitable-drugs

```
SELECT
  manufacturer,
  COUNT(drug) AS drug_count,
  ABS(SUM(total_sales - cogs)) AS total_loss
FROM pharmacy_sales
WHERE total_sales - cogs <= 0
GROUP BY manufacturer
ORDER BY total_loss DESC;
```
# Pharmacy Analytics (Part 3)[CVS Health SQL Interview Question]
https://datalemur.com/questions/total-drugs-sales

```
SELECT 
manufacturer,
CONCAT('$', ROUND(SUM(total_sales)/1000000), ' million') AS sale
FROM pharmacy_sales
GROUP BY manufacturer
ORDER BY SUM(total_sales) DESC;
```
# Amazon Highest Cost Orders 
https://platform.stratascratch.com/coding/9915-highest-cost-orders?code_type=1

```
select a.first_name, 
sum(b.total_order_cost), 
b.order_date 
FROM customers a
INNER JOIN orders b on a.id = b. cust_id
WHERE b.order_date between  '2019-02-01' AND '2019-05-01'
GROUP BY b.cust_id,b.order_date 
ORDER BY sum(b.total_order_cost) DESC LIMIT 1 ;
```

# Highest Salary In Department
https://platform.stratascratch.com/coding/9897-highest-salary-in-department?code_type=1

```
SELECT
  department,
  first_name AS employee_name,
  salary
FROM
  (SELECT
  department,
first_name,
  salary, 
  ROW_NUMBER() OVER(PARTITION BY department ORDER BY salary DESC) as rn
FROM employee) 
AS subquery
WHERE rn=1
```



# Highest Target Under Manager
https://platform.stratascratch.com/coding/9905-highest-target-under-manager?code_type=1

```
SELECT 
first_name, 
 target 
FROM salesforce_employees
WHERE target IN
    (SELECT MAX(target) 
    from salesforce_employees WHERE manager_id=13) 
    AND manager_id = 13
```

