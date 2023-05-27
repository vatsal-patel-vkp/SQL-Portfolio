# SQL - Basic Level

## 1. Creating 2 tables in sql 

CREATE TABLE EmployeeDemographics(
	EmployeeID int,
	FirstName Varchar(50),
	LastName Varchar(50),
	Age int,
	Gender Varchar(50)
);


CREATE TABLE EmployeeSalary(
	EmployeeId int,
	JobTitle Varchar(50),
	Salary int
)


## 2. Inserting data values into 2 tables that represents employees and their designated employment and salary referring fetching data with through EmployeeId

INSERT INTO EmployeeDemographics VALUES
	(1002, 'Dev', 'Patel', 30, 'Male'),
	(1003, 'Pramit', 'Parikh', 29, 'Male'),
	(1004, 'Angela', 'Martin', 31, 'Female'),
	(1005, 'Toby', 'Flenderson', 32, 'Male'),
	(1006, 'Urali', 'Rana', 35, 'Female'),
	(1007, 'Viral', 'Patel', 34, 'Male'),
	(1008, 'Jasleen', 'Chibber', 29, 'Female'),
	(1009, 'Preet', 'Desai', 27, 'Male')

INSERT INTO EmployeeSalary VALUES
	(1001, 'Salesman', 45000),
	(1002, 'Receptionist', 36000),
	(1003, 'Salesman', 63000),
	(1004, 'Accountant', 47000),
	(1005, 'HR', 50000),
	(1006, 'Regional Manager', 65000),
	(1007, 'Supplier Relations', 41000),
	(1008, 'Salesman', 48000),
	(1009, 'Accountant', 42000)



## 3. Selecting top 1000 employees to display their data

SELECT TOP (1000) [EmployeeID]
      ,[FirstName]
      ,[LastName]
      ,[Age]
      ,[Gender]
  FROM [SQL_Practice].[dbo].[EmployeeDemographics]


SELECT TOP (1000) [EmployeeID]
	, [JobTitle]
	, [Salary]
  FROM [SQL_Practice].[dbo].[EmployeeSalary]
  ![image](https://github.com/vatsal-patel-vkp/Financial-Analysis/assets/107895872/2bbdab2a-adfd-4a43-b691-bddadade9cca)