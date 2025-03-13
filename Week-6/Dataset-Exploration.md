### _1. Find the average price of cars in the dataset._
Query: </br>
SELECT ROUND(avg(Price),2) AS average FROM train;
</br>
Result: </br>
![image](https://github.com/user-attachments/assets/364225ec-2a77-48f3-adbd-fe5a36bcb5a5)
</br>

### _2. Calculate the number of cars with leather interior that are cheaper than $1400._
Query: </br>
SELECT COUNT(*) FROM train WHERE `Leather interior` = 'yes' AND Price < 1400;
</br>
Result: </br>
![image](https://github.com/user-attachments/assets/9432d8a8-09ca-4147-a68d-c8ee05396b34)
</br>

### _3. Get the maximum price of Toyota cars produced in 2011._
Query: </br>
SELECT max(Price) FROM train WHERE Manufacturer = 'TOYOTA' AND `Prod. year` = 2011;
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
Result: </br>
![image](https://github.com/user-attachments/assets/2b089d33-1d07-4862-b10a-831981d4813b)
</br>

### _5. Calculate the percentage of cars that use petrol fuel only among cars with category Jeep._
Query: </br>
SELECT (SUM(CASE WHEN `Fuel type` = 'Petrol' THEN 1 ELSE 0 END) *100 / COUNT(*))
FROM train 
WHERE CATEGORY = 'Jeep'
</br>

### _6. Find the cheapest car(s) in the dataset. (If multiple cars have the same lowest price, return all of them.)_
Query: </br>
SELECT * 
FROM train 
WHERE Price = (SELECT MIN(Price) FROM train);
</br>

### _7. Find the percentage of Toyota cars that are above the average price of all cars._
SELECT ( SUM( CASE WHEN Manufacturer = 'TOYOTA' AND Price > (SELECT avg(Price) FROM train) THEN 1 ELSE 0 END) * 100 / COUNT(*) ) AS Toyota_Percentage
FROM train
</br>
