## Домашняя работа SQL №1
1. Вывести все поля и все строки
```
select * from qa_users;
```
2. Вывести всех студентов в таблице
```
select username from qa_users;
```
3. Вывести только Id пользователей
```
select user_id from qa_users;
```
4. Вывести только имя пользователей
```
select username from qa_users;
```
5. Вывести только email пользователей
```
select email from qa_users;
```
6. Вывести имя и email пользователей
```
select username, email from qa_users;
```
7. Вывести id, имя, email и дату создания пользователей
```
select user_id, username, created_on from qa_users;
```
8. Вывести пользователей где password 12333
```
select * from qa_users where "password" = '12333';
```
9. Вывести пользователей которые были созданы 2021-03-26 00:00:00
```
select * from qa_users where "created_on"='2021-03-26 00:00:00';
```
10. Вывести пользователей где в имени есть слово Анна
```
select * from qa_users where username like'Anna%';
```
11. Вывести пользователей где в имени в конце есть 8
```
select * from qa_users where username like'%8';
```
12. Вывести пользователей где в имени в есть буква а
```
select * from qa_users where username like'%a%';
```
13. Вывести пользователей которые были созданы 2021-07-12 00:00:00
```
select * from qa_users where "created_on"='2021-07-12 00:00:00';
```
14. Вывести пользователей которые были созданы 2021-07-12 00:00:00 и имеют пароль 1m313
```
select * from qa_users where "created_on"='2021-07-12 00:00:00' and "password" = '1m313';
```
15. Вывести пользователей которые были созданы 2021-07-12 00:00:00 и у которых в имени есть слово Andrey
```
select * from qa_users where "created_on" = '2021-07-12 00:00:00'and "username" like '%Andrey%';
```
16. Вывести пользователей которые были созданы 2021-07-12 00:00:00 и у которых в имени есть цифра 8
```
select * from qa_users where "created_on" = '2021-07-12 00:00:00'and "username" like '%8%';
```
17. Вывести пользователя у которых id равен 10
```
select * from qa_users where "user_id" = '10';
```
18. Вывести пользователя у которых id равен 53
```
select * from qa_users where "user_id" = '53';
```
19. Вывести пользователя у которых id больше 40
```
select * from qa_users where "user_id" > '40';
```
20. Вывести пользователя у которых id меньше 30
```
select * from qa_users where "user_id" < '30';
```
21. Вывести пользователя у которых id меньше 27 или больше 88
```
select * from qa_users where "user_id" < '27' or "user_id" >'88';
```
22. Вывести пользователя у которых id меньше либо равно 37
```
select * from qa_users where "user_id" < '37' or "user_id" = '37';
```
23. Вывести пользователя у которых id больше либо равно 37
```
select * from qa_users where "user_id" > '37' or "user_id" = '37';
```
24. Вывести пользователя у которых id больше 80 но меньше 90
```
select * from qa_users where "user_id" > '80' and "user_id" < '90';
```
25. Вывести пользователя у которых id между 80 и 90
```
select * from qa_users where "user_id" >= '80' and "user_id" <= '90';
```
26. Вывести пользователей где password равен 12333, 1m313, 123313
```
select * from qa_users where password in ('12333','1m313','123313');
```
27. Вывести пользователей где created_on равен 2020-10-03 00:00:00, 2021-05-19 00:00:00, 2021-03-26 00:00:00
```
select * from qa_users where created_on in ('2020-10-03 00:00:00','2021-05-19 00:00:00','2021-03-26 00:00:00');
```
28. Вывести минимальный id
```
select min(user_id) as min from qa_users;
```
29. Вывести максимальный.
```
select max(user_id) as max from qa_users;
```
30. Вывести количество пользователей
```
select count(user_id) from qa_users;
```
31. Вывести id пользователя, имя, дату создания пользователя. Отсортировать по порядку возрастания даты добавления пользователя.
```
select user_id, username, created_on from qa_users order by created_on asc;
```
32. Вывести id пользователя, имя, дату создания пользователя. Отсортировать по порядку убывания даты добавления пользователя.
```
select user_id, username, created_on from qa_users order by created_on desc;
```
____
## Домашняя работа SQL №2
 1. Вывести всех работников чьи зарплаты есть в базе, вместе с зарплатами.
