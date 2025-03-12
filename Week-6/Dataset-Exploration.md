### _1. Find the average price of cars in the dataset._
SELECT ROUND(avg(Price),2) AS average FROM train
</br>

### _2. Calculate the number of cars with leather interior that are cheaper than $1400._
SELECT COUNT(*) FROM train WHERE `Leather interior` = 'yes' AND Price < 1400;
</br>

### _3. Get the maximum price of Toyota cars produced in 2011._
SELECT max(Price) FROM train WHERE Manufacturer = 'TOYOTA' AND `Prod. year` = 2011;
</br>

### _4. Sort the car manufacturers according to the average price of their cars descendingly._
SELECT Manufacturer, average FROM 
( 
	SELECT ROUND(avg(Price),2) AS average, Manufacturer FROM train GROUP BY Manufacturer 
) AS averages
ORDER BY average DESC;
</br>

### _5. Calculate the percentage of cars that use petrol fuel only among cars with category Jeep._
SELECT (SUM(CASE WHEN `Fuel type` = 'Petrol' THEN 1 ELSE 0 END) *100 / COUNT(*))
FROM train 
WHERE CATEGORY = 'Jeep'
</br>

### _6. Find the cheapest car(s) in the dataset. (If multiple cars have the same lowest price, return all of them.)_
SELECT * 
FROM train 
WHERE Price = (SELECT MIN(Price) FROM train);
</br>

### _7. Find the percentage of Toyota cars that are above the average price of all cars._
SELECT ( SUM( CASE WHEN Manufacturer = 'TOYOTA' AND Price > (SELECT avg(Price) FROM train) THEN 1 ELSE 0 END) * 100 / COUNT(*) ) AS Toyota_Percentage
FROM train
</br>
