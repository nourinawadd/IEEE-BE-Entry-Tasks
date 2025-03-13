## [Dataset Used](https://www.kaggle.com/datasets/sidharth178/car-prices-dataset?select=train.csv)
### _1. Find the average price of cars in the dataset._
Query: </br>
SELECT ROUND(avg(Price),2) AS average FROM train;
</br>
</br>
Result: </br>
![image](https://github.com/user-attachments/assets/364225ec-2a77-48f3-adbd-fe5a36bcb5a5)
</br>

### _2. Calculate the number of cars with leather interior that are cheaper than $1400._
Query: </br>
SELECT COUNT(*) FROM train WHERE `Leather interior` = 'yes' AND Price < 1400;
</br>
</br>
Result: </br>
![image](https://github.com/user-attachments/assets/9432d8a8-09ca-4147-a68d-c8ee05396b34)
</br>

### _3. Get the maximum price of Toyota cars produced in 2011._
Query: </br>
SELECT max(Price) FROM train WHERE Manufacturer = 'TOYOTA' AND `Prod. year` = 2011;
</br>
</br>
Result: </br>
![image](https://github.com/user-attachments/assets/7f29e2dd-08c0-4196-9b0d-f4bda8c90da9)
</br>

### _4. Sort the car manufacturers according to the average price of their cars descendingly._
Query: </br>
SELECT Manufacturer, average FROM 
( 
	SELECT ROUND(avg(Price),2) AS average, Manufacturer FROM train GROUP BY Manufacturer 
) AS averages
ORDER BY average DESC;
</br>
</br>
Result: </br>
![image](https://github.com/user-attachments/assets/2b089d33-1d07-4862-b10a-831981d4813b)
</br>

### _5. Calculate the percentage of cars that use petrol fuel only among cars with category Jeep._
Query: </br>
SELECT (ROUND(SUM(CASE WHEN `Fuel type` = 'Petrol' THEN 1 ELSE 0 END) *100 / COUNT(\*),2)) as Percentage
FROM train 
WHERE CATEGORY = 'Jeep'
</br>
</br>
Result: </br>
![image](https://github.com/user-attachments/assets/eba4dd19-05af-4fe0-92cb-6035ce87d9a6)
</br>

### _6. Find the cheapest car(s) in the dataset. (If multiple cars have the same lowest price, return all of them.)_
Query: </br>
SELECT * 
FROM train 
WHERE Price = (SELECT MIN(Price) FROM train);
</br>
</br>
Result: </br>
![image](https://github.com/user-attachments/assets/5eef50e5-7376-44e5-8bd0-d832c381f51d)
</br>

### _7. Find the percentage of Toyota cars that are above the average price of all cars._
SELECT ( ROUND(SUM( CASE WHEN Manufacturer = 'TOYOTA' AND Price > (SELECT avg(Price) FROM train) THEN 1 ELSE 0 END) * 100 / COUNT(*),2) ) AS Toyota_Percentage
FROM train
</br>
</br>
Result: </br>
![image](https://github.com/user-attachments/assets/81c8f314-4d2b-4efb-967b-0c5ee5b0ad90)
</br>
