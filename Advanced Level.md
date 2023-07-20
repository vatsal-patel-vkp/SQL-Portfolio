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


