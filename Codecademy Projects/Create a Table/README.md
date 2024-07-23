# Create a Table - Codecademy

Problem statement: In this project, you will create your own friends table and add/delete data from it!

* Create a table named friends with three columns:
  * id that stores INTEGER
  * name that stores TEXT
  * birthday that stores DATE

         CREATE TABLE friends (
          id INTEGER,
          name TEXT,
          birthday DATE
         );

* Beneath your current code, add Ororo Munroe to friends. Her birthday is May 30th, 1940.
* Add two of your friends to the table. Insert an id, name, and birthday for each of them.

      INSERT INTO friends
      VALUES 
      (1, 'Ororo Munroe', '1940-05-30'),
      (2, 'Jen G', '2000-04-29'),
      (3, 'Steve L', '1997-12-20');

* Ororo Munroe just realized that she can control the weather and decided to change her name. Her new name is "Storm". Update her record in friends.

      UPDATE friends
      SET name = 'Storm'
      WHERE id = 1;

* Add a new column named email. Update the email address for everyone in your table. Storm's email is storm@codecademy.com.

      ALTER TABLE friends
      ADD email TEXT;

      UPDATE friends
      SET email = 'storm@codecademy.com'
      WHERE id = 1;

      UPDATE friends
      SET email = 'jen@gmail.com'
      WHERE id = 2;

      UPDATE friends 
      SET email = 'steve@gmail.com'
      WHERE id = 3;

* Wait, Storm is fictional... Remove her from friends.

      DELETE FROM friends
      WHERE id = 1;
