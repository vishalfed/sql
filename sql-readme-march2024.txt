Day1- 7-Mar-2024
-----------------
RDBMS - MYSQL8.0


Application/Software/Product/Program
---------------------------------------
1)Web Application
2)Mobile Application
3)Desktop Application
4)Hybrid Application
5)Single Page Application
6)PWA(Progressive Web Application)


Enterprise/Business ORgnizations -> do the business -> make a money by providing the services to their customers

Banks
Hotels
Hospitals
Colleges
School
Transport Agencies



Why we develop the applications?

  To provide services


4 layers (logical separation of the code)
  tier   (physical separation of the code)



1) Presentation Layer -> Code written to provide input screen/response th the user
2) Service Layer -> Logical iplementation of business rules
3) Data Access Layer -> Code written to acess the data from database
4) Data Layer -> It is source of data


C - CREATE
R - READ
U - UPDATE
D - DELETE

RDBMS-> Relational Database Management System

Data is getting stored in the forms rows nd columns

Relation -> Table


class-table-entity
variable-column/field/attribute


class Employee{
int id;
String name;
double salary;
}

Employee e1=new Employee(101,'Amol',1000);

---------------------------
Employee
---------------------------
ID       NAME     SALARY
---------------------------
101      Amol     1000



XML
----
<employee>
<id>101</id>
<name>Amol</name>
<salary>1000</salary>
</employee>

JSON
------
employee={id:101,name:'Amol',salary:1000};


MySQL follows Client-Server
----------------------------

CUI -> MySQL Client
GUI -> MySQL Work Bench

https://dev.mysql.com/downloads/file/?id=526408



Default user :root
Password     :<given_at_installation_time>
Default port :3306

jdbcurl : jdbc:mysql://localhost:3306/test



To display all the databases;
--------------------------------
show databases;

To create a databse
--------------------------------
create database sql_march_2024;

select databse
--------------------------------
use sql_march_2024;


show all tables
--------------------------------
show tables;


create table employee
--------------------------------
create table employee(
id int primary key,
name text not null,
salary double not null
);


describe table employee
--------------------------------
desc employee;


insert records in employee table
--------------------------------

insert into employee values(1,'Amol',1000);
insert into employee(id,name,salary)values(3,'Amit',3000);


display records in employee table
--------------------------------
select * from employee;

SQL-Queries
-----------
DDL -> CREATE,ALTER,DROP
DML -> INSERT,UPDATE,DELETE
DRL -> SELECT
TCL -> COMMIT,ROLLBACK



Day2- 8-Mar-2024
-----------------
https://www.javatpoint.com/mysql-tutorial

database - school

 id  (primary key)
 first_name not null
 last_name not null
 mobile unique 
 email  unique
 dob  not null 
 class (1-10)
 gender(M|F|N) 
 city  
 state


1) Database Creation
--------------------
CREATE DATABASE SCHOOL;

2) Database Section
-------------------
USE SCHOOL;
 
3) Table Creation
-------------------

CREATE TABLE STUDENTS(
ID INT PRIMARY KEY,
FIRST_NAME VARCHAR(20) NOT NULL,
LAST_NAME VARCHAR(20) NOT NULL,
EMAIL VARCHAR(30) UNIQUE,
MOBILE VARCHAR(30) UNIQUE,
DOB DATE NOT NULL,
CLASS INT,
GENDER CHAR,
CITY TEXT,
STATE TEXT
);



3) Table Description
-------------------
DESC/DESCRIBE STUDENTS;


3) TABLE ALTERATION
-------------------
ALTER TABLE STUDENTS DROP COLUMN STATE;

ALTER TABLE STUDENTS ADD COLUMN STATE TEXT NOT NULL;

ALTER TABLE STUDENTS MODIFY COLUMN EMAIL VARCHAR(30) UNIQUE NOT NULL;

ALTER TABLE STUDENTS MODIFY COLUMN MOBILE VARCHAR(10) UNIQUE NOT NULL;

ALTER TABLE STUDENTS MODIFY COLUMN CLASS INT CHECK (CLASS>=1 AND CLASS<=10);

ALTER TABLE STUDENTS MODIFY COLUMN CLASS INT CHECK (CLASS BETWEEN 1 AND 10);

