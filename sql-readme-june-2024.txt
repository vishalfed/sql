
RDBMS (MySQL)     16 hours
----------------------------------------
Day1 : 24-Jun-2024   
----------------------------------------
Program/Software/Application/Product/Service


Application
----------------
Desktop
Mobile
Web
Hybrid
PWA
SPA


C -> CREATE
R -> READ/RETRIEVE
U -> UPDATE
D -> DELETE


Database  (Collection Of Data)
--------------------------------------------
array/collection
txt,word,pdf,excel,xml
RDBMS -> MySQL,Oracle,Postgres
NOSQL -> MongoDB,Cassendra,Hbase,
Cloud -> Google Cloud



RDBMS (Relational Database System)
------------------------------------------------------
Relation -> Table

Stores the data in tabular format
-----------------------------------------------------
Employee
--------------
id   fname lname  email salary  dept_id   dept_name   mgr_id  city designation   dob doj


101  Amol  Kale    a@gmail.com 12000   11   Sales      __         Pune  CEO

   

number  text/string   date


SQL
------
DDL - Data Defintion Lanaguage
DML - Data MAnipulation Language
DRL - Data Retrieval Language
TCL - Tranasaction Control Language

MySQL -> (Client - Server)  ->https://dev.mysql.com/downloads/installer/

CUI -> MySQL Client
GUI -> MySQL Workbench

Default port :3306
Default usernmae :root


show databases;
create database pc_company;
use pc_company;

create table employee(
id int,
name text,
salary float
); 

show tables;
desc employee;
describe employee;


insert into employee values(101,'AMOL',10000);
insert into employee values(102,'SACHIN',20000);
insert into employee values(102,'MOHAN',30000);

insert into employee (name) values('MOHAN');



select * from employee;
----------------------------------------------------------------------------------








Day2 : 25-Jun-2024  
----------------------------
SQL Types
----------------
DDL -> CREATE,ALTER,DROP
DML -> INSERT,UPDATE,DELETE
DRL -> SELECT
TCL -> COMMIT,ROLLBACK
------------------------------------------------
A  ->ATOMOCITY
C -> CONSISENCY
I  -> ISOLATION
D -> DURABLE


NOSQL
-----------
C -> COSNSISTENCY
       -> Weak
       -> Eventual
       -> Strong  

A -> AVAILABILITY
P -> PARTION TOLEREANCE

Employee
--------------
id   fname lname  email salary  dept_id   dept_name   mgr_id  city designation   dob doj

drop table employee;

create table employee(
id int primary key,
fname text,
lname text, 
email  varchar(20) not null unique,
salary float, 
dept_id int default 11,
dept_name varchar(20) default 'Training',
mgr_id int,
city text,
designation text,
dob date,
doj  date
);

desc employee;


alter table employee modify doj datetime default CURRENT_TIMESTAMP;
alter table employee modify dob date CHECK (dob <sysdate());
alter table employee drop column city;
alter table employee add column city text;
alter table employee modify column id int AUTO_INCREMENT;
alter table employee modify designation varchar(20) default 'graduate_hire';


insert into employee (fname,lname,email,salary,dob,city) values('sachin','Tendulkar','Sachin@gmail.com',12000,'1972-07-24','MUMBAI');
insert into employee (fname,lname,email,salary,dob,city) values('virendra','Sehwag','Virendra@gmail.com',15000,'1985-07-24','MUMBAI');
insert into employee (fname,lname,email,salary,dob,city) values('Mohan','Shende','Mohan@gmail.com',12000,'1978-07-24','MUMBAI');
insert into employee (fname,lname,email,salary,dob,city) values('Sumit','Raghvan','Sumit@gmail.com',12000,'1977-07-24','SOLAPUR');
insert into employee (fname,lname,email,salary,dob,city) values('Sumit','Patil','Sumit1@gmail.com',13000,'2025-07-24','SOLAPUR');


insert into employee (fname,lname,email,salary,dob,city) values('Prakash','Patil','Prakash@gmail.com',12000,'1992-07-24','PUNE');


insert into employee (fname,lname,email,salary,dob,city) values('Prakash','Patil','Prakash@gmail.com',12000,'1992-07-24','PUNE');
insert into employee (fname,lname,salary,dob,city) values('Prakash','Patil',12000,'1992-07-24','PUNE');


select * from employee where fname='SACHIN';

select * from employee where fname='SACHIN' AND lname='TENDULKAR';

select * from employee where fname='Sachin' AND lname='tENDULKAR';



update employee set mgr_id=1 where id=2;


update employee set mgr_id=2 where id>2;

select * from employee where city='PUNE' OR city='SOLAPUR';
select * from employee where city IN ('PUNE' ,'SOLAPUR');


