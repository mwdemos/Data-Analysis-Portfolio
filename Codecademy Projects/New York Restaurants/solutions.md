# New York Restaurants

Problem statement: We have put together a table of restaurants called nomnom and we need your help to answer some questions. Use the SQL commands you just learned and find the best dinner spots in the city.

* What are the distinct neighborhoods?
  
      SELECT DISTINCT neighborhood
      FROM nomnom;

* What are the distinct cuisine types?

      SELECT DISTINCT cuisine
      FROM nomnom;

* Suppose we would like some Chinese takeout. What are our options?

      SELECT *
      FROM nomnom
      WHERE cuisine = 'Chinese';

* Suppose Abbi and Ilana want to ahve a fancy dinner date. Return all the restaurants that are Italian and $$$.

      SELECT *
      FROM nomnom
      WHERE cuisine = 'Italian' AND price = '$$$';

* Your coworker Trey can't remember the exact name  of a restaurant he went to but he knows it contains the word 'meatball' in it. Can you find it for him using a query?

      SELECT *
      FROM nomnom
      WHERE name LIKE '%meatball%';

* Let's order delivery to the house! Find all the close by spots in Midtown, Downtown or Chinatown.

      SELECT *
      FROM nomnom
      WHERE neighborhood = 'Midtown' OR neighborhood = 'Downtown' OR neighborhood = 'Chinatown';

* Find all the health grade pending restaurants (empty values).

      SELECT *
      FROM nomnom
      WHERE health IS NULL;

* Create a Top 10 Restaurants Ranking based on reviews.

      SELECT *
      FROM nomnom
      ORDER BY review DESC
      LIMIT 10;

* Use a CASE statement to change the rating system to:
  * review > 4.5 is Extraordinary
  * review > 4 is Excellent
  * review > 3 is Good
  * review > 2 is Fair
  * Everything else is Poor

        SELECT name,
          CASE
            WHEN review > 4.5 THEN 'Extraordinary'
            WHEN review > 4 THEN 'Excellent'
            WHEN review > 3 THEN 'Good'
            WHEN review > 2 THEN 'Fair'
            ELSE 'Poor'
          END AS 'Review'
        FROM nomnom;
