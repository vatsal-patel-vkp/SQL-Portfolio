# Nashville Housing Data Analysis using SQL


## Overview

This SQL project focuses on conducting a comprehensive analysis of housing data in Nashville, Tennessee. The aim is to derive valuable insights into the city's real 
estate market, property trends, and pricing patterns. The project involves querying and manipulating the dataset using SQL to perform various analyses, presenting the 
findings in a clear and visually appealing manner.



## Dataset

The dataset used in this project comprises historical housing data for Nashville. It includes information such as property addresses, sale dates, sale prices, 
property sizes, number of bedrooms, number of bathrooms, and other relevant attributes. The data is sourced from reputable real estate agencies and government records, 
ensuring its accuracy and reliability.



## Project Objectives

Data Exploration: Perform an initial exploration of the dataset to understand its structure, identify potential data quality issues, and gain insights into the 
distribution of key variables.

Neighborhood Analysis: Group properties by neighborhoods and analyze the variations in housing prices, property sizes, and other attributes across different areas 
of Nashville.

Property Type Analysis: Explore the impact of property types (e.g., single-family homes, apartments, condos) on housing prices and other factors.

Market Segmentation: Perform a segmentation analysis to categorize properties into different price ranges and identify the features that contribute most to 
higher-priced properties.




## Project Workflow

Data Import and Setup: Load the dataset into a SQL database, create appropriate tables, and ensure data integrity.

Exploratory Data Analysis: Conduct initial exploratory analysis to understand the dataset's characteristics and identify any data quality issues.

Data Cleaning: Address missing or inconsistent data, perform data transformations as necessary, and prepare the dataset for analysis.

Neighborhood Analysis: Group properties by neighborhood and analyze housing metrics for each area.

Property Type Analysis: Compare property types based on their prices, sizes, and other relevant attributes.

Market Segmentation: Implement clustering algorithms or other segmentation techniques to categorize properties into different price ranges.




## Conclusion

The Nashville Housing Data Analysis SQL project offers valuable insights into the city's real estate market. By conducting a thorough analysis of housing data, 
the project aims to provide useful information for potential homebuyers, real estate investors, and policymakers. The project's findings can be showcased on a 
GitHub repository portfolio, demonstrating your proficiency in SQL, data analysis, and data visualization.


-------------------------------------------------------------------------------------------
-------------------------------------------------------------------------------------------
-------------------------------------------------------------------------------------------
-------------------------------------------------------------------------------------------




# SQL Codes

SELECT * FROM NashvilleHousing