select * from employee where city='PUNE' OR city='SOLAPUR' OR city='MUMBAI';
select * from employee where city IN ('PUNE' ,'SOLAPUR','MUMBAI');


select max(salary) from employee;
select min(salary) from employee;
select sum(salary) from employee;
select avg(salary) from employee;

select count(salary) from employee;
select count(*) from employee;
select count(mgr_id) from employee;


select max(salary),min(salary),sum(salary),avg(salary),count(salary) from employee;


select max(salary) AS MAX_SALARAY ,min(salary) AS MIN_SALARY,sum(salary) AS TOTAL_SALARY ,avg(salary) AS AVG_SALARY,count(salary) AS NUMBER_OF_EMPLOYEES from employee;


Day3 : 26-Jun-2024   
----------------------------


Course (Master)
----------
cid      name     price
------------------------------
10      Java       12000
20      Node.js    15000


Student  (Child)
------------
sid     name      cid
---------------------------
101    Sachin    10
102    Mahesh   20



create table course (cid int primary key,name text,price float);
INSERT INTO COURSE VALUES(10,'Java',12000);
INSERT INTO COURSE VALUES(20,'Node.js',15000);
INSERT INTO COURSE VALUES(30,'Python',15000);




create table student (sid int primary key,name text,course_id int);

INSERT INTO STUDENT VALUES(101,'Sachin',10);
INSERT INTO STUDENT VALUES(102,'Sachin',20);
INSERT INTO STUDENT VALUES(103,'Mahesh',30);
INSERT INTO STUDENT VALUES(104,'Sunil',null);




 select * from course;
 select * from student;

drop table student;


create table student (sid int primary key,name text,course_id int, FOREIGN KEY (course_id) REFERENCES course(cid));


create table student (sid int primary key,name text,course_id int, FOREIGN KEY (course_id) REFERENCES course(cid) ON DELETE CASCADE);


create table student (sid int primary key,name text,course_id int, FOREIGN KEY (course_id) REFERENCES course(cid) ON DELETE SET NULL);

create table student (sid int primary key,name text,course_id int, FOREIGN KEY (course_id) REFERENCES course(cid) ON DELETE SET NULL 
        ON UPDATE CASCADE
);




 delete from course where cid=10;
 update course set cid=40 where cid=30;






passportnumber
liscenscenumber
ssn

(ssn,passportnumber)
(ssn,liscensenumber,passportnumber)


--------------------------------------------------------------------

https://github.com/vishalfed/sql


Day4 : 27-Jun-2024   
----------------------------
SQL Activity1 & SQL Activity 2

Agenda SQL Activity 2
----------------------

Problem # 1 Creating Tables : 
-----------------------------------

create database ums;

use ums;


create table pc_student_info(
reg_number varchar(20) primary key,
student_name varchar(30) not null,
branch varchar(20), 
contact_number varchar(10),
date_of_birth date not null,
date_of_joining date not null default (current_date),
address varchar(250), 
email_id varchar(20)
);





create table pc_subject_master(
subject_code varchar(10) primary key,
subject_name varchar(20) not null,
weightage int not null
);





create table pc_student_marks(
reg_number varchar(20),
subject_code varchar(10),
semester int not null,
marks int default (0),
foreign key (reg_number) references pc_student_info(reg_number),
foreign key (subject_code) references pc_subject_master(subject_code)
);


create table pc_student_result(
reg_number varchar(20),
semester int not null,
gpa float,
is_eligible_scholarship char(3),
foreign key (reg_number) references pc_student_info(reg_number)
);





Problem # 2 Working with constraints:
-----------------------------------------------------

a)

alter table pc_subject_master modify column subject_name varchar(20) not null unique;


b)
alter table pc_student_info modify column contact_number varchar(10) not null unique;



c)

alter table pc_student_info modify column date_of_birth date not null CHECK (date_of_birth < sysdate());


d) 

alter table pc_student_marks modify column marks int  CHECK (marks<=100) default (0);


e)

alter table pc_student_result modify column gpa int  CHECK (gpa between 0 and 10) default (0);


f)

alter table pc_student_result modify column is_eligible_scholarship char(3)  CHECK (is_eligible_scholarship='Yes' OR is_eligible_scholarship='NO') default (0);

alter table pc_student_result modify column is_eligible_scholarship char(1)  CHECK (is_eligible_scholarship in ('Y','N'));



Problem # 3  Loading tables using DML:  
-------------------------------------------

a)
----

alter table pc_student_info modify column email_id varchar(40);


insert into pc_student_info values
 ('MC101301','James','MCA','9714589787',STR_TO_DATE('12-jan-1984','%d-%b-%Y'),STR_TO_DATE('08-jul-2010','%d-%b-%Y'),'No 10 South Block,Nivea','james.mca@yahoo.com'),
