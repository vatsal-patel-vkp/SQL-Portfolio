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




