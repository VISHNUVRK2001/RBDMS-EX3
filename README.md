# RBDMS-EX3

QUERIES:

1)Creating the Database and use the database:
mysql>create database socialnetwork1;
mysql>use socialnetwork1;

2) Creating Table users, friends, userprofile:

mysql>create table users1(id int NOT NULL AUTO_INCREMENT, name varchar(40),email varchar(50),address varchar(50),dob TIMESTAMP, isactive tinyint(1),regon TIMESTAMP,logon TIMESTAMP,gender char(1),PRIMARY KEY(id));
mysql> create table friends1(id int NOT NULL AUTO_INCREMENT,userid int(10) UNSIGNED  NOT NULL,friendname varchar(30),PRIMARY KEY(id));
mysql>create table userprofile1(id int(10),userid int(10),location varchar(20));

3)Inserting the values to the tables:

(i) Setting the limit for auto increment field:
mysql> alter table users1 auto_increment=101;
mysql>alter table friends1 auto_increment=11;
(ii) Insert values to the table –users1:
mysql>insert into users1(name,email,address,dob,isactive,regon,logon)values
('ravi','ravi199@gmail.com','15-gandhi nagar cbe','1995-5-10',1,'2015-6-15','2017-5-15',’m’);
mysql>insert into users1(name,email,address,dob,isactive,regon,logon)values
('ram','ram1503@gmail.com','25-raja street chennai','1994-10-23',1,'2014-5-1','2017-5-12',’’);
mysql>insert into users1(name,email,address,dob,isactive,regon,logon)values
('kumar','kumarkumar@yahoo.com','165-nehru nagar madurai’,'1995-11-23',1,'2016-5-1',
'2017-5-25,’m’);
mysql>insert into users1(name,email,address,dob,isactive,regon,logon)values
('sam','sam1234@gmail.com','25 att colony cbe’,'1993-9-23',1,'2017-2-1','2017-2-25,’m’);
(iii)Insert the values into friends1 table:
mysql>insert into friends1(userid,friendname)values(101,’sanjay’);
mysql>insert into friends1(userid,friendname)values(101,’mathan’);
mysql>insert into friends1(userid,friendname)values(101,’sarath’);
mysql>insert into friends1(userid,friendname)values(102,’ajay’);
mysql>insert into friends1(userid,friendname)values(102,’gowtham’);
mysql>insert into friends1(userid,friendname)values(102,’adhav’);
mysql>insert into friends1(userid,friendname)values(103,’pranav’);
mysql>insert into friends1(userid,friendname)values(104,’jai’);
mysql>insert into friends1(userid,friendname)values(104,’kathir’);
mysql>insert into friends1(userid,friendname)values(104,’vijay’);
(iv)Insert the values into userprofile1 table:
mysql>insert into userprofile1 values(1,101,’cbe’);
mysql>insert into userprofile1 values(2,102,’chennai’);
mysql>insert into userprofile1 values(3,103,’madurai’);
mysql>insert into userprofile1 values(4,104,’cbe’);
4) Fetch the most recent 5 registered users
mysql>select *from users1 ORDER BY id DESC limit 0,5;
5) Fetch all the friends of user_id user x 
mysql>select name from friends1 where userid=101;

6) Fetch all the users who are above 21 years old
mysql>select name from users1 where TIMESTAMPDIFF(YEAR,dateofbirth,CURDATE())>21;
 
7) Find the count of users who signed-up with gmail Id. (ie. users' email ends with 
@gmail.com) 

mysql>select count(id) from users1 where email LIKE ‘%gmail.com’

8) Fetch all the users who registered last month 
mysql>select name from users1 where MONTH(regon)=2;

9) Fetch all users of ‘Chennai’ location
select userid from userprofile1 where location=”chennai”;

10) Find actively monthly and weekly users count. ie. Count of users who have logged-in 
in the last 15 days. 

select count(id) from users1 where DATE(logon) BETWEEN ‘2017-05-01’ AND ‘2017-05-31’;

11) Find how many users who have not mentioned their gender
mysql>select count(id) from users1 where gender =’’;