(
'BEC111402','Manio', 'ECE','8912457875',STR_TO_DATE('23-feb-1983','%d-%b-%Y'),STR_TO_DATE('25-jun-2011','%d-%b-%Y'),'8/12,Park View,Sieera',	'manioma@gmail.com'),
(
'BEEI101204','Mike','EI','8974567897',STR_TO_DATE('10-feb-1983','%d-%b-%Y'),STR_TO_DATE('25-aug-2010','%d-%b-%Y'),'Cross villa,NY',	'mike.james@ymail.com'),
(
'MB111305','Paulson','MBA','8547986123',STR_TO_DATE('13-dec-1984','%d-%b-%Y'),STR_TO_DATE('08-aug-2010','%d-%b-%Y'),'Lake view,NJ',	'paul.son@rediffmail.com'),
(
'MB222305','Pradeep','MBA','8239947383',STR_TO_DATE('13-dec-2011','%d-%b-%Y'),STR_TO_DATE('08-aug-2011','%d-%b-%Y'),'Warje Pune',NULL);


select * from pc_student_info;



------------------------

b)


alter table pc_subject_master modify column subject_name varchar(50);

insert into pc_subject_master values
('EE01DCF','DCF',30),
('EC02MUP','Microprocessor',40), 
('MC06DIP','Digital Image Processing',30),
('MB03MAR','Marketing Techniques',20),
('EI05IP','Instrumentation Precision',40),
('CPSC02DS','Data Structures',40);

SELECT * FROM pc_subject_master;


c)
---
ALTER TABLE pc_student_marks RENAME PC_STUDENT_MARKS;

INSERT INTO PC_STUDENT_MARKS VALUES('MC101301','EE01DCF',	1,	75);
INSERT INTO PC_STUDENT_MARKS VALUES('MC101301','EC02MUP',	1,	65);
INSERT INTO PC_STUDENT_MARKS VALUES('MC101301','MC06DIP',	1,	70);
INSERT INTO PC_STUDENT_MARKS VALUES('BEC111402','EE01DCF',	1,	55);
INSERT INTO PC_STUDENT_MARKS VALUES('BEC111402','EC02MUP',	1,	80);
INSERT INTO PC_STUDENT_MARKS VALUES('BEC111402','MC06DIP',	1,	60);
INSERT INTO PC_STUDENT_MARKS VALUES('BEEI101204','EE01DCF',	1,	85);
INSERT INTO PC_STUDENT_MARKS VALUES('BEEI101204','EC02MUP',	1,	78);
INSERT INTO PC_STUDENT_MARKS VALUES('BEEI101204','MC06DIP',	1,	80);
INSERT INTO PC_STUDENT_MARKS VALUES('BEEI101204','MB03MAR',	2,	75);
INSERT INTO PC_STUDENT_MARKS VALUES('BEEI101204','EI05IP',	2,	65);
INSERT INTO PC_STUDENT_MARKS VALUES('BEEI101204','CPSC02DS',    2,	75);
INSERT INTO PC_STUDENT_MARKS VALUES('MB111305','EE01DCF',	1,	65);
INSERT INTO PC_STUDENT_MARKS VALUES('MB111305','EC02MUP',	1,	68);
INSERT INTO PC_STUDENT_MARKS VALUES('MB111305','MC06DIP',	1,	63);
INSERT INTO PC_STUDENT_MARKS VALUES('MB111305','MB03MAR',	2,	85);
INSERT INTO PC_STUDENT_MARKS VALUES('MB111305','EI05IP',	2,	74);
INSERT INTO PC_STUDENT_MARKS VALUES('MB111305','CPSC02DS',      2,	62);


SELECT * FROM PC_STUDENT_MARKS;

d)

INSERT INTO PC_STUDENT_RESULT VALUES('MC101301',1,7.5,'Y');
INSERT INTO PC_STUDENT_RESULT VALUES('BEC111402',1,7.1,'Y');
INSERT INTO PC_STUDENT_RESULT VALUES('BEEI101204',1,8.3,'Y');
INSERT INTO PC_STUDENT_RESULT VALUES('BEEI101204',2,6.9,'N');
INSERT INTO PC_STUDENT_RESULT VALUES('MB111305',1,6.5,'N');
INSERT INTO PC_STUDENT_RESULT VALUES('MB111305',2,6.8,'N');

SELECT * FROM PC_STUDENT_RESULT;



Problem # 4 Perform the following operations:  
--------------------------------------------------------------

a)
update pc_student_info set reg_number='MC101212' where student_name='James';

b)
update pc_subject_master set subject_code='DS0112' where subject_name='Data Structures';

c) 
insert into pc_subject_master (subject_code,subject_name) values('AB2345','AI');