```
select employee_name, monthly_salary 
from employees
join employees_salary
on employees.id = employees_salary.employee_id;
```
 2. Вывести всех работников у которых ЗП меньше 2000.
```
select employee_name, monthly_salary
from employees
join employees_salary
on employees.id = employees_salary.employee_id 
where monthly_salary < 2000;
```
 3. Вывести все зарплатные позиции, но работник по ним не назначен. (ЗП есть, но не понятно кто её получает.)
```
select employee_name, monthly_salary 
from employees
right join employees_salary
on employees.id = employees_salary.employee_id
where employee_name is null;
```
 4. Вывести все зарплатные позиции  меньше 2000 но работник по ним не назначен. (ЗП есть, но не понятно кто её получает.)
```
select employee_name, monthly_salary 
from employees
right join employees_salary
on employees.id = employees_salary.employee_id
where employee_name is null 
and monthly_salary < 2000;
```
 5. Найти всех работников кому не начислена ЗП.
```
select employee_name, monthly_salary 
from employees
left join employees_salary
on employees.id = employees_salary.employee_id
where monthly_salary is null;
```
 6. Вывести всех работников с названиями их должности.
```
select employee_name, role_name
from roles_employees
full join employees
on roles_employees.employee_id = employees.id
left join roles
on role_id = roles.id;
```
 7. Вывести имена и должность только Java разработчиков.
```
select employee_name, role_name
from roles_employees
join employees
on roles_employees.employee_id = employees.id
join roles
on role_id = roles.id
where role_name like '%Java%';
```
 8. Вывести имена и должность только Python разработчиков.
```
select employee_name, role_name
from roles_employees
join employees
on roles_employees.employee_id = employees.id
join roles
on role_id = roles.id
where role_name like '%Python%';
```
 9. Вывести имена и должность всех QA инженеров.
```
select employee_name, role_name
from roles_employees
join employees
on roles_employees.employee_id = employees.id
join roles
on role_id = roles.id
where role_name like '%QA engineer%';
```
 10. Вывести имена и должность ручных QA инженеров.
```
select employee_name, role_name
from roles_employees
join employees
on roles_employees.employee_id = employees.id
join roles
on role_id = roles.id
where role_name like '%Manual QA engineer%';
```
 11. Вывести имена и должность автоматизаторов QA
```
select employee_name, role_name
from roles_employees
join employees
on roles_employees.employee_id = employees.id
join roles
on role_id = roles.id
where role_name like '%Automation QA engineer%';
```
 12. Вывести имена и зарплаты Junior специалистов
```
select employee_name, monthly_salary
from employees
join employees_salary
on employees_salary.employee_id = employees.id
join roles_employees
on roles_employees.employee_id = employees.id
join roles
on role_id = roles.id 
where role_name like '%Junior%';
```
 13. Вывести имена и зарплаты Middle специалистов
```
select employee_name, monthly_salary
from employees
join employees_salary
on employees_salary.employee_id = employees.id
join roles_employees
on roles_employees.employee_id = employees.id
join roles
on role_id = roles.id 
where role_name like '%Middle%';
```
 14. Вывести имена и зарплаты Senior специалистов
```
select employee_name, monthly_salary
from employees
join employees_salary
on employees_salary.employee_id = employees.id
join roles_employees
on roles_employees.employee_id = employees.id
join roles
on role_id = roles.id 
where role_name like '%Senior%';
```
 15. Вывести зарплаты Java разработчиков
```
select monthly_salary
from employees
join employees_salary
on employees_salary.employee_id = employees.id
join roles_employees
on roles_employees.employee_id = employees.id
join roles
on role_id = roles.id 
where role_name like '%Java developer%';
```
 16. Вывести зарплаты Python разработчиков
