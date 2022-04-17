# DDL - Create 

create database store;

USE store;

# -- From the Diagram --

create table countries(
code int primary key Not null ,
name varchar(20) Not null,
continent_name varchar(20) 
);


create table users(
id int primary key Not null,
full_name varchar(20) Not null,
email varchar(20) ,
gender char(1) Not null check(gender = 'm' or gender = 'f'),
date_of_birth varchar(15) Not null,
created_at datetime,
country_code int,
foreign key (country_code) references countries(code)
);

create table orders(
id int primary key Not null,
user_id int,
status varchar(6) check(status = 'start' or status ='finish'),
created_at datetime,
foreign key (user_id) references users(id)
);

create table order_products(
order_id int Not null,
product_id int  Not Null,
primary key (order_id,product_id),
quantity int default 0,
foreign key (order_id ) references orders(id),
foreign key (product_id ) references products(id) 
);

create table products(
id int primary key Not null,
name varchar(10) Not null,
price int default 0,
status varchar(10) check(status = 'valid' or status= 'expired'),
created_at datetime default 0
);

# DQL - Select 
Select * From countries;
Select * From users;
Select * From orders;
Select * From order_products;
Select * From products;

# DDL  - continue the other commands for DDL 

# -- Add unique constraint to column " name ". --

Alter Table countries add UNIQUE(name);

# -- Add not null constraint to column " continent_name " --

Alter Table countries Modify continent_name varchar(20) Not null;

# -- Add unique constraint to column " email ". --
Alter Table users add UNIQUE(email);

# /* Add check constraint to column " gender " between 'm' or 'f'
		               in the table above */
			       
# -- Add check constraint to column " status " between 'start' or 'finish'.--
                     -- in the table above --
#  -- Add default value to column " quantity " value 0. --
                     -- in the table order_product above --
                     
# DML - Insert into - table Countries 

Update countries set code = 1234 where code = 1;
Update countries set code = 4444 where code = 2;
Insert into countries values (1234,'Alanoud','Alahsa');
Insert into countries values (4444,'Amjad','Damamm');
Insert into countries values (3029,'Ziyed','Damamm');
Insert into countries values (1111,'Osamah','Damamm');

# DML - Insert into - table users

Update users set created_at = '2017-05-08 12:35:29.123' where id = 1;
Insert into users values (1, 'Alanoud khaled','a@a.com','f','01/08/1997', '12:00',1234);
Insert into users values (2, 'Amjad Ahmed','s@s.com','f','04/08/1996', '2018-05-06 13:35:30.123',4444);
Insert into users values (3, 'Ziyed Khaled','z@z.com','m','10/09/2002', '2019-04-06 16:35:30.123',3029);
Insert into users values (4, 'Osamah Ahmed','o@o.com','m','24/09/2019', '2019-09-06 16:35:29.123',1111);

# DML - insert into - table orders

Insert into orders values (1,1,'finish','2018-05-06 16:35:30.123');
Insert into orders values (2,2,'finish','2018-05-06 18:40:30.124');

# DML - insert into - table products

Insert into products values (1,'skin care',100,'valid','2018-05-06 16:35:30.123');
Insert into products values (2,'clothes',200,'expired','2017-06-07 00:35:30.123');

# DML - insert into - table order_products

Insert into order_products values (1,1,5);
Insert into order_products values (2,2,10);
Insert into order_products values (1,2,4);

# DML - Update countries table

Update  countries set continent_name= 'Riyadh' where code = '3029';

# DML - Delete row from products table.

Delete from products where id =2;

# Bouns 
Alter Table  products  Modify column created_at datetime DEFAULT CURRENT_TIMESTAMP;