d) 
update pc_student_info set contact_number='8912457875' where student_name='Paulson';

e)

select * from pc_student_info where student_name='James';

select reg_number from pc_student_info where student_name='James';


select * from pc_subject_master where subject_name='DCF';

select subject_code from pc_subject_master where subject_name='DCF';


update pc_student_marks set marks=15 where reg_number='MC101301' AND subject_code='EE01DCF';

update pc_student_marks set marks=12 where reg_number=(select reg_number from pc_student_info where student_name='James'
) AND subject_code=(select subject_code from pc_subject_master where subject_name='DCF');


f)

select reg_number from pc_student_info where student_name='Mike';

BEEI101204

update pc_student_result set gpa=11 where reg_number='BEEI101204';


update pc_student_result set gpa=3 where reg_number=(select reg_number from pc_student_info where student_name='Mike');


Day5 : 28-Jun-2024   
----------------------------
SQL Joins
--------------


create table department(
id int primary key,
name text);

INSERT INTO DEPARTMENT VALUES(11,'ACCOUNTS');
INSERT INTO DEPARTMENT VALUES(22,'SALES');
INSERT INTO DEPARTMENT VALUES(33,'SUPPORT');
INSERT INTO DEPARTMENT VALUES(44,'REVENUE');
INSERT INTO DEPARTMENT VALUES(55,'MARKETING');
 

drop table employee;

create table employee(
id int primary key,
name text,
salary float,
dept_id int
);

INSERT INTO EMPLOYEE VALUES(101,'AMOL',12000,11);
INSERT INTO EMPLOYEE VALUES(102,'MOHAN',62000,11);
INSERT INTO EMPLOYEE VALUES(103,'SUNIL',42000,22);
INSERT INTO EMPLOYEE VALUES(104,'PRAKASH',16000,22);
INSERT INTO EMPLOYEE VALUES(105,'RAM',12000,77);
INSERT INTO EMPLOYEE VALUES(106,'RAJESH',15000,77);
INSERT INTO EMPLOYEE VALUES(107,'PRAMOD',16000,88);



select * from employee;

select * from department;



SQL JOINS
----------------
INNER JOIN
LEFT JOIN / LEFT OUTER JOIN
RIGHT JOIN / RIGHT OUTER JOIN
CROSS JOIN


INNER JOIN
-----------------
SELECT e.id,e.name,e.salary,e.dept_id,d.name FROM EMPLOYEE e JOIN DEPARTMENT d ON d.id=e.dept_id;
 
SELECT e.id,e.name,e.salary,d.id,d.name FROM EMPLOYEE e INNER JOIN DEPARTMENT d ON d.id=e.dept_id;


LEFT OUTER JOIN
----------------------------
SELECT e.id,e.name,e.salary,e.dept_id,d.name FROM EMPLOYEE e LEFT OUTER JOIN DEPARTMENT d ON d.id=e.dept_id;

 
RIGHT OUTER JOIN
----------------------------
SELECT e.id,e.name,e.salary,e.dept_id,d.name FROM EMPLOYEE e RIGHT OUTER JOIN DEPARTMENT d ON d.id=e.dept_id;


CROSS JOIN
----------------------------
SELECT e.id,e.name,e.salary,e.dept_id,d.name FROM EMPLOYEE e CROSS JOIN DEPARTMENT d;


SELF JOIN
-----------------

SELECT e.id,e.fname,e.lname,m.mgr_id,m.fname,m.lname FROM EMPLOYEE e JOIN EMPLOYEE m ON e.mgr_id=m.id;


SELECT e.id,concat(e.fname,'  ',e.lname) as Employee_Name,m.mgr_id,concat(m.fname,'  ',m.lname) as Manager_Name FROM EMPLOYEE e JOIN EMPLOYEE m ON e.mgr_id=m.id;


--------------------------------------------
SQL Activity 3
------------------------
1)

SELECT * FROM PC_STUDENT_INFO WHERE EMAIL_ID IS NULL;

SELECT * FROM PC_STUDENT_INFO WHERE EMAIL_ID IS NOT NULL;

2)

SELECT branch,count(*) from PC_STUDENT_INFO GROUP BY branch;
 
SELECT branch as Branch_Name, count(*) as Number_Of_Students from PC_STUDENT_INFO GROUP BY branch;

 3)

SELECT si.reg_number,sm.marks FROM PC_STUDENT_INFO si JOIN PC_STUDENT_MARKS sm ON si.reg_number=sm.reg_number WHERE sm.marks>50;

4)
SELECT si.reg_number,si.student_name,sr.gpa FROM PC_STUDENT_INFO si JOIN PC_STUDENT_RESULT sr ON si.reg_number=sr.reg_number ORDER BY gpa;

