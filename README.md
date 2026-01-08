SQL 50
1978. Employees whose manager left the company 

select employee_id
from employees
where manager_id not in (select employee_id from employees)
