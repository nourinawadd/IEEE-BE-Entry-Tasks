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


### [Problem 4](https://leetcode.com/problems/rising-temperature/description/)
**Solution:** </br>
SELECT id FROM Weather w WHERE temperature > 
(
    SELECT temperature FROM Weather WHERE recordDate = DATE_SUB(w.recordDate, INTERVAL 1 DAY)
);
</br>


### [Problem 5](https://leetcode.com/problems/confirmation-rate/description/)
**Solution:** </br>
SELECT 
    s.user_id, 
    IFNULL(COUNT(CASE WHEN c.action = 'confirmed' THEN 1 END) / COUNT(c.user_id), 0) AS confirmation_rate
FROM Signups s
LEFT JOIN Confirmations c ON s.user_id = c.user_id
GROUP BY s.user_id;
</br>


### [Problem 6](https://www.hackerrank.com/challenges/the-report/problem)
**Solution:** </br>
SELECT 
    CASE 
        WHEN g.Grade >= 8 THEN s.Name 
        ELSE NULL 
        END AS Name, 
    g.Grade, s.Marks 
    FROM Grades AS g JOIN Students AS s 
    ON s.Marks BETWEEN g.Min_Mark AND g.Max_Mark 
ORDER BY g.Grade DESC, s.Name ASC;
</br>