SELECT si.reg_number,si.student_name,sr.gpa FROM PC_STUDENT_INFO si JOIN PC_STUDENT_RESULT sr ON si.reg_number=sr.reg_number ORDER BY gpa DESC;


5)

SELECT * FROM PC_STUDENT_INFO;


SELECT * FROM PC_STUDENT_INFO ORDER BY STUDENT_NAME ASC;

6)

SELECT * FROM PC_STUDENT_INFO ORDER BY date_of_birth ASC;

SELECT * FROM PC_STUDENT_INFO ORDER BY date_of_birth DESC;


7)

SELECT si.reg_number,si.student_name, sb.subject_name,sm.semester,sm.marks    
 FROM PC_STUDENT_INFO si JOIN PC_SUBJECT_MASTER sb JOIN  PC_STUDENT_MARKS sm
ON si.reg_number=sm.reg_number AND sb.subject_code=sm.subject_code;

Day 6 : 29-Jun-2024
----------------------------
8)
select 
     si.reg_number,
     si.student_name,
     sm.semester,
     sm.marks
from pc_student_info si join pc_student_marks sm
     on       
     si.reg_number=sm.reg_number
     order by si.reg_number,sm.semester;

9)

select 
     si.reg_number,
     si.student_name,
     concat(sb.subject_code,' - ', 
     sb.subject_name) as Subject_Code_Subject_Name,
     sm.semester,
     sm.marks
from pc_student_info si join pc_subject_master sb join pc_student_marks sm
     on       
     si.reg_number=sm.reg_number and sb.subject_code=sm.subject_code
     where sm.marks> 70;
 

10)

select 
     si.reg_number,
     sr.gpa,
     sr.is_eligible_scholarship
from pc_student_info si join pc_student_result sr
     on       
     si.reg_number=sr.reg_number
     order by sr.is_eligible_scholarship desc;
 

11)
select 
     si.reg_number,
     si.student_name,
     sm.semester,
     sr.gpa
 from pc_student_info si join pc_student_marks sm join pc_student_result sr
     on       
     si.reg_number=sr.reg_number and si.reg_number=sm.reg_number
     order by sr.gpa desc;
 
12)
select 
     si.reg_number,
     si.student_name,
     sm.marks,
     ((sm.marks*sb.weightage)/100) as weighted_marks 
    
 from pc_student_info si join pc_student_marks sm join pc_subject_master sb join pc_student_result sr
     on       
     si.reg_number=sr.reg_number and sb.subject_code=sm.subject_code;

13)

select * from pc_student_info where student_name like'M%';

14)

select si.reg_number,si.student_name,sm.marks from pc_student_info si join pc_student_marks sm on si.reg_number=sm.reg_number where sm.marks>=60 and sm.marks<=100;

select si.reg_number,si.student_name,sm.marks from pc_student_info si join pc_student_marks sm on si.reg_number=sm.reg_number where sm.marks between 60 and 100;


15)

select si.reg_number,si.student_name,sm.marks from pc_student_info si join pc_student_marks sm on si.reg_number=sm.reg_number where si.student_name not like 'J%';


16)

select si.reg_number,si.student_name,sb.subject_code,sb.subject_name, sm.marks from pc_student_info si join pc_student_marks sm join pc_subject_master sb on si.reg_number=sm.reg_number and sb.subject_code=sm.subject_code where sb.subject_code in ('EE01DCF','EC02MUP');


select si.reg_number,si.student_name,sb.subject_code,sb.subject_name, sm.marks from pc_student_info si join pc_student_marks sm join pc_subject_master sb on si.reg_number=sm.reg_number and sb.subject_code=sm.subject_code where sb.subject_code in ('EE01DCF','EC02MUP');

17)
select * from pc_student_info where student_name like '%on';


18)
select si.reg_number,si.student_name,sm.semester,sm.marks from pc_student_info si join pc_student_marks sm on si.reg_number=sm.reg_number  where si.email_id is not null;

19)
select upper(student_name) as Name,upper(branch) as branch  from pc_student_info;

20)
select lower(subject_code),lower(subject_name),weightage from pc_subject_master;

21)
select concat(student_name,' with ',reg_number,' is studying in Branch',branch) from pc_student_info;

22)

select reg_number,date_format(date_of_birth,'%Y/%m/%d') from pc_student_info;

	
select reg_number,date_format(date_of_birth,'%M %d,%Y') from pc_student_info;

23)

select student_name,contact_number,email_id, (datediff(current_date,date_of_birth))/365 from pc_student_info;

select student_name,contact_number,email_id, round((datediff(current_date,date_of_birth))/365) as age from pc_student_info;

select student_name,contact_number,email_id, ceil((datediff(current_date,date_of_birth))/365) as age from pc_student_info;