```
select monthly_salary
from employees
join employees_salary
on employees_salary.employee_id = employees.id
join roles_employees
on roles_employees.employee_id = employees.id
join roles
on role_id = roles.id 
where role_name like '%Python%';
```
 17. Вывести имена и зарплаты Junior Python разработчиков
```
select employee_name, monthly_salary
from employees
full join employees_salary
on employees_salary.employee_id = employees.id
full join roles_employees
on roles_employees.employee_id = employees.id
full join roles
on role_id = roles.id 
where role_name like '%Junior Python%';
```
 18. Вывести имена и зарплаты Middle JS разработчиков
```
select employee_name, monthly_salary
from employees
join employees_salary
on employees_salary.employee_id = employees.id
join roles_employees
on roles_employees.employee_id = employees.id
join roles
on role_id = roles.id 
where role_name like '%Middle JavaScript%';
```
 19. Вывести имена и зарплаты Senior Java разработчиков
```
select employee_name, monthly_salary
from employees
join employees_salary
on employees_salary.employee_id = employees.id
join roles_employees
on roles_employees.employee_id = employees.id
join roles
on role_id = roles.id 
where role_name like '%Senior Java%';
```
 20. Вывести зарплаты Junior QA инженеров
```
select monthly_salary
from employees
join employees_salary
on employees_salary.employee_id = employees.id
join roles_employees
on roles_employees.employee_id = employees.id
join roles
on role_id = roles.id 
where role_name like '%Junior%QA%';
```
 21. Вывести среднюю зарплату всех Junior специалистов
```
select avg(monthly_salary)
from employees
join employees_salary
on employees_salary.employee_id = employees.id
join roles_employees
on roles_employees.employee_id = employees.id
join roles
on role_id = roles.id
where role_name like '%Junior%';
```
 22. Вывести сумму зарплат JS разработчиков
```
select sum(monthly_salary)
from employees
join employees_salary
on employees_salary.employee_id = employees.id
join roles_employees
on roles_employees.employee_id = employees.id
join roles
on role_id = roles.id
where role_name like '%JavaScript%';
```
 23. Вывести минимальную ЗП QA инженеров
```
select MIN(monthly_salary)
from employees
join employees_salary
on employees_salary.employee_id = employees.id
join roles_employees
on roles_employees.employee_id = employees.id
join roles
on role_id = roles.id
where role_name like '%QA engineer%';
```
 24. Вывести максимальную ЗП QA инженеров
```
select MAX(monthly_salary)
from employees
join employees_salary
on employees_salary.employee_id = employees.id
join roles_employees
on roles_employees.employee_id = employees.id
join roles
on role_id = roles.id
where role_name like '%QA engineer%';
```
 25. Вывести количество QA инженеров
```
select COUNT(monthly_salary)
from employees
join employees_salary
on employees_salary.employee_id = employees.id
join roles_employees
on roles_employees.employee_id = employees.id
join roles
on role_id = roles.id
where role_name like '%QA engineer%';
```
 26. Вывести количество Middle специалистов.
```
select COUNT(monthly_salary)
from employees
join employees_salary
on employees_salary.employee_id = employees.id
join roles_employees
on roles_employees.employee_id = employees.id
join roles
on role_id = roles.id
where role_name like '%Middle%';
```
 27. Вывести количество разработчиков
```
select COUNT(monthly_salary)
from employees
join employees_salary
on employees_salary.employee_id = employees.id
join roles_employees
on roles_employees.employee_id = employees.id
join roles
on role_id = roles.id
where role_name like '%developer%';
```
 28. Вывести фонд (сумму) зарплаты разработчиков.
```
select SUM(monthly_salary)
from employees
join employees_salary
on employees_salary.employee_id = employees.id
join roles_employees
on roles_employees.employee_id = employees.id
join roles
on role_id = roles.id
where role_name like '%developer%';
```
 29. Вывести имена, должности и ЗП всех специалистов по возрастанию