ALTER TABLE STUDENTS MODIFY COLUMN GENDER CHAR CHECK (GENDER IN ('M','F','N')) DEFAULT 'M';


ALTER TABLE STUDENTS MODIFY COLUMN GENDER CHAR CHECK (GENDER IN ('M','F','N')) DEFAULT 'M';


INSERT INTO STUDENTS VALUES(1,'AMOL','PATIL','amol@gamil.com','8145567654','1982-07-01',1,'M','Pune','MAHARASHTRA');

INSERT INTO STUDENTS VALUES(2,'AMOL','PATIL','amol1@gamil.com','8145567652','1982-07-01',1,'M','Pune','MAHARASHTRA');

INSERT INTO STUDENTS VALUES(3,'AMOL','PATIL','amol2@gamil.com','8145568652','1982-07-01',5,'X','Pune','MAHARASHTRA');


INSERT INTO STUDENTS(ID,FIRST_NAME,LAST_NAME,EMAIL,MOBILE,DOB,STATE) VALUES(4,'AMOL','PATIL','amol5@gamil.com','9145568652','1982-07-01','MAHARASHTRA');






Day3- 11-Mar-2024
-----------------


ALTER TABLE STUDENTS MODIFY COLUMN DOB DATE NOT NULL CHECK (DOB < sysdate());


INSERT INTO STUDENTS VALUES(8,'AMOL','PATIL','amol2@gamil.com','8145568652','2022-07-01',5,'M','Pune','MAHARASHTRA');



Todays Agenda
--------------
DBMS keys


STUDENTS
----------------------------------------------------------------
SID       REG_ID      NAME  EMAIL             BRANCH_CODE  
------------------------------------------------------------
101       CS-2022-11  AMOL  AMOL@GMAIL.COM    CS 
----------------------------------------------------------------


BRANCH
--------------------------------------------------------
BRANCH_CODE     BRANCH NAME        HOD              
---------------------------------------------------------
CS              Computer Science  XYZ
ME              Mechanical        ABC





1) Super Key

SID
EMAIL
REG_ID
(SID,EMAIL)
(SID,REG_ID)
(SID,EMAIL,REG_ID)


2) CANDIDATE KEY

SID
EMAIL
REG_ID


3) Primary Key

REG_ID

4) Alternate keys

EMAIL
REG_ID

5) Foreign Key

  BRANCH_CODE

6) COMPOSITE KEY 

   (SID,REG_ID)
   (SID,EMAIL)

7) COMPOUND KEY
    (SID,EMAIL,BRANCH_CODE)

8) SURROGATE KEY

    sr_number
    row_number 



CREATE TABLE DEPTS(ID INT PRIMARY KEY,NAME VARCHAR(30));

INSERT INTO DEPTS VALUES(10,'ACCOUNTS');
INSERT INTO DEPTS VALUES(20,'SALES');
INSERT INTO DEPTS VALUES(30,'REVENU');
INSERT INTO DEPTS VALUES(40,'COLLECTION');

select * from depts;


CREATE TABLE EMPS(ID INT PRIMARY KEY,NAME VARCHAR(30),DEPT_ID INT,
FOREIGN KEY (DEPT_ID)  REFERENCES DEPTS(ID));


CREATE TABLE EMPS(ID INT PRIMARY KEY,NAME VARCHAR(30),DEPT_ID INT,
FOREIGN KEY (DEPT_ID)  REFERENCES DEPTS(ID) ON DELETE CASCADE ON UPDATE CASCADE);

CREATE TABLE EMPS(ID INT PRIMARY KEY,NAME VARCHAR(30),DEPT_ID INT,
FOREIGN KEY (DEPT_ID)  REFERENCES DEPTS(ID) ON DELETE SET NULL ON UPDATE CASCADE);


INSERT INTO EMPS VALUES(1,'AMOL',10);
INSERT INTO EMPS VALUES(2,'SACHIN',10);
INSERT INTO EMPS VALUES(3,'SUNIL',20);
INSERT INTO EMPS VALUES(4,'MOHAN',20);

INSERT INTO EMPS VALUES(5,'MOHAN',50);

select * from emps;

