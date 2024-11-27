**DML Commands in MySQL**

**Overview**
      
       This project demonstrates the use of DML Commands in MySQL.DML commands in SQL are used to manipulate data
       stored in tables. These commands handle tasks such as inserting, updating, deleting, and retrieving data. 
       
**Primary DML commands:**
       
**1.INSERT:** 
    
    Used to add new rows of data into a table.
  
**Syntax:** 
    
    INSERT INTO table_name (column1, column2, column3, ...)VALUES (value1, value2, value3, ...);
  
**2.UPDATE:** 
   
    Used to modify existing data in a table.
  
**Syntax:**
   
    UPDATE table_name SET column1 = value1, column2 = value2, ...WHERE condition;

**3.DELETE:** 
   
    Used to remove rows from a table.
  
**Syntax:** 

    DELETE FROM table_name WHERE condition;
  
**4.SELECT:** 
  
    Used to retrieve data.
  
**Syntax:** 
  
    SELECT column1, column2, ...FROM table_name WHERE condition;
    SELECT * FROM table_name;
  

**Data Constraints used:**

       1.Primary Key         : Unique identifier for each record.
       2.Not Null            :Ensures that the column cannot have a NULL value.
       3.Auto_increment      :Automatically generates a unique number whenever a new row is inserted.
       4.Check               :Validate data against specific condition.


**Illustration with a Sample Database:**
      
      The script performs the following:

      1.Creating a database named Employee.
      2.Creating a table Manager with the fields:Manager_ID,First_name,Last_name,DOB,Age.
      3.DDL Operations:
          * Adding a new columms Gender and Department_salary to managers table.
          * Inserting 10 rows into the managers table.
          * Inserting new column Department.
      4.DML Operations:
          * Retrieving name and DOB of manager with manager_id 1.
          * Displaying annual income of all managers.
          * Displaying all manager records except JOHN.
          * Updating column Department.
          * Displaying details of managers whose department is 'IT' and earns more than 25000.
          * Displaying details of managers whose department_salary between 10000 and 35000
          
  
**CREATING DATABASE EMPLOYEE**

    create database	Employee;
    use Employee;

**CREATING TABLE MANAGERS WITH THE FIELDS Manager_Id,First_name,Last_Name,DOB,Age**

    create table Managers(
    Manager_Id int auto_increment PRIMARY KEY,
    First_name varchar(50) NOT NULL,
    Last_Name varchar(30),
    DOB DATE CHECK(DOB <'1984-12-31'),
    Age int CHECK(Age >=40 and Age <=50));

**INSERTING NEW FIELDS GENDER AND DEPARTMENT SALARY**

    alter table managers add column Gender char(1) CHECK(Gender in('M','F','O'));
    alter table managers add column Department_Salary int;
    desc managers;

**INSERTING VALUES INTO THE TABLES MANAGERS**

    insert into managers(First_name,Last_Name,DOB,Age,Gender,Department_Salary) values('John','Peter','1983-01-02','41','M','20000');
    insert into managers(First_name,Last_Name,DOB,Age,Gender,Department_Salary) values('Jo','Joseph','1984-01-02','40','M','27000');
    insert into managers(First_name,Last_Name,DOB,Age,Gender,Department_Salary) values('Varun','Simon','1982-01-12','42','M','70000');
    insert into managers(First_name,Last_Name,DOB,Age,Gender,Department_Salary) values('Rahul','Sunny','1984-01-20','40','M','45000');
    insert into managers(First_name,Last_Name,DOB,Age,Gender,Department_Salary) values('Mary','Peter','1983-07-10','41','F','50000');
    insert into managers(First_name,Last_Name,DOB,Age,Gender,Department_Salary) values('Anna','Mathew','1981-10-02','43','F','30000');
    insert into managers(First_name,Last_Name,DOB,Age,Gender,Department_Salary) values('Samuel','Mathew','1983-11-09','41','M','50000');
    insert into managers(First_name,Last_Name,DOB,Age,Gender,Department_Salary) values('Thomas','Varkey','1980-06-07','44','M','32000');
    insert into managers(First_name,Last_Name,DOB,Age,Gender,Department_Salary) values('Bobby','Jose','1983-08-05','41','M','55000');
    insert into managers(First_name,Last_Name,DOB,Age,Gender,Department_Salary) values('Mathew','Peter','1979-01-30','45','M','75000');
    select *from managers;

**RETRIEVING NAME AND DOB OF MANAGER WITH MANAGER ID 1**

    select First_name,Last_name,DOB from managers where manager_id=1;

**DISPLAY ANNUAL INCOME OF ALL MANAGER**

    select Department_salary*12 as annual_salary from managers;

**DISPLAY ALL MANAGER RECORDS EXCEPT JOHN**

    select *from managers where First_name!='John';

**INSERTING NEW COLUMN DEPARTMENT**

    alter table managers add column department varchar(20);

**UPDATING VALUES TO DEPARTMENT FIELD**

    update managers set department='IT' where first_name='John';
    update managers set department='HR' where first_name='Jo';
    update managers set department='Marketing' where first_name='Varun';
    update managers set department='IT' where first_name='Rahul';
    update managers set department='IT' where first_name='Mary';
    update managers set department='Marketing' where first_name='Anna';
    update managers set department='Finanace' where first_name='Samuel';
    update managers set department='Operations' where first_name='Thomas';
    update managers set department='Finance' where first_name='Bobby';
    update managers set department='HR' where first_name='Mathew';

    select *from managers;

**DISPLAYING DETAILS OF MANAGER WHOSE DEPARTMENT IS 'IT' AND EARNS 'MORE THAN 25000 PER MONTH'** 

    select *from managers where department='IT'and Department_Salary>25000;

**DISPLAYING DETAILS OF MANAGERS WHOSE SALARY BETWEEN 10000 AND 35000**

    select *from managers where department_salary between 10000 and 35000;