```
select employee_name, role_name, monthly_salary
from employees
left join employees_salary
on employees_salary.employee_id = employees.id
left join roles_employees
on roles_employees.employee_id = employees.id
left join roles
on role_id = roles.id
order by monthly_salary ASC;
```
 30. Вывести имена, должности и ЗП всех специалистов по возрастанию у специалистов у которых ЗП от 1700 до 2300
```
select employee_name, role_name, monthly_salary
from employees
left join employees_salary
on employees_salary.employee_id = employees.id
left join roles_employees
on roles_employees.employee_id = employees.id
left join roles
on role_id = roles.id
where "monthly_salary" > '1700' and "monthly_salary" < '2300';
order by monthly_salary ASC;
```
 31. Вывести имена, должности и ЗП всех специалистов по возрастанию у специалистов у которых ЗП меньше 2300
```
select employee_name, role_name, monthly_salary
from employees
left join employees_salary
on employees_salary.employee_id = employees.id
left join roles_employees
on roles_employees.employee_id = employees.id
left join roles
on role_id = roles.id
where "monthly_salary" < '2300'
order by monthly_salary ASC;
```
 32. Вывести имена, должности и ЗП всех специалистов по возрастанию у специалистов у которых ЗП равна 1100, 1500, 2000
```
select employee_name, role_name, monthly_salary
from employees
left join employees_salary
on employees_salary.employee_id = employees.id
left join roles_employees
on roles_employees.employee_id = employees.id
left join roles
on role_id = roles.id
where monthly_salary in ('1100','1500','2000')
order by monthly_salary ASC;
```
____
## Домашняя работа SQL №3
 1. Создайте базу из представленной картинки;
 ![photo_2021-10-12_18-20-47](https://user-images.githubusercontent.com/88891623/138416220-1e39057e-72b6-49d0-aa62-d338585d90a5.jpg)
 1.2. У каждой таблицы должно быть поле id;  /  1.3. id автоинкрементальный и является первичным ключом;
```
create table salary (
	id serial primary key,
	monthly_salary int not null
);
```
```
create table roles (
	id serial primary key,
	role_title varchar (50) not null
);
```
```
create table roles_salary (
	id serial primary key,
	id_role int not null,
	id_salary int not null,
	foreign key (id_role)
		references roles (id),
	foreign key (id_salary)
		references salary (id)
);
```
```
create table employees (
	id serial primary key,
	employee_name varchar (50) not null
);
```
```
create table employees_roles (
	id serial primary key,
	id_role int not null,
	id_employee int not null,
	foreign key (id_role)
		references roles (id),
	foreign key (id_employee)
		references employees (id)
);
```
```
create table Service (
	id serial primary key,
	service_title varchar (50) not null,
	price int not null
);
```
```
create table materials (
	id serial primary key,
	material_title varchar (50) not null,
	amount int not null
);
```
```	
create table claim (
	id serial primary key,
	service_id int not null,
	employee_id int not null,
	material_id int not null,
	claim_date date not null,
	sales_manager int not null,
	foreign key (employee_id)
		references employees (id),
	foreign key (sales_manager)
		references employees (id),
	foreign key (service_id)
		references Service (id),
	foreign key (material_id)
		references materials (id)
);
```
 2. Заполните таблицы данными. Не менее 10 строк в каждой таблице;
```
insert into	salary (id, monthly_salary) values (default, 500);
insert into	salary (id, monthly_salary) values (default, 600);
insert into	salary (id, monthly_salary) values (default, 700);
insert into	salary (id, monthly_salary) values (default, 800);
insert into	salary (id, monthly_salary) values (default, 900);
insert into	salary (id, monthly_salary) values (default, 1000);
insert into	salary (id, monthly_salary) values (default, 1100);
insert into	salary (id, monthly_salary) values (default, 1200);
insert into	salary (id, monthly_salary) values (default, 1300);
insert into	salary (id, monthly_salary) values (default, 1400);
```
```
insert into roles (id, role_title) values (default, 'Manual QA engineer');
insert into roles (id, role_title) values (default, 'Manual QA engineer');
insert into roles (id, role_title) values (default, 'Manual QA engineer');
insert into roles (id, role_title) values (default, 'Manual QA engineer');
insert into roles (id, role_title) values (default, 'Manual QA engineer');
insert into roles (id, role_title) values (default, 'Automation QA engineer');
insert into roles (id, role_title) values (default, 'Automation QA engineer');
insert into roles (id, role_title) values (default, 'Automation QA engineer');
insert into roles (id, role_title) values (default, 'Automation QA engineer');
insert into roles (id, role_title) values (default, 'Automation QA engineer');
```
```
insert into roles_salary (id, id_role, id_salary) values (default, 1, 15);
insert into roles_salary (id, id_role, id_salary) values (default, 2, 16);
insert into roles_salary (id, id_role, id_salary) values (default, 3, 17);
insert into roles_salary (id, id_role, id_salary) values (default, 4, 18);
insert into roles_salary (id, id_role, id_salary) values (default, 5, 19);
insert into roles_salary (id, id_role, id_salary) values (default, 6, 20);
insert into roles_salary (id, id_role, id_salary) values (default, 7, 21);
insert into roles_salary (id, id_role, id_salary) values (default, 8, 22);
insert into roles_salary (id, id_role, id_salary) values (default, 9, 23);
insert into roles_salary (id, id_role, id_salary) values (default, 10, 24);
```
```
insert into employees (id, employee_name) values (default, 'Angelina Jolie');
insert into employees (id, employee_name) values (default, 'Charlize Theron');
insert into employees (id, employee_name) values (default, 'Jessica Alba');
insert into employees (id, employee_name) values (default, 'Megan Fox');
insert into employees (id, employee_name) values (default, 'Penelope Cruz');
insert into employees (id, employee_name) values (default, 'Robert Pattinson');
insert into employees (id, employee_name) values (default, 'Bradley Pitt');
insert into employees (id, employee_name) values (default, 'Antonio Banderas');
insert into employees (id, employee_name) values (default, 'David Boreanaz');
insert into employees (id, employee_name) values (default, 'George Clooney');
```
```
insert into employees_roles (id, id_role, id_employee) values (default, 1, 10);
insert into employees_roles (id, id_role, id_employee) values (default, 2, 9);
insert into employees_roles (id, id_role, id_employee) values (default, 3, 8);
insert into employees_roles (id, id_role, id_employee) values (default, 4, 7);
insert into employees_roles (id, id_role, id_employee) values (default, 5, 6);
insert into employees_roles (id, id_role, id_employee) values (default, 6, 5);
insert into employees_roles (id, id_role, id_employee) values (default, 7, 4);
insert into employees_roles (id, id_role, id_employee) values (default, 8, 3);
insert into employees_roles (id, id_role, id_employee) values (default, 9, 2);
insert into employees_roles (id, id_role, id_employee) values (default, 10, 1);
```
```
insert into Service (id, service_title, price) values (default, 'Web App', 10000);
insert into Service (id, service_title, price) values (default, 'Web App', 11000);
insert into Service (id, service_title, price) values (default, 'Web App', 12000);
insert into Service (id, service_title, price) values (default, 'Web App', 13000);
insert into Service (id, service_title, price) values (default, 'Web App', 14000);
insert into Service (id, service_title, price) values (default, 'Mobile App', 15000);
insert into Service (id, service_title, price) values (default, 'Mobile App', 16000);
insert into Service (id, service_title, price) values (default, 'Mobile App', 17000);
insert into Service (id, service_title, price) values (default, 'Mobile App', 18000);
insert into Service (id, service_title, price) values (default, 'Mobile App', 19000);
```
```
insert into materials (id, material_title, amount, price) values (default, 'A', 17, 101);
insert into materials (id, material_title, amount, price) values (default, 'B', 18, 102);
insert into materials (id, material_title, amount, price) values (default, 'C', 19, 103);
insert into materials (id, material_title, amount, price) values (default, 'D', 20, 104);
insert into materials (id, material_title, amount, price) values (default, 'E', 21, 105);
insert into materials (id, material_title, amount, price) values (default, 'F', 22, 106);
insert into materials (id, material_title, amount, price) values (default, 'G', 23, 107);
insert into materials (id, material_title, amount, price) values (default, 'H', 24, 108);
insert into materials (id, material_title, amount, price) values (default, 'I', 25, 109);
insert into materials (id, material_title, amount, price) values (default, 'J', 26, 110);
```
```
insert into claim (id, service_id, employee_id, material_id, claim_date, sales_manager) values (default, 1, 10, 1, '01.10.2021', 1);
insert into claim (id, service_id, employee_id, material_id, claim_date, sales_manager) values (default, 2, 9, 2, '02.10.2021', 2);
insert into claim (id, service_id, employee_id, material_id, claim_date, sales_manager) values (default, 3, 8, 3, '03.10.2021', 3);
insert into claim (id, service_id, employee_id, material_id, claim_date, sales_manager) values (default, 4, 7, 4, '04.10.2021', 4);
insert into claim (id, service_id, employee_id, material_id, claim_date, sales_manager) values (default, 5, 6, 5, '05.10.2021', 5);
insert into claim (id, service_id, employee_id, material_id, claim_date, sales_manager) values (default, 6, 5, 6, '06.10.2021', 6);
insert into claim (id, service_id, employee_id, material_id, claim_date, sales_manager) values (default, 7, 4, 7, '07.10.2021', 7);
insert into claim (id, service_id, employee_id, material_id, claim_date, sales_manager) values (default, 8, 3, 8, '08.10.2021', 8);
insert into claim (id, service_id, employee_id, material_id, claim_date, sales_manager) values (default, 9, 2, 9, '09.10.2021', 9);
insert into claim (id, service_id, employee_id, material_id, claim_date, sales_manager) values (default, 10, 1, 10, '10.10.2021', 10);
```
 3. Добавить таблицу Suppliers с полями id, name;
```
create table Suppliers (
	id serial primary key,
	name varchar (50) not null
);
```
 4. Добавить 10 строк поставщиков в таблицу Suppliers;
```
insert into Suppliers (id, name) values (DEFAULT, 'Alfa');
insert into Suppliers (id, name) values (DEFAULT, 'Bravo');
insert into Suppliers (id, name) values (DEFAULT, 'Charlie');
insert into Suppliers (id, name) values (DEFAULT, 'Delta');
insert into Suppliers (id, name) values (DEFAULT, 'Echo');
insert into Suppliers (id, name) values (DEFAULT, 'Foxtrot');
insert into Suppliers (id, name) values (DEFAULT, 'Golf');
insert into Suppliers (id, name) values (DEFAULT, 'Hotel');
insert into Suppliers (id, name) values (DEFAULT, 'India');
insert into Suppliers (id, name) values (DEFAULT, 'Juliett');
```
 5. Обновить таблицу Materials. Добавить поле suplier_id которое связано с полем id в таблице Suppliers;
```
alter table materials 
	add column supplier_id int,
	add foreign key (supplier_id)
		references suppliers (id);
```		
 6. Обновить таблицу Employees. Добавить varchar поле surname на 50 символов;
```	
alter table employees
	add column surname varchar (50)
```	
 7. Обновить таблицу Salary. Добавить varchar поле currency на 7 символов.
```	
alter table salary
	add column currency varchar (7)
```
Результат:
![Снимок](https://user-images.githubusercontent.com/88891623/138417357-8b6debc8-1de0-4a74-86bf-2d0f074215ef.PNG)