Day4- 12-Mar-2024
-----------------
SQL Queries and Operators,Functions,Index

drop table students;

create table students(
id int primary key,
first_name text,
last_name text,
dob date,
email text,
age int,
mobile text(10),
city text
);

INSERT INTO STUDENTS VALUES(101,'ram','patil','2015-05-11','ram@gmail.com',34,'8156678654','pune');
INSERT INTO STUDENTS VALUES(102,'sachin','patil','2011-01-12','sachin@gmail.com',34,'8156678654','pune');
INSERT INTO STUDENTS VALUES(103,'pradeep','patil','2010-11-13','pradeep@gmail.com',34,'8156678654','pune');
INSERT INTO STUDENTS VALUES(104,'mohan104','patil','2013-09-11','mohan@gmail.com',34,'8156678654','pune');
INSERT INTO STUDENTS VALUES(105,'mohan105','patil','2013-09-11','mohan@gmail.com',34,'8156678654','nagpur');
INSERT INTO STUDENTS VALUES(106,'mohan106','patil','2013-09-11','mohan@gmail.com',34,'8156678654','nagpur');
INSERT INTO STUDENTS VALUES(107,'mohan107','patil','2013-09-11','mohan@gmail.com',34,'8156678654','pune');
INSERT INTO STUDENTS VALUES(108,'mohan108','patil','2013-09-11','mohan@gmail.com',34,'8156678654','pune');
INSERT INTO STUDENTS VALUES(109,'mohan109','patil','2013-09-11','mohan@gmail.com',34,'8156678654','solpaur');
INSERT INTO STUDENTS VALUES(110,'mohan110','patil','2013-09-11','mohan@gmail.com',34,'8156678654','solapur');
INSERT INTO STUDENTS VALUES(115,'mohan115','patil','2013-09-11','mohan@gmail.com',34,'8156678654','pune');
INSERT INTO STUDENTS VALUES(112,'mohan112','patil','2013-09-11','mohan@gmail.com',34,'8156678654','banglore');
INSERT INTO STUDENTS VALUES(117,'mohan117','patil','2013-09-11','mohan@gmail.com',34,'8156678654','banglore');
INSERT INTO STUDENTS VALUES(116,'mohan116','patil','2013-09-11','mohan@gmail.com',34,'8156678654','mumbai');
INSERT INTO STUDENTS VALUES(111,'mohan111','patil','2013-09-11','mohan@gmail.com',34,'8156678654','mumbai');




SELECT * FROM STUDENTS;

SELECT ID,FIRST_NAME,LAST_NAME,EMAIL FROM STUDENTS;

SELECT ID,CONCAT(FIRST_NAME,' ',LAST_NAME),EMAIL FROM STUDENTS;
 

SELECT ID,CONCAT(FIRST_NAME,' ',LAST_NAME) AS NAME ,EMAIL FROM STUDENTS;

 
SELECT ID,UPPER(CONCAT(FIRST_NAME,' ',LAST_NAME)) AS NAME ,UPPER(EMAIL) FROM STUDENTS;



SELECT * FROM STUDENTS WHERE CITY='PUNE';


SELECT * FROM STUDENTS WHERE CITY='pune';



SELECT * FROM STUDENTS WHERE CITY='solapur' OR CITY='MUMBAI' OR CITY='NAGPUR';

SELECT * FROM STUDENTS WHERE CITY IN ('solapur','MUMBAI','NAGPUR');


UPDATE STUDENTS SET AGE=40 WHERE CITY='PUNE';

UPDATE STUDENTS SET AGE=30 WHERE CITY='MUMBAI';

UPDATE STUDENTS SET AGE=20 WHERE CITY='SOLAPUR';

SELECT * FROM STUDENTS WHERE AGE>=34 AND AGE<=40;

SELECT * FROM STUDENTS WHERE AGE BETWEEN 34 AND 40;


UPDATE STUDENTS SET MOBILE=NULL WHERE CITY='NAGPUR';


SELECT * FROM STUDENTS WHERE MOBILE=NULL;

SELECT * FROM STUDENTS WHERE MOBILE IS NULL;

SELECT * FROM STUDENTS WHERE MOBILE IS NOT NULL;