select student_name,contact_number,email_id, floor((datediff(current_date,date_of_birth))/365) as age from pc_student_info;



 Day7 : 1st-July-2024
-----------------------------   
24)

select sm.semester,si.reg_number,si.student_name,avg(sm.marks) from pc_student_info si join pc_student_marks sm on si.reg_number=sm.reg_number group by sm.semester,si.reg_number,si.student_name;


select si.reg_number,si.student_name,sm.semester,avg(sm.marks) from pc_student_info si join pc_student_marks sm on si.reg_number=sm.reg_number group by sm.semester,si.reg_number;


select si.student_name,sm.semester,avg(sm.marks) from pc_student_info si join pc_student_marks sm on si.reg_number=sm.reg_number group by sm.semester,si.student_name;


select si.reg_number,si.student_name,sm.semester,avg(sm.marks) from pc_student_info si join pc_student_marks sm on si.reg_number=sm.reg_number group by sm.semester,si.reg_number,si.student_name;



select sm.semester,avg(sm.marks) from pc_student_info si join pc_student_marks sm on si.reg_number=sm.reg_number group by sm.semester;

25)

select max(marks) from pc_student_marks;

select reg_number from pc_student_marks where marks=(select max(marks) from pc_student_marks);

select * from pc_student_info where reg_number in (select reg_number from pc_student_marks where marks=(select max(marks) from pc_student_marks);


select si.reg_number,si.student_name,sm.marks from pc_student_info si join pc_student_marks sm on
si.reg_number=sm.reg_number where sm.marks=(select max(marks) from pc_student_marks);


26)

select si.reg_number,si.student_name,sm.marks from pc_student_info si join pc_student_marks sm on
si.reg_number=sm.reg_number where sm.marks=(select max(marks) from pc_student_marks where subject_code='EI05IP');

27)

mysql> select count(*) as 'number of candidates eligible for scholarship' from pc_student_result where is_eligible_scholarship='Y';

28)

select sr.semester,si.reg_number,si.student_name,max(sr.gpa) from pc_student_result sr join pc_Student_info si on sr.reg_number=si.reg_number 
where sr.gpa in (select max(gpa) from pc_student_result group by semester)
group by sr.semester,si.reg_number,si.student_name;


29)

select si.reg_number,si.student_name,sr.gpa,sr.is_eligible_scholarship from pc_student_info si join pc_student_result sr on si.reg_number=sr.reg_number where sr.is_eligible_scholarship='Y';

select si.*,sr.gpa,sr.is_eligible_scholarship from pc_student_info si join pc_student_result sr on si.reg_number=sr.reg_number where sr.is_eligible_scholarship='Y';


30)

select semester,count(reg_number) from pc_student_result group by semester;

select semester,sum(gpa) from pc_student_result group by semester;


select semester,count(reg_number),sum(gpa) from pc_student_result group by semester;


select semester,count(reg_number) as count_of_student, sum(gpa) as total_gpa  from pc_student_result group by semester;

select semester,count(reg_number) as count_of_student, sum(gpa) as total_gpa,(sum(gpa)/count(reg_number)) as avg_gpa from pc_student_result group by semester;


31)

select si.reg_number,si.student_name,sr.semester,sr.gpa from pc_student_info si join pc_student_result sr on si.reg_number=sr.reg_number;


create view PC_STUDENT_GPA AS select si.reg_number,si.student_name,sr.semester,sr.gpa from pc_student_info si join pc_student_result sr on si.reg_number=sr.reg_number;

32)

select * from pc_student_gpa where gpa>5;


33)

select si.reg_number,si.student_name,sr.semester,avg(sr.gpa) as avg_gpa from pc_student_info si join pc_student_result sr on si.reg_number=sr.reg_number group by sr.semester,si.reg_number,si.student_name;

create view PC_STUDENT_AVG_GPA AS select si.reg_number,si.student_name,sr.semester,avg(sr.gpa) as avg_gpa from pc_student_info si join pc_student_result sr on si.reg_number=sr.reg_number group by sr.semester,si.reg_number,si.student_name;

34)
select * from pc_student_avg_gpa where avg_gpa>7;

select reg_number,student_name,email_id from pc_student_avg_gpa where vg_gpa>7;


35)

select reg_number,student_name,ifnull(email_id,'no valid email address') from pc_student_info;

select reg_number,student_name,COALESCE(email_id,'no valid email address') from pc_student_info;


36)


select si.reg_number,si.student_name,si.branch, 
CASE si.branch WHEN 'ECE' THEN 'Electronics and Communication Engineering' 
WHEN 'MCA' THEN 'Master Computer Application'           
WHEN 'MBA' THEN 'Master In Business Administration'           
ELSE 'this is not in the case'
END  as 'branch_full_form' from pc_student_info si;


