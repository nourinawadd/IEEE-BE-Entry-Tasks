### [Problem 1](https://leetcode.com/problems/game-play-analysis-i/description/)
**Solution:** </br>
SELECT player_id, min(event_date) AS first_login FROM Activity GROUP BY player_id;
</br>
### [Problem 2](https://leetcode.com/problems/department-highest-salary/description/)
**Solution:** </br>
SELECT d.name AS Department, e.name AS Employee, e.salary AS Salary FROM Employee e JOIN Department d on e.departmentId = d.id WHERE e.salary = 
(
    SELECT max(e2.salary) FROM Employee e2 WHERE e2.departmentId = e.departmentId
);
</br>
### [Problem 3](https://leetcode.com/problems/customers-who-never-order/description/)
**Solution:** </br>
SELECT c.name AS Customers FROM Customers c WHERE c.id NOT IN 
(
    SELECT o.customerId FROM Orders o JOIN Customers c ON c.id = o.customerId
);
</br>