SELECT ID,FIRST_NAME,MOBILE FROM STUDENTS;


SELECT ID,FIRST_NAME,IFNULL(MOBILE,'MOBILE NOT AVAILABLE') FROM STUDENTS;

SELECT ID,FIRST_NAME,ISNULL(MOBILE) FROM STUDENTS;

SELECT ID,FIRST_NAME,COALESCE(MOBILE,'MOBILE NOT AVAILABLE') FROM STUDENTS;


SELECT ID,FIRST_NAME,MOBILE FROM STUDENTS WHERE FIRST_NAME LIKE 'm%';
SELECT ID,FIRST_NAME,MOBILE FROM STUDENTS WHERE FIRST_NAME NOT LIKE 'M%';

SELECT ID,FIRST_NAME,MOBILE FROM STUDENTS WHERE LENGTH(FIRST_NAME)=3;

ALTER TABLE STUDENTS ADD COLUMN MARKS INT CHECK(MARKS BETWEEN 0 AND 100) DEFAULT 20;


UPDATE STUDENTS SET MARKS=50 WHERE CITY='PUNE';

UPDATE STUDENTS SET MARKS=70 WHERE CITY='MUMBAI';

UPDATE STUDENTS SET MARKS=45 WHERE CITY='SOLAPUR';

UPDATE STUDENTS SET MARKS=75 WHERE CITY='BANGLORE';

UPDATE STUDENTS SET MARKS=35 WHERE CITY='NAGPUR';


Aggregate function/ single row function/ window functions

min(),max(),sum(),avg,(),count()


SELECT MAX(MARKS),MIN(MARKS),SUM(MARKS),AVG(MARKS),COUNT(MARKS) FROM STUDENTS;


SELECT CITY,MAX(MARKS),MIN(MARKS),SUM(MARKS),AVG(MARKS),COUNT(MARKS) FROM STUDENTS GROUP BY CITY;


SELECT CITY,MAX(MARKS),MIN(MARKS),SUM(MARKS),AVG(MARKS),COUNT(MARKS) FROM STUDENTS GROUP BY CITY ORDER BY CITY;

SELECT CITY,MAX(MARKS),MIN(MARKS),SUM(MARKS),AVG(MARKS),COUNT(MARKS) FROM STUDENTS GROUP BY CITY ORDER BY CITY DESC;


SELECT MAX(MARKS) FROM STUDENTS;


SELECT * FROM STUDENTS WHERE MARKS=(SELECT MAX(MARKS) FROM STUDENTS);

SELECT * FROM STUDENTS WHERE MARKS=(SELECT MIN(MARKS) FROM STUDENTS);


SELECT * FROM STUDENTS ORDER BY MARKS;

SELECT * FROM STUDENTS ORDER BY MARKS LIMIT 3;


SELECT * FROM STUDENTS ORDER BY MARKS DESC;

SELECT * FROM STUDENTS ORDER BY MARKS DESC LIMIT 3;


SELECT * FROM STUDENTS ORDER BY MARKS DESC LIMIT 3 OFFSET 3;

SELECT DATE_FORMAT(DOB,'%D %b %Y') FROM STUDENTS;



Day5- 13-Mar-2024
-----------------
Database JOINS

- Natural JOINS
1) INNER JOIN
2) OUTER JOIN
3) LEFT JOIN/LEFT OUTER JOIN
3) RIGHT JOIN/RIGHT OUTER JOIN
4) FULL OUTER JOIN
5) CROSS JOIN
6) SELF JOIN


CREATE TABLE SUBJECTS(SUBJECT_CODE INT PRIMARY KEY,NAME TEXT);

INSERT INTO SUBJECTS VALUES(10,'MATH');
INSERT INTO SUBJECTS VALUES(20,'ENGLISH');
INSERT INTO SUBJECTS VALUES(30,'HISTORY');
INSERT INTO SUBJECTS VALUES(40,'MARATHI');
INSERT INTO SUBJECTS VALUES(50,'SOCIAL STUDIES');


CREATE TABLE TEACHERS(ID INT PRIMARY KEY,NAME TEXT,SUBJECT_CODE INT);

