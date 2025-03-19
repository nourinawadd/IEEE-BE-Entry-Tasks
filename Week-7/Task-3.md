
### [Problem 1](https://www.hackerrank.com/challenges/what-type-of-triangle/problem?isFullScreen=true)
**Solution:** </br>
SELECT 
    CASE
        WHEN A + B <= C OR A + C <= B OR B + C <= A THEN 'Not A Triangle'
        WHEN A = B AND B = C THEN 'Equilateral'
        WHEN A = B OR A = C OR B = C THEN 'Isosceles'
        ELSE 'Scalene'
    END AS TriangleType
FROM TRIANGLES;
</br>


### [Problem 2](https://leetcode.com/problems/find-products-with-valid-serial-numbers/description/)
**Solution:** </br>
SELECT * 
FROM products 
WHERE description REGEXP 'SN[0-9]{4}-[0-9]{4}\\b'
ORDER BY product_id;
</br>


### [Problem 3](https://leetcode.com/problems/find-students-who-improved/description/)
**Solution:** </br>
WITH ScoreRank AS (
    SELECT 
        student_id, 
        subject, 
        score, 
        exam_date,
        RANK() OVER (PARTITION BY student_id, subject ORDER BY exam_date ASC) AS first_attempt,
        RANK() OVER (PARTITION BY student_id, subject ORDER BY exam_date DESC) AS last_attempt
    FROM Scores
)

SELECT 
    s1.student_id, 
    s1.subject, 
    s1.score AS first_score, 
    s2.score AS latest_score
FROM ScoreRank s1
JOIN ScoreRank s2 
ON s1.student_id = s2.student_id 
AND s1.subject = s2.subject
WHERE s1.first_attempt = 1 
AND s2.last_attempt = 1
AND s2.score > s1.score
ORDER BY s1.student_id, s1.subject;
</br>


### [Problem 4](https://leetcode.com/problems/percentage-of-users-attended-a-contest/description/)
**Solution:** </br>
SELECT 
    r.contest_id, 
    ROUND(COUNT(DISTINCT r.user_id) * 100.0 / (SELECT COUNT(*) FROM Users), 2) AS percentage
FROM Register r
GROUP BY r.contest_id
ORDER BY percentage DESC, contest_id ASC;
</br>
