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
  


## 4. Fetching data and displaying information from the database table using different methods

SELECT * FROM EmployeeDemographics

![image](https://github.com/vatsal-patel-vkp/SQL/assets/107895872/159960f2-c44b-451f-9360-764c39f2e3b6)


SELECT FirstName, LastName FROM EmployeeDemographics

![image](https://github.com/vatsal-patel-vkp/SQL/assets/107895872/83562123-a9b9-44dd-a93d-5a2788406b14)


SELECT TOP 5 * FROM EmployeeDemographics

![image](https://github.com/vatsal-patel-vkp/SQL/assets/107895872/37689856-3434-48e7-b89c-fbc8e8685bab)


SELECT DISTINCT(EmployeeID) FROM EmployeeDemographics

![image](https://github.com/vatsal-patel-vkp/SQL/assets/107895872/0fb28010-2a74-43e1-bcdd-2157c7327473)


SELECT DISTINCT(Gender) FROM EmployeeDemographics

![image](https://github.com/vatsal-patel-vkp/SQL/assets/107895872/f258592d-50ba-4bf8-916d-d8cba4d2f708)


SELECT COUNT(LastName) AS 'Total No. Last Names'
FROM EmployeeDemographics

![image](https://github.com/vatsal-patel-vkp/SQL/assets/107895872/37e07d27-f2b2-4885-9ac3-a4a71a010a9f)


SELECT MAX(Salary) AS 'Max Salary', 
	   MIN(Salary) AS 'Min Salary', 
	   AVG(Salary) AS 'Avg_Salary' 
FROM EmployeeSalary

![image](https://github.com/vatsal-patel-vkp/SQL/assets/107895872/b35481f3-cc2b-470d-b941-cdd3e69bcfc9)


  

## 5. Using different methods with "WHERE" statements to fetch data from the Database Table

SELECT * FROM SQL_Practice.dbo.EmployeeDemographics 
WHERE FirstName = 'Jim'

![image](https://github.com/vatsal-patel-vkp/SQL/assets/107895872/845664b9-d9d3-478b-b51a-a1ea070d1a4d)


SELECT * FROM SQL_Practice.dbo.EmployeeDemographics
WHERE FirstName <> 'Jim'

![image](https://github.com/vatsal-patel-vkp/SQL/assets/107895872/1274bf23-3dfe-4c40-82a9-610c86ab2d00)


SELECT * FROM EmployeeDemographics
WHERE Age >= 30

![image](https://github.com/vatsal-patel-vkp/SQL/assets/107895872/41cdc6dd-4a10-49e6-808e-95bb5f9cc544)


SELECT * FROM EmployeeDemographics
WHERE Age <= 32 OR Gender = 'Male'

![image](https://github.com/vatsal-patel-vkp/SQL/assets/107895872/10c50bfe-e5db-4791-84d6-766e4058cf83)


SELECT * FROM EmployeeDemographics
WHERE LastName LIKE '%P%'

![image](https://github.com/vatsal-patel-vkp/SQL/assets/107895872/d8ded3ea-b156-4728-8323-c84dbeebde3e)


SELECT * FROM EmployeeDemographics
WHERE LastName LIKE 'P%l%'

![image](https://github.com/vatsal-patel-vkp/SQL/assets/107895872/17a5c923-41e3-4564-8ee5-30ca49e717d6)


SELECT * FROM EmployeeDemographics
WHERE LastName IS NOT NULL

![image](https://github.com/vatsal-patel-vkp/SQL/assets/107895872/ae697645-d6cd-4ead-b524-2f559fbe4fec)


SELECT * FROM EmployeeDemographics
WHERE FirstName IN ('Jim', 'Dev', 'Pramit', 'Rana')

![image](https://github.com/vatsal-patel-vkp/SQL/assets/107895872/0c48c5fb-8a90-40b6-b785-4b61a49d0d67)


SELECT Gender, Age, COUNT(Gender)
FROM EmployeeDemographics 
GROUP BY Gender, Age

![image](https://github.com/vatsal-patel-vkp/SQL/assets/107895872/cc007c43-ec56-4bc6-a737-4e2ecf433c88)


SELECT Gender, COUNT(Gender)
FROM EmployeeDemographics
WHERE Age > 31
GROUP BY Gender

![image](https://github.com/vatsal-patel-vkp/SQL/assets/107895872/f3ca8e11-950c-476e-8b27-c78ca5b11cdc)


SELECT Gender, Count(Gender) AS 'Gender Count'
FROM EmployeeDemographics
WHERE Age > 20
GROUP BY Gender
ORDER By 'Gender Count' DESC

![image](https://github.com/vatsal-patel-vkp/SQL/assets/107895872/3d3b2cad-eba0-47dd-a6ef-f8c1bee0a534)


SELECT * FROM EmployeeDemographics
ORDER BY Age DESC, Gender DESC

![image](https://github.com/vatsal-patel-vkp/SQL/assets/107895872/6079792f-cfe0-4b28-8c66-32730440e0bb)