INSERT INTO TEACHERS VALUES(1,'AMOL',10);
INSERT INTO TEACHERS VALUES(2,'SACHIN',20);
INSERT INTO TEACHERS VALUES(3,'PRADEEP',30);
INSERT INTO TEACHERS VALUES(4,'SUNIL',30);


+--------------+----------------+
| SUBJECT_CODE | NAME           |
+--------------+----------------+
|           10 | MATH           |
|           20 | ENGLISH        |
|           30 | HISTORY        |
|           40 | MARATHI        |
|           50 | SOCIAL STUDIES |
+--------------+----------------+

+----+---------+--------------+
| ID | NAME    | SUBJECT_CODE |
+----+---------+--------------+
|  1 | AMOL    |           10 |
|  2 | SACHIN  |           20 |
|  3 | PRADEEP |           30 |
|  4 | SUNIL   |           30 |
+----+---------+--------------+


INNER JOIN
-----------

SELECT T.ID,T.NAME,S.SUBJECT_CODE,S.NAME FROM TEACHERS T JOIN SUBJECTS S ON T.SUBJECT_CODE=S.SUBJECT_CODE;
 
SELECT T.ID,T.NAME,S.SUBJECT_CODE,S.NAME FROM TEACHERS T INNER JOIN SUBJECTS S ON T.SUBJECT_CODE=S.SUBJECT_CODE;
 
SELECT TEACHERS.ID,TEACHERS.NAME,SUBJECTS.SUBJECT_CODE,SUBJECTS.NAME FROM TEACHERS JOIN SUBJECTS  ON TEACHERS.SUBJECT_CODE=SUBJECTS.SUBJECT_CODE;
 
LEFT JOIN/ LEFT OUTER JOIN
-----------------------------

SELECT T.ID,T.NAME,S.SUBJECT_CODE,S.NAME FROM TEACHERS T LEFT JOIN SUBJECTS S ON T.SUBJECT_CODE=S.SUBJECT_CODE;
 

SELECT T.ID,T.NAME,S.SUBJECT_CODE,S.NAME FROM TEACHERS T LEFT OUTER JOIN SUBJECTS S ON T.SUBJECT_CODE=S.SUBJECT_CODE;
 
ROGHT JOIN/ RIGHT OUTER JOIN
-----------------------------

SELECT T.ID,T.NAME,S.SUBJECT_CODE,S.NAME FROM TEACHERS T RIGHT JOIN SUBJECTS S ON T.SUBJECT_CODE=S.SUBJECT_CODE;
 

SELECT T.ID,T.NAME,S.SUBJECT_CODE,S.NAME FROM TEACHERS T RIGHT OUTER JOIN SUBJECTS S ON T.SUBJECT_CODE=S.SUBJECT_CODE;
 
CROSS JOIN
------------
SELECT T.ID,T.NAME,S.SUBJECT_CODE,S.NAME FROM TEACHERS T CROSS JOIN SUBJECTS S;

 

UNION /UNION ALL
---------------------------

SELECT SUBJECT_CODE FROM TEACHERS
UNION
SELECT SUBJECT_CODE FROM SUBJECTS;


SELECT SUBJECT_CODE FROM TEACHERS
UNION ALL
SELECT SUBJECT_CODE FROM SUBJECTS;





SELF JOIN
------------

CREATE TABLE EMPLOYEES(
ID INT PRIMARY KEY,
FIRST_NAME TEXT,
LAST_NAME TEXT,
MGR_ID INT 
);

INSERT INTO EMPLOYEES VALUES(101,'SUNIL','PATIL',NULL);
INSERT INTO EMPLOYEES VALUES(102,'SACHIN','PATIL',101);
INSERT INTO EMPLOYEES VALUES(103,'AMOL','PATIL',101);
INSERT INTO EMPLOYEES VALUES(104,'RAJENDRA','PATIL',102);
INSERT INTO EMPLOYEES VALUES(105,'PRAKASH','PATIL',102);
INSERT INTO EMPLOYEES VALUES(106,'SUMIT','PATIL',104);

SELECT * FROM EMPLOYEES;


SELECT e.id,
concat(e.FIRST_NAME,' ',e.LAST_NAME) AS EMPLOYEE_NAME,
m.id,
concat(m.FIRST_NAME,' ',m.LAST_NAME) AS MANAGER_NAME
FROM EMPLOYEES e JOIN EMPLOYEES m ON e.mgr_id=m.id;



CREATE INDEX fn_index ON students(first_name);

  



----------------------------------

https://github.com/vishalfed/sql


Day6- 14-Mar-2024
-----------------
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
--------------------------------------

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






Day7- 15-Mar-2024
------------------


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





SQL Activity 3
----------------

1) 

SELECT * FROM PC_STUDENT_INFO WHERE EMAIL_ID IS NOT NULL;
SELECT * FROM PC_STUDENT_INFO WHERE EMAIL_ID IS NULL;


2)
 select count(*) from pc_student_info;
 select branch,count(*) from pc_student_info group by branch;
 
3)

select reg_number,marks from pc_student_marks where marks>50;


4)

select si.reg_number,si.student_name,sr.gpa
from pc_student_info si join pc_student_result sr
on si.reg_number=sr.reg_number;



select si.reg_number,si.student_name,sr.gpa
from pc_student_info si join pc_student_result sr
on si.reg_number=sr.reg_number order by gpa;


select si.reg_number,si.student_name,sr.gpa
from pc_student_info si join pc_student_result sr
on si.reg_number=sr.reg_number order by gpa desc;

5) 

select * from pc_student_info;
select * from pc_student_info order by student_name;


6)

select * from pc_student_info;
select * from pc_student_info order by date_of_birth desc;
select reg_number,student_name,FLOOR(DATEDIFF(CURRENT_DATE, date_of_birth)/365) AS AGE from pc_student_info order by age;

Day8- 16-Mar-2024
------------------
7)

select 
     si.reg_number,
     si.student_name,
     sb.subject_name,
     sm.semester,
     sm.marks
from pc_student_info si join pc_subject_master sb join pc_student_marks sm
     on       
     si.reg_number=sm.reg_number and sb.subject_code=sm.subject_code;


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

Day9- 18-Mar-2024
------------------

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


24)
select si.reg_number,si.student_name,sm.semester,avg(sm.marks) from pc_student_info si join pc_student_marks sm on si.reg_number=sm.reg_number group by sm.semester,si.reg_number,si.student_name;


select sm.semester,avg(sm.marks) from pc_student_info si join pc_student_marks sm on si.reg_number=sm.reg_number group by sm.semester;

25)

select max(marks) from pc_student_marks;

select si.* from pc_student_info si join pc_student_marks sm on si.reg_number=sm.reg_number where marks=(select max(marks) from pc_student_marks);


26)


select max(marks) from pc_student_marks where subject_code='EI05IP';

select si.* from pc_student_info si join pc_student_marks sm on si.reg_number=sm.reg_number where marks=(select max(marks) from pc_student_marks where subject_code='EI05IP');



27) 
select count(*) as scholasrship_eligibility_count from pc_student_Result where is_eligible_scholarship='Yes';


28)

select si.reg_number,si.student_name,sr.semester,max(sr.gpa) from pc_student_info si join pc_student_result sr on si.reg_number=sr.reg_number group by sr.semester,si.reg_number,si.student_name;



Day10- 19-Mar-2024
------------------

29)
select si.reg_number,si.student_name,sr.gpa,sr.is_eligible_scholarship from pc_student_info si join pc_student_result sr on si.reg_number=sr.reg_number where sr.is_eligible_scholarship='YES';

30)
select semester,avg(gpa) from pc_student_result group by semester;

31)

select si.reg_number,si.student_name,sr.semester,sr.gpa from pc_student_info si join pc_student_result sr on si.reg_number=sr.reg_number;


create view PC_STUDENT_GPA AS select si.reg_number,si.student_name,sr.semester,sr.gpa from pc_student_info si join pc_student_result sr on si.reg_number=sr.reg_number;

select * from pc_student_gpa where gpa>5;



32)

select si.reg_number,si.student_name,sr.semester,avg(sr.gpa) as avg_gpa from pc_student_info si join pc_student_result sr on si.reg_number=sr.reg_number group by sr.semester,si.reg_number,si.student_name;


