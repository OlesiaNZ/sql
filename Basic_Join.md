# Basic Join

## Tasks:
1. The total score of a hacker is the sum of their maximum scores for all of the challenges. Write a query to print the hacker_id, name, and total score of the hackers ordered by the descending score. If more than one hacker achieved the same total score, then sort the result by ascending hacker_id. Exclude all hackers with a total score of from your result.
```{SQL}
SELECT score.hacker_id, Hackers.name, sum(max_score) AS total_score 
FROM (SELECT hacker_id, challenge_id, max(score) AS max_score
      FROM Submissions 
      GROUP BY hacker_id, challenge_id) AS score
JOIN Hackers 
ON score.hacker_id = Hackers.hacker_id
GROUP BY score.hacker_id, Hackers.name
HAVING total_score > 0
ORDER BY total_score DESC, score.hacker_id ASC;
```
<br/>