![image](https://github.com/vatsal-patel-vkp/SQL-Portfolio/assets/107895872/ae29412a-b773-4916-8b3b-a43b7430f0d0)

-------------------------------------------------------------------------------------------

-- Standardize the SaleDate

SELECT SaleDate, CONVERT(Date, SaleDate) AS Conv_Date
FROM NashvilleHousing

![image](https://github.com/vatsal-patel-vkp/SQL-Portfolio/assets/107895872/5f231365-6db4-4296-b3b0-dc004e0f2d4c)


ALTER TABLE NashvilleHousing
ALTER COLUMN SaleDate DATE;

SELECT SaleDate 
FROM NashvilleHousing

![image](https://github.com/vatsal-patel-vkp/SQL-Portfolio/assets/107895872/1e55f842-1ae3-4bf5-a71a-04a80f7ea457)


-------------------------------------------------------------------------------------------


-- Populate the Address (By adding value in missing columns)

SELECT Address, COUNT(UniqueID)
FROM NashvilleHousing
WHERE Address IS NULL
GROUP BY Address

SELECT * 
FROM NashvilleHousing

SELECT a.ParcelID, a.Address, b.ParcelID, b.Address, ISNULL(a.Address, b.Address)
FROM NashvilleHousing a
JOIN NashvilleHousing b
ON a.ParcelID = b.ParcelID
AND a.UniqueID <> b.UniqueID
WHERE a.Address IS NULL


UPDATE a
SET PropertyAddress = ISNULL(a.PropertyAddress, b.PropertyAddress)
FROM NashvilleHousing a
JOIN NashvilleHousing b
ON a.ParcelID = b.ParcelID
AND a.UniqueID <> b.UniqueID
WHERE a.PropertyAddress IS NULL


SELECT *
FROM NashvilleHousing
WHERE ParcelID IS NULL

![image](https://github.com/vatsal-patel-vkp/SQL-Portfolio/assets/107895872/c85cf890-5658-484c-87f8-d9b41a75a8e7)

-------------------------------------------------------------------------------------------

-- Seperating (Address, City, State) FROM PropertyAddress and OwnerAddress

SELECT PropertyAddress
FROM NashvilleHousing

SELECT SUBSTRING(PropertyAddress, 1, CHARINDEX(',', PropertyAddress)-1) AS Address,
SUBSTRING(PropertyAddress, CHARINDEX(',', PropertyAddress)+1, LEN(PropertyAddress)) AS City
FROM NashvilleHousing

ALTER TABLE NashvilleHousing
ADD Address NVARCHAR(255);

UPDATE NashvilleHousing
SET Address = SUBSTRING(PropertyAddress, 1, CHARINDEX(',', PropertyAddress)-1)

ALTER TABLE NashvilleHousing
ADD City NVARCHAR(255);

UPDATE NashvilleHousing
SET City = SUBSTRING(PropertyAddress, CHARINDEX(',', PropertyAddress)+1, LEN(PropertyAddress))

SELECT * 
FROM NashvilleHousing

![image](https://github.com/vatsal-patel-vkp/SQL-Portfolio/assets/107895872/97f309c0-301d-419e-8a75-068b70212425)


-------------------------------------------------------------------------------------------


-- Using Parsing method to split OwnerAddress 

SELECT OwnerAddress
FROM NashvilleHousing

SELECT 
PARSENAME(REPLACE(OwnerAddress, ',', '.'), 3) AS OwnerAddress,
PARSENAME(REPLACE(OwnerAddress, ',', '.'), 2) AS OwnerCity,
PARSENAME(REPLACE(OwnerAddress, ',', '.'), 1) AS OwnerState
FROM NashvilleHousing


ALTER TABLE NashvilleHousing
ADD OwnerStreetAddress NVARCHAR(255);

UPDATE NashvilleHousing
SET OwnerStreetAddress = PARSENAME(REPLACE(OwnerAddress, ',', '.'), 3)


ALTER TABLE NashvilleHousing
ADD OwnerCity NVARCHAR(255);

UPDATE NashvilleHousing
SET OwnerCity = PARSENAME(REPLACE(OwnerAddress, ',', '.'), 2)


ALTER TABLE NashvilleHousing
ADD OwnerState NVARCHAR(255);

UPDATE NashvilleHousing
SET OwnerState = PARSENAME(REPLACE(OwnerAddress, ',', '.'), 1)

SELECT * 
FROM NashvilleHousing


-------------------------------------------------------------------------------------------


--Change Y and N to Yes and No

SELECT DISTINCT(SoldAsVacant), COUNT(SoldAsVacant)
FROM NashvilleHousing
GROUP BY SoldAsVacant


SELECT SoldAsVacant,
	CASE WHEN SoldAsVacant = 'Y' OR SoldAsVacant = 'y' THEN 'Yes'
		 WHEN SoldAsVacant =  'N' OR SoldAsVacant = 'n' THEN 'No'
		 ELSE SoldAsVacant
	END
FROM NashvilleHousing


UPDATE NashvilleHousing
SET SoldAsVacant = CASE WHEN SoldAsVacant = 'Y' OR SoldAsVacant = 'y' THEN 'Yes'
						 WHEN SoldAsVacant =  'N' OR SoldAsVacant = 'n' THEN 'No'
						 ELSE SoldAsVacant
				   END





-------------------------------------------------------------------------------------------


-- Remove Duplicates

WITH RowNumCTE AS (
	SELECT *,
	ROW_NUMBER() OVER (PARTITION BY ParcelID,
									PropertyAddress,
									SaleDate,
									SalePrice,
									LegalReference
									ORDER BY UniqueID) AS row_num
	FROM NashvilleHousing
)
SELECT * 
--DELETE
FROM RowNumCTE
WHERE row_num > 1


SELECT *
FROM NashvilleHousing


-------------------------------------------------------------------------------------------

-- Delete unused Columns

SELECT * 
FROM NashvilleHousing

ALTER TABLE NashvilleHousing
DROP COLUMN PropertyAddress, OwnerAddress, TaxDistrict