33)
create view PC_STUDENT_AVG_GPA AS select si.reg_number,si.student_name,sr.semester,avg(sr.gpa) as avg_gpa from pc_student_info si join pc_student_result sr on si.reg_number=sr.reg_number group by sr.semester,si.reg_number,si.student_name;


34)
select * from pc_student_avg_gpa where avg_gpa>7;


select reg_number,student_name,email_id from pc_student_info;

35)

select reg_number,student_name,ifnull(email_id,'no valid email address') from pc_student_info;

select reg_number,student_name,COALESCE(email_id,'no valid email address') from pc_student_info;



36)
select si.reg_number,si.student_name,si.branch, 
CASE si.branch WHEN 'ECE' THEN 'Electronics and Communication Engineering' 
WHEN 'MCA' THEN 'Master Computer Application'           
WHEN 'MBA' THEN 'Master In Business Administration'           
ELSE 'this is not in the case'
END from pc_student_info si;








----------------------------

DROP TABLE animals;

CREATE TABLE animals (
     id MEDIUMINT NOT NULL AUTO_INCREMENT,
     name CHAR(30) NOT NULL,
     PRIMARY KEY (id)
);

ALTER TABLE animals AUTO_INCREMENT = 100;

INSERT INTO animals (name) VALUES
    ('dog'),('cat'),('penguin'),
    ('lax'),('whale'),('ostrich');

SELECT * FROM animals;



create table product(id int primary key,name text);

insert into product values(1,'TV');
insert into product values(2,'MOBILE');
insert into product values(3,'ROUTER');
insert into product values(4,'COMPUTER');

select * from product;

create table product_list(id int primary key,name text);

insert into product_list values(1,'Computer');

select * from product_list;




MERGE PRODUCT_LIST AS TARGET
    USING PRODUCT AS SOURCE 
    ON (PRODUCT.ID=PRODUCT_LIST.ID)
    WHEN MATCHED 
    THEN UPDATE
         SET PRODUCT_LIET.NAME = PRODUCT.NAME
    WHEN NOT MATCHED 
    THEN INSERT (ID,NAME)          
         VALUES (PRODUCT.ID,PRODUCT.NAME); 
         
----------------------------------------------------
Day11- 20-Mar-2024
------------------
1) MYSQL TRANSACTION
2) STORED PROCEDURE -> DOESN'T Resturn the value
3) FUNCTION    -> RETURN THE VALUE

TRANSACTION   -> Ineteraction With Database
------------


INSERT
DELETE
UPDATE

CREATE TABLE ACCOUNTS;

CREATE TABLE ACCOUNTS(id int primary key,name text,balance double);

INSERT INTO ACCOUNTS VALUES(1,'AMOL',10000);
INSERT INTO ACCOUNTS VALUES(2,'AMEYA',20000);
INSERT INTO ACCOUNTS VALUES(3,'SUMIT',30000);
INSERT INTO ACCOUNTS VALUES(4,'SUNIL',40000);
INSERT INTO ACCOUNTS VALUES(5,'RAMESH',50000);

SELECT * FROM ACCOUNTS;



https://www.freecodecamp.org/news/how-to-use-mysql-transactions/

To START THE TRANSACTION
----------------------------
BEGIN;
START TRANSACTION;
SET AUTOCOMMIT =0;
SET AUTO COMMIT = OFF;


TO ABORT THE TRANSACTION
--------------------------
ROLLBACK;

TO COMMIT THE TRANSACTION
--------------------------
COMMIT;
 


A -Atomocity
C -Consistency
I -Isolation
D -Durablity



CONSISTENCY
-------------
1. WEAK   -> 1 min,1 hour,1 day
2. STRONG -> Immeditatly after data is changed (STOCK MARKET)
3. EVENTUAL -> Within specified time 



delimiter //


CREATE PROCEDURE showInfo(IN r_number VARCHAR(20),OUT name VARCHAR(20),OUT brnch VARCHAR(20))
       BEGIN
         SELECT student_name,branch INTO name,brnch FROM pc_student_info
         WHERE reg_number=r_number;
       END//

delimiter ;

CALL showInfo('BEEI101204', @name,@branch);

SELECT @name,@branch;


