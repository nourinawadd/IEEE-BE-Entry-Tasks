### [Problem 1](https://www.hackerrank.com/challenges/revising-the-select-query/problem)
**Solution:** </br>
SELECT * FROM CITY WHERE COUNTRYCODE = 'USA' AND POPULATION > 100000;
</br>

### [Problem 2](https://www.hackerrank.com/challenges/name-of-employees/problem)
**Solution:** </br>
SELECT name FROM Employee ORDER BY name;
</br>

### [Problem 3](https://leetcode.com/problems/invalid-tweets/description/)
**Solution:** </br>
SELECT tweet_id FROM Tweets WHERE LENGTH(content) > 15;
</br>

### [Problem 4](https://leetcode.com/problems/swap-salary/description/)
**Solution:** </br>
UPDATE Salary 
SET sex = CASE sex
WHEN 'f' THEN 'm'
WHEN 'm' THEN 'f'
ELSE sex
END
WHERE sex IN('m', 'f');
</br>
