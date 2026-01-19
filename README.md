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



1633. Percentage of users attended a contest

select contest_id, round(count(distinct(user_id))*100/(select count(user_id) from users),2) as percentage 
from register
group by contest_id 
order by percentage desc;


550.Game play analysis IV

select round(count(distinct player_id )/(select count(distinct player_id ) from Activity),2) as fraction  
from Activity 
where (player_id, date_sub(event_date, interval 1 day) ) in
(select player_id,min(event_date)from activity);


1193.Monthly Transactions I 

select left(trans_date,7)as month,
       country,
       count(state) as trans_count,
       sum(state = "approved ") as approved_count,
       sum(amount) as trans_total_amount,
       sum((state = 'approved') * amount) as approved_total_amount
from 
    Transactions
group by 
    month, country;


1075.Project employees I

select p.project_id,avg(e.experience_years )as average_years 
from project p left join employee e
using(employee_id)
group by project_id;