DELIMITER //
CREATE FUNCTION showStudent(r_number VARCHAR(20))
 RETURNS VARCHAR(60) DETERMINISTIC
BEGIN
    DECLARE details VARCHAR(60);
    SELECT CONCAT('Name : ',student_name,', Branch: ',branch) into details FROM pc_student_info_pc WHERE reg_number=r_number;
 RETURN (details);
 END//        
DELIMITER ;

   
SELECT showStudent('BEEI101204');  
   
------------------------



delimiter //

CREATE PROCEDURE showAccountDetails(IN account_id INT,OUT account_name TEXT,OUT account_balance DOUBLE)
       BEGIN
         SELECT name,balance INTO account_name,account_balance FROM        accounts
         WHERE id=account_id;
       END//

delimiter ;

CALL showAccountDetails(1, @name,@balance);

SELECT @name,@balance;




DELIMITER //

CREATE FUNCTION showAccountInfo(account_id INT)
 RETURNS VARCHAR(60) DETERMINISTIC
BEGIN
    DECLARE details VARCHAR(60);
    SELECT CONCAT('Account Name : ',name,', Balance: ',balance) into details FROM accounts WHERE id=account_id;
 RETURN (details);
 END//        
DELIMITER ;

   
SELECT showAccountInfo(1);
SELECT showAccountInfo(2);
SELECT showAccountInfo(3);
SELECT showAccountInfo(4);
SELECT showAccountInfo(5);
  


Day12- 21-Mar-2024
-------------------------------
1) Database Backup and Restore
2) Joins recap
3) Database Normalization
4) Online SQL Practice ->https://www.sql-practice.com/
5) Interview Questions -
   https://trainings.internshala.com/blog/rdbms-interview-questions-and-answers/


create table student(id int primary key,name text,course_id int);

INSERT INTO STUDENT VALUES(1,'SACHIN',10);
INSERT INTO STUDENT VALUES(2,'MOHAN',20);
INSERT INTO STUDENT VALUES(3,'PRADEEP',30);
INSERT INTO STUDENT VALUES(4,'RAM',80);
INSERT INTO STUDENT VALUES(5,'KRISHNA',90);

SELECT * FROM STUDENT;

create table course(course_id int primary key,name text);
INSERT INTO COURSE VALUES(10,'HTML');
INSERT INTO COURSE VALUES(20,'CSS');
INSERT INTO COURSE VALUES(30,'RDBMS');
INSERT INTO COURSE VALUES(40,'JAVA');
INSERT INTO COURSE VALUES(50,'REACT');
INSERT INTO COURSE VALUES(60,'SPRING BOOT');

SELECT * FROM COURSE;


INNER
------
SELECT s.id,s.name,s.course_id,c.name from student s join course c on s.course_id=c.course_id;

LEFT OUTER
-------------


SELECT s.id,s.name,s.course_id,c.name from student s left join course c on s.course_id=c.course_id;

RIGHT OUTER
-------------

SELECT s.id,s.name,s.course_id,c.name from student s right join course c on s.course_id=c.course_id;


CROSS
------

SELECT s.id,s.name,s.course_id,c.name from student s cross join course c;








MYSQL BACKUP/RESTORE
----------------------
https://phoenixnap.com/kb/how-to-backup-restore-a-mysql-database

BACKUP
--------
C:\Program Files\MySQL\MySQL Server 8.0\bin>mysqldump.exe -u root -p company > company_db.sql

RESTORE
-------

CREATE DATABASE COMPANY;

C:\Program Files\MySQL\MySQL Server 8.0\bin> mysql -u root -p company < company_db.sql

---------------------

C:\Program Files\MySQL\MySQL Server 8.0\bin>mysqldump -u root -p ums > d:\SQL_VISHAL_SIR\ums.sql
Enter password: *****


C:\Program Files\MySQL\MySQL Server 8.0\bin>mysql -u root -p ums < d:\SQL_VISHAL_SIR\ums.sql
Enter password: *****

C:\Program Files\MySQL\MySQL Server 8.0\bin>mysql -u root -p test_backup < d:\SQL_VISHAL_SIR\ums.sql
Enter password: *****

C:\Program Files\MySQL\MySQL Server 8.0\bin>