Day8 : 2-July-2024   
----------------------------
1) MySQL Stored Procedure and Functions
2) MySQL Index
3) Database Normalization


Stored Procedure
--------------------------

use ums;

delimiter //

CREATE PROCEDURE showStudentDetails (IN r_number VARCHAR(20), OUT name VARCHAR(40),OUT email VARCHAR(40), OUT branch_1 VARCHAR(40))
       BEGIN
         SELECT student_name,email_id,branch INTO name,email,branch_1 FROM pc_student_info
         WHERE reg_number = r_number;
       END//

delimiter ;


call showStudentDetails('MB111305',@name,@email,@branch);

select @name,@email,@branch;


Function
-------------------------
delimiter //

CREATE FUNCTION showStudent(r_number VARCHAR(20))
 RETURNS VARCHAR(100) DETERMINISTIC
BEGIN
    DECLARE details VARCHAR(100);
    SELECT CONCAT('Name : ',student_name,', Branch: ',branch,', Email:',email_id) into details FROM pc_student_info WHERE reg_number=r_number;
 RETURN (details);
 END// 

delimiter ;


select showStudent('MB111305');


select showStudent('MB111305') as Student_Details;





Write a stored procedure and function to perform calc application
------------------------------------------------------------------------------------------
delimiter //


CREATE PROCEDURE add_numbers(IN a INT,IN b INT, OUT result INT)
 x int := 30;  
       BEGIN
         result:=x ;      
 END//


delimiter ;

call add_numbers(100,20,@result);

select @result;


Assignment
-------------------
show databases;
create database pc_company;
use pc_company;

create table employee(
id int primary key,
name text,
salary float
); 

show tables;
desc employee;
describe employee;


insert into employee values(101,'AMOL',10000);
insert into employee values(102,'SACHIN',20000);
insert into employee values(103,'MOHAN',30000);



Create a Stored procdure with name showEmployeeDetails(in id, out nm text,out sal float) to display name and salary of the employee based on id passed to the stored procedure;


Create a Function  with name showEmpDetails(in id) to return name and salary of the employee based on id passed to the function;




Day9 : 3-July-2024   
----------------------------
1) TRANSACTION (COMMIT,ROLLBACK)
2) ACID
3) Database backup and restore 
4) Database Normlaization
4) Online SQL Practice ->https://www.sql-practice.com/
5) Interview Questions -
   https://trainings.internshala.com/blog/rdbms-interview-questions-and-answers/


drop database bank;
create database bank;
use bank;
create table accounts(accno int primary key ,name text,balance float);
insert into accounts values(101,'AMOL',12000);
insert into accounts values(102,'SACHIN',22000);
insert into accounts values(103,'AMOL',32000);

select * from accounts;



BEGIN / START TRANSACTION command is used to start the transaction.

1) SET autocommit = 0;  
1) SET autocommit = OFF;  
2) BEGIN;
3) START TRANSACTION;


COMMIT;  / END TRANSACTION  successfull execution

COMMIT;


ROLLBCK;  abort the trasnaction
 
ROLLBACK;




MYSQL BACKUP/RESTORE
--------------------------------------------
https://phoenixnap.com/kb/how-to-backup-restore-a-mysql-database

BACKUP
--------
C:\Program Files\MySQL\MySQL Server 8.0\bin>mysqldump.exe -u root -p company > company_db.sql

RESTORE
-------------

CREATE DATABASE COMPANY;

C:\Program Files\MySQL\MySQL Server 8.0\bin> mysql -u root -p company < company_db.sql



mysqldump.exe -u root -p bank > bank_db.sql


mysql -u root -p bank < bank_db.sql
mysql -u root -p bank_db < bank_db.sql
mysql -u root -p a_ums < d:\VISHAL_SIR\ums.sql







SQL opeartors
-----------------------
AND, OR,IN, LIKE, NOT LIKE
UNION
UNION ALL

 



-----------------------------------------------------------------------------------------------------------------------------------------

Day10 : 4-July-2024   
----------------------------
SQL Window Functions
-------------------------------
ROW_NUMBER()
RANK()
DENSE_RANK() .
LEAD()
LAG()





SQL CLAUSE SEQUENCE
-------------------------------------

SELECT DISTINCT column, AGG_FUNC(column_or_expression), …
FROM mytable
    JOIN another_table
      ON mytable.column = another_table.column
    WHERE constraint_expression
    GROUP BY column
    HAVING constraint_expression
    ORDER BY column ASC/DESC
    LIMIT no_of_rows to display OFFSET rows_to_skip;







mysql> CREATE TABLE t (qty INT, price INT);
mysql> INSERT INTO t VALUES(3, 50), (5, 60);
mysql> CREATE VIEW v AS SELECT qty, price, qty*price AS value FROM t;
mysql> SELECT * FROM v;


