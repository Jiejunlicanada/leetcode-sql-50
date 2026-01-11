SQL 50
1978. Employees whose manager left the company 

select employee_id
from employees
where manager_id not in (select employee_id from employees)


626.Exchange seat


select case when id%2=1 and id+1 in(select id from seat) then id+1 
    when id%2=0 then id-1
    else id
    end as id,student 
from seat
order by id


1907. Count Salary Categories


SELECT 'Low Salary' AS category,
       COUNT(*)     AS accounts_count
FROM Accounts
WHERE income < 20000

UNION ALL

SELECT 'Average Salary' AS category,
       COUNT(*)         AS accounts_count
FROM Accounts
WHERE income BETWEEN 20000 AND 50000

UNION ALL

SELECT 'High Salary' AS category,
       COUNT(*)       AS accounts_count
FROM Accounts
WHERE income > 50000;




1731.The Number of Employees Which Report to Each Employee

select e.employee_id,e.name,count(e1.employee_id )as reports_count,round(avg(e1.age)) as average_age 
from employees e join employees e1
on e.employee_id  = e1.reports_to 
group by employee_id ,name    


1405.Customers who bought all the products

select customer_id from customer
group by customer_id
having count(product_key)=2



1729.Find Followers Count

select user_id,count(*)as followers_count
from Followers  
group by user_id;



596.Classes with at least 5 students

select class
from courses
group by class
having count(*) >= 5;
