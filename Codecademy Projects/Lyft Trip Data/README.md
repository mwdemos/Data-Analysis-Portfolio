# Lyft Trip Data - Codecademy

Problem statement: Let’s practice what we learned about joins by combining rows from different tables. Suppose you are a Data Analyst at Lyft, a ride-sharing platform. For a project, you were given three tables:
  * trips: trips information
  * riders: user data
  * cars: autonomous cars
Have fun!

* Try out a simple cross join between riders and cars. Is it useful?

      SELECT riders.first, riders.last, cars.model
      FROM riders, cars;

  No, each use is combined with each car model.

* Suppose we want to create a Trip Log with the trips and its users. Find the columns to join between trips and riders and combine the two tables using a LEFT JOIN. Let trips be the left table.

      SELECT * FROM trips
      LEFT JOIN riders ON trips.rider_id = riders.id;

* Suppose we want to create a link between the trips and the cars used during those trips. Find the columns to join on and combine the trips and cars table using an INNER JOIN.

      SELECT * FROM trips
      JOIN cars ON trips.car_id = cars.id;

* The new riders data are in! There are three new users this month. Stack the riders table on top of the new table called riders2.

      SELECT * FROM riders
      UNION
      SELECT * FROM riders2;
  
