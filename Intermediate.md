# SQL - Intermediate Level


## 6. Inner & Outer Joins

SELECT * FROM EmployeeDemographics

![image](https://github.com/vatsal-patel-vkp/SQL/assets/107895872/e3a6945a-c2a4-4cea-b68f-b36557c3a33d)

SELECT *
FROM SQL_Practice.dbo.EmployeeDemographics
INNER JOIN SQL_Practice.dbo.EmployeeSalary
ON EmployeeDemographics.EmployeeID = EmployeeSalary.EmployeeId

![image](https://github.com/vatsal-patel-vkp/SQL/assets/107895872/79f6a66a-bea5-4920-aaea-7617dd3fd3bb)

SELECT *
FROM SQL_Practice.dbo.EmployeeDemographics
Full Outer JOIN SQL_Practice.dbo.EmployeeSalary
ON EmployeeDemographics.EmployeeID = EmployeeSalary.EmployeeId

![image](https://github.com/vatsal-patel-vkp/SQL/assets/107895872/3950ecf4-93a0-485b-bbaf-4253a0dd1cd7)



SELECT JobTitle, AVG(Salary) As 'Average Salary'
FROM EmployeeDemographics 
INNER JOIN EmployeeSalary
ON EmployeeDemographics.EmployeeID = EmployeeSalary.EmployeeId
WHERE JobTitle = 'Salesman'
GROUP BY JobTitle

![image](https://github.com/vatsal-patel-vkp/SQL/assets/107895872/04f32579-7f4b-4940-9422-447f87779abf)



SELECT EmployeeDemographics.EmployeeID, FirstName, LastName, Salary
FROM SQL_Practice.dbo.EmployeeDemographics
INNER JOIN SQL_Practice.dbo.EmployeeSalary
ON EmployeeDemographics.EmployeeID = EmployeeSalary.EmployeeID
WHERE FirstName <> 'Urali'

![image](https://github.com/vatsal-patel-vkp/SQL/assets/107895872/c35ee543-6291-4bc7-a07b-f16c5f8f8b01)

===========================================================================================


## 7. Union

SELECT EmployeeID, FirstName, Age
FROM EmployeeDemographics
UNION
SELECT EmployeeID, JobTitle, Salary
FROM EmployeeSalary

![image](https://github.com/vatsal-patel-vkp/SQL/assets/107895872/79bed731-7b2f-4434-817a-ab3e4130ff38)


===========================================================================================


## 8. CASE Statement

SELECT FirstName, LastName, JobTitle, Salary,
CASE
	WHEN JobTitle = 'Salesman' THEN Salary + (Salary * 0.10)
	WHEN JobTitle = 'Accountant' THEN Salary + (Salary * 0.05)
	WHEN JobTitle = 'HR' THEN Salary + (Salary * 0.01)
	ELSE Salary + (Salary * 0.03)
END AS 'Salary After Raise'
FROM EmployeeDemographics
JOIN EmployeeSalary
ON EmployeeDemographics.EmployeeID = EmployeeSalary.EmployeeId

![image](https://github.com/vatsal-patel-vkp/SQL/assets/107895872/88c9cdae-80f6-46bd-843a-874c8d88ba08)


===========================================================================================


## 9. Having Clause Statement

SELECT JobTitle, AVG(Salary)
FROM EmployeeDemographics
JOIN EmployeeSalary
ON EmployeeDemographics.EmployeeID = EmployeeSalary.EmployeeId
GROUP BY JobTitle
HAVING AVG(Salary) > 45000
ORDER BY AVG(Salary) DESC

![image](https://github.com/vatsal-patel-vkp/SQL/assets/107895872/83fa33b0-fb5e-405d-ba1d-525d3f106eef)


===========================================================================================


## 9. Updating & Deleting Data

SELECT * FROM EmployeeDemographics

![image](https://github.com/vatsal-patel-vkp/SQL/assets/107895872/8c837b8c-9d8d-47ad-8f85-263513a8872d)


UPDATE EmployeeDemographics
SET Age = 36, Gender = 'Female'
WHERE EmployeeID = 1012

![image](https://github.com/vatsal-patel-vkp/SQL/assets/107895872/91d656e3-613e-432f-aa9c-f7e572880389)


DELETE
FROM EmployeeDemographics
WHERE EmployeeID = 1005

![image](https://github.com/vatsal-patel-vkp/SQL/assets/107895872/327f6022-0d84-4921-a8ea-7e3ffbf11133)


