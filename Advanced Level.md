# SQL - Advanced Level

## 13. CTE (Common Table Expressions) Statement

WITH CTE_Employee as (
	SELECT FirstName, LastName, Gender, Salary, 
	COUNT(Gender) OVER (PARTITION BY Gender) AS TotalGender,
	AVG(Salary) OVER (PARTITION BY Gender) AS AvgSalary
	FROM EmployeeDemographics emp
	JOIN EmployeeSalary sal
	ON emp.EmployeeID = sal.EmployeeID
	WHERE Salary > 45000
)
SELECT * 
FROM CTE_Employee

![image](https://github.com/vatsal-patel-vkp/SQL/assets/107895872/6c93d662-a994-443c-86a9-06dae14d73d3)

===========================================================================================

## 14. Temp (Temporary Table) Statement

CREATE TABLE #temp_employee(
	EmployeeID INT,
	JobTitle VARCHAR(50),
	Salary INT
)

INSERT INTO #temp_employee VALUES
	(1001, 'Salesman', 45000),
	(1002, 'HR', 40000)

INSERT INTO #temp_employee
SELECT * 
FROM EmployeeSalary

SELECT *
FROM #temp_employee

![image](https://github.com/vatsal-patel-vkp/SQL/assets/107895872/3db96e88-13e3-43a1-bea5-78fe206b22ab)


DROP TABLE #temp_employee2
CREATE TABLE #temp_employee2(
	Jobtitle VARCHAR(50),
	EmployeePerJob INT,
	AvgAge INT,
	AvgSalary INT)


INSERT INTO #temp_employee2
SELECT JobTitle, COUNT(JobTitle), AVG(Age), AVG(salary)
FROM EmployeeDemographics emp
JOIN EmployeeSalary sal
on emp.EmployeeID = sal.EmployeeId
GROUP BY JobTitle

SELECT * FROM #temp_employee2

![image](https://github.com/vatsal-patel-vkp/SQL/assets/107895872/a2448839-cbd3-44ed-a521-c7145086446d)



===========================================================================================

## 15. String Function Statements

CREATE TABLE EmployeeErrors(
	EmployeeID INT,
	FirstName VARCHAR(50),
	LastName VARCHAR(50)
)

INSERT INTO EmployeeErrors VALUES
	(1001, 'Jimbo', 'Halbert'),
	(1002, 'Pamela', 'Beasely'),
	(1003, 'TOby', 'Flenderson - Fired')

SELECT * FROM EmployeeErrors

![image](https://github.com/vatsal-patel-vkp/SQL/assets/107895872/b9355a36-e869-4ceb-be97-3b8737f9bca0)


UPDATE EmployeeErrors
SET EmployeeID = '  1002'
WHERE FirstName = 'Pamela'


SELECT EmployeeID, TRIM(FirstName) AS FNTrim
FROM EmployeeErrors

![image](https://github.com/vatsal-patel-vkp/SQL/assets/107895872/36836582-9b99-48ee-8df5-689dcdf1b99f)


SELECT EmployeeID, RTRIM(EmployeeID) AS RTRIMID
FROM EmployeeErrors

![image](https://github.com/vatsal-patel-vkp/SQL/assets/107895872/cfe6b106-499e-40f0-8f72-4b322d4aa3c0)


SELECT EmployeeID, LTRIM(EmployeeID) AS LTRIMID
FROM EmployeeErrors

![image](https://github.com/vatsal-patel-vkp/SQL/assets/107895872/c844418e-eeff-40d5-a605-a118e1844cc3)


SELECT LastName, REPLACE(LastName, ' - Fired', '') AS LastNameFixed
FROM EmployeeErrors

![image](https://github.com/vatsal-patel-vkp/SQL/assets/107895872/55e7c8a6-68cf-4671-bdb7-9f63ad104903)


SELECT SUBSTRING(FirstName,1,3)
FROM EmployeeErrors

![image](https://github.com/vatsal-patel-vkp/SQL/assets/107895872/f1f9b2b1-738d-435f-957f-5a24d7a0e313)


SELECT err.FirstName, SUBSTRING(err.FirstName,1,3), dem.FirstName, SUBSTRING(dem.FirstName,1,3)
FROM EmployeeErrors err
JOIN EmployeeDemographics dem
ON SUBSTRING(err.FirstName, 1,3) = SUBSTRING(dem.FirstName, 1, 3)


SELECT FirstName, UPPER(FirstName) AS CapitalName
FROM EmployeeErrors

![image](https://github.com/vatsal-patel-vkp/SQL/assets/107895872/ceb72273-bf63-4929-ab46-62144bc0e2fb)


SELECT LastName, LOWER(LastName) AS LowerCaseName
FROM EmployeeErrors

![image](https://github.com/vatsal-patel-vkp/SQL/assets/107895872/839195c7-5440-4816-988e-952d75121f42)



===========================================================================================

## 17. Stored Procedures Statement

CREATE PROCEDURE TEST
AS 
SELECT * FROM EmployeeDemographics


EXEC TEST


CREATE PROCEDURE TEMP_EMPLOYEE_2
AS 
CREATE TABLE #temp_employee2(
	Jobtitle VARCHAR(50),
	EmployeePerJob INT,
	AvgAge INT,
	AvgSalary INT)


INSERT INTO #temp_employee2
SELECT JobTitle, COUNT(JobTitle), AVG(Age), AVG(salary)
FROM EmployeeDemographics emp
JOIN EmployeeSalary sal
on emp.EmployeeID = sal.EmployeeId
GROUP BY JobTitle

SELECT * FROM #temp_employee2

![image](https://github.com/vatsal-patel-vkp/SQL/assets/107895872/16659404-eb63-4ce5-a739-ea6df5ec7bf5)

===========================================================================================

## 16. Sub-Query Statement

SELECT EmployeeID, Jobtitle, Salary
FROM EmployeeSalary
WHERE EmployeeId in (
	SELECT EmployeeId 
	FROM EmployeeDemographics
	WHERE Age > 30
)

![image](https://github.com/vatsal-patel-vkp/SQL/assets/107895872/cadbc5c4-e86d-4e04-a9fc-fc9e90ca50b8)






