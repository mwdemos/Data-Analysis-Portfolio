# Analyze Hacker News Trends - Codecademy

Problem statement: Hacker News is a popular website run by Y Combinator. It’s widely known by people in the tech industry as a community site for sharing news, showing off projects, asking questions, among other things. In this project, you will be working with a table named hacker_news that contains stories from Hacker News since its launch in 2007. It has the following columns:
  * title: the title of the story
  * user: the user who submitted the story
  * score: the score of the story
  * timestamp: the time of the story
  * url: the link of the story
This data was kindly made publicly available under the MIT license.

* Recent studies have found that online forums tend to be dominated by a small percentage of their users (1-9-90 Rule). Is this true of Hacker News? Is a small percentage of Hacker News submitters taking the majority of the points? First find the total score of all the stories.

      SELECT SUM(score)
      FROM hacker_news;

* Next, we need to pinpoint the users who have accumulated a lot of points across their stories. Find the individual users who have gotten combined scores of more than 200, and their combined scores.

      SELECT user, SUM(score)
      FROM hacker_news
      GROUP BY user
      HAVING SUM(score) > 200
      ORDER BY 2 DESC;

* Then, we want to add these users' scores together and divide by the total to get the percentage. Add their scores together and divide it by the total sum. So, is Hacker News dominated by these users?

      SELECT (517+309+304+282) / 6366.0;

* Oh no! While we are looking at the power users, some users are rickrolling--tricking readers into clicking on a link to a funny video and claiming that it links to information about coding. The url of the video is https://www.youtube.com/watch?v=dQw4w9WgXcQ. How many times has each offending user posted this link?

      SELECT user,
         COUNT(*)
      FROM hacker_news
      WHERE url IS 'https://www.youtube.com/watch?v=dQw4w9WgXcQ'
      GROUP BY user
      ORDER BY COUNT(*) DESC;

* Hacker News stories are essentially links that take users to other websites. Which of these sites feed Hacker News the most: GitHub, Medium, or New York Times? First, we want to categorize each story based on their source. We can do this using a CASE statement.

      SELECT CASE
         WHEN url LIKE '%github.com%' THEN 'GitHub'
         WHEN url LIKE '%medium.com%' THEN 'Medium'
         WHEN url LIKE '%nytimes.com%' THEN 'New York Times'
         ELSE 'Other'
        END AS 'Source'
      FROM hacker_news;

* Next, build on the previous query: add a column for the number of stories from each URL using COUNT(). Also, GROUP BY the CASE statement.

      SELECT CASE
         WHEN url LIKE '%github.com%' THEN 'GitHub'
         WHEN url LIKE '%medium.com%' THEN 'Medium'
         WHEN url LIKE '%nytimes.com%' THEN 'New York Times'
         ELSE 'Other'
        END AS 'Source',
        COUNT(*)
      FROM hacker_news
      GROUP BY 1;

* Every submitter wants their story to get a high score so that the story makes it to the front page, but... What's the best time of the day to post a story on Hacker News? SQLite comes with a strftime() function--a very powerful function that allows you to return a formatted date. Let's write a query that returns three columns:
    1. The hours of the trimestamp
    2. The average score for each hour
    3. The count of stories for each hour
    * Round the average scores.
    * Rename the columns to make it more readable.
    * Add a WHERE clause to filter out the NULL values in timestamp.
 
          SELECT strftime('%H', timestamp) AS 'Hour', ROUND(AVG(score)) AS 'Average Score', COUNT(*) AS 'Number of Stories'
          FROM hacker_news
          WHERE timestamp IS NOT NULL
          GROUP BY 1
          ORDER BY 2 DESC;