---------------------------------------------------------------------------------------------------
MYSQL EXPLAIN AND ANALYZE
------------------------------------------------------------------------------------------------
select * from pc_student_info where student_name='Pradeep';

explain analyze select * from pc_student_info where student_name='Pradeep';

explain analyze select * from pc_student_info where reg_number='MB222305';

explain analyze select * from pc_student_info where contact_number='8239947383';

explain analyze select * from pc_student_info where address='Warje Pune';

create index addr_index on pc_student_info(address);

desc pc_student_info;

explain analyze select * from pc_student_info where address='Warje Pune';




select e.*,d.name from employee e join department d on e.dept_id=d.id;


select d.id,d.name,count(e.id) from employee e join department d on e.dept_id=d.id 
GROUP BY d.id,d.name;


select d.id,d.name,sum(e.salary) from employee e join department d on e.dept_id=d.id 
GROUP BY d.id,d.name;


select d.id,d.name,avg(e.salary) from employee e join department d on e.dept_id=d.id 
GROUP BY d.id,d.name;


select d.id,d.name,max(e.salary) from employee e join department d on e.dept_id=d.id 
GROUP BY d.id,d.name;

select d.id,d.name,min(e.salary) from employee e join department d on e.dept_id=d.id 
GROUP BY d.id,d.name;



select d.id,d.name,count(e.id),sum(e.salary),avg(e.salary),max(e.salary),min(e.salary) from employee e join department d on e.dept_id=d.id 
GROUP BY d.id,d.name;



select d.id,d.name,count(e.id),sum(e.salary),avg(e.salary),max(e.salary),min(e.salary) from employee e join department d on e.dept_id=d.id 
GROUP BY d.id,d.name
HAVING count(e.id)=2
;



select d.id,d.name,count(e.id),sum(e.salary),avg(e.salary),max(e.salary),min(e.salary) from employee e join department d on e.dept_id=d.id 
GROUP BY d.id,d.name
HAVING max(e.salary) < 150000
ORDER BY d.name DESC
LIMIT 2 OFFSET 0
;



MySQL - RANK vs DENSE_RANK vs ROW_NUMBER - Different Tie Handling Approaches
-------------------------------------------------------------------------------------------------------------------------------

CREATE TABLE StudentScores
    (`gender` varchar(1), `student` varchar(8), `score` int)
;

INSERT INTO StudentScores
    (`gender`, `student`, `score`)
VALUES
    ('M', 'Tobi', 92),
    ('M', 'Tom', 92),
    ('M', 'Sam', 89),
    ('M', 'Ron', 100),
    ('F', 'Mary', 97),
    ('F', 'Emily', 95),
    ('F', 'Jennifer', 89),
    ('F', 'Lori', 89),
    ('F', 'Audra', 84);




-- ROW_NUMBER breaks the tie
--------------------------------------------

SELECT *
	,ROW_NUMBER() OVER (
		ORDER BY score DESC
		) AS RowNum
FROM StudentScores


-- RANK() keeps the tie and skip numbers
-------------------------------------------------------------
SELECT *
	,RANK() OVER (
		ORDER BY score DESC
		) AS RankNum
FROM StudentScores;


-- DENSE_RANK() keeps the tie as well, but does NOT skip numbers
----------------------------------------------------------------------------------------------
SELECT *
	,DENSE_RANK() OVER (
		ORDER BY score DESC
		) AS DenseRankNum
FROM StudentScores;





SELECT *
	,ROW_NUMBER() OVER (
		ORDER BY score DESC
		) AS RONUMBER
                   ,RANK() OVER (
		ORDER BY score DESC
		) AS RankNum
                   ,DENSE_RANK() OVER (
		ORDER BY score DESC
		) AS DenseRankNum
	
FROM StudentScores;



SELECT *
	,lead(score) OVER (
		ORDER BY score DESC
		) AS  lead_value

	,lag(score) OVER (
		ORDER BY score DESC
		) AS  lead_value
                   	
FROM StudentScores;


----------------------------------------

The LEAD() and LAG() function in MySQL are used to get preceding and succeeding value of any row within its partition. These functions are termed as nonaggregate Window functions.



SELECT *
	,lead(score,3) OVER (
		ORDER BY score DESC
		) AS  lead_value

	,lag(score,3) OVER (
		ORDER BY score DESC
		) AS  lead_value
                   	
FROM StudentScores;


SELECT *
	,lead(score,3,0) OVER (
		ORDER BY score DESC
		) AS  lead_value

	,lag(score,3,0) OVER (
		ORDER BY score DESC
		) AS  lead_value
                   	
FROM StudentScores;








