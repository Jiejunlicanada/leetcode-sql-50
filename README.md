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
