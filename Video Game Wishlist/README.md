# Video Game Wishlist

Before this project, I kept a list of games I wanted but didn't own, or owned but didn't finish playing. I kept it in the notes app on my phone. After some time, the list got long and disorganized. If I'm in the mood for a platformer, I want to be able to reorder my list by genre. If I'm curious how many Mario games I own and haven't finished playing, I want to be able to sort my list by franchise. If I'm trying to justify buying a new console like a PlayStation 5, maybe I want to see how many of my wishlist games are PS5 exclusives. The notes app didn't cut it. SQL did though! Of course, it didn't hurt that I wanted extra SQL practice anyways. So, I created the table below.

# Creating and Editing the "games" Table

    CREATE TABLE games (
    title TEXT UNIQUE,
    console TEXT,
    release_date YEAR,
    genre TEXT,
    owned TEXT,
    started_playing TEXT,
    franchise TEXT
    );

Forcing game titles to be unique is handy for stopping me when I accidentally try to add a game twice. I actually used the following INSERT query to add a multitude of games into my table but kept it to just one game here for the sake of brevity.

    INSERT INTO games
    VALUES ('Baldur''s Gate 3', 'PC', 2023, 'RPG', 'yes', 'no', 'Baldur''s Gate');

The following are a few queries I wrote to practice making table edits, such as updating my list to include games I recently purchased from the Steam Summer Sale, and deleting The Outer Worlds from the list once I completed the game.

    UPDATE games
    SET owned='yes', started='no'
    WHERE title='Cyberpunk 2077';

    UPDATE games
    SET console='Game Boy'
    WHERE title LIKE 'Metroid 2%';

    ALTER TABLE games
    RENAME COLUMN started_playing TO started;

    DELETE FROM games
    WHERE title = 'The Outer Worlds';

# Filtering and Aggregating 

After adding so much, I needed to check the [final resulting table](https://github.com/mwdemos/Data-Analysis-Portfolio/blob/main/Video%20Game%20Wishlist/SQL%20Code%20Outputs/VideoGameWishlist_games_output_orderByFranchise.pdf).

    SELECT * FROM games
    ORDER BY franchise;

It looks like the majority of the games might be RPGs. I used the following query to find out the [percentage](https://github.com/mwdemos/Data-Analysis-Portfolio/blob/main/Video%20Game%20Wishlist/SQL%20Code%20Outputs/VideoGameWishlist_games_output_rpg_percentage.pdf), which is about 46%. I suppose I have a genre preference.

    SELECT (SELECT COUNT(*) FROM games WHERE genre = 'RPG')*100.0 / (SELECT COUNT(*) FROM games) AS rpg_percentage;

To determine which game to play next, it helps to know which of my games I've started but haven't finished: The [resulting list](https://github.com/mwdemos/Data-Analysis-Portfolio/blob/main/Video%20Game%20Wishlist/SQL%20Code%20Outputs/VideoGameWishlist_games_output_started.pdf) tells me that I have some unfinished business!

    SELECT * FROM games
    WHERE started='yes'
    ORDER BY franchise;

# Joining Tables

I also had a smaller, less detailed [list of just Super Nintendo games](https://github.com/mwdemos/Data-Analysis-Portfolio/blob/main/Video%20Game%20Wishlist/SQL%20Code%20Outputs/VideoGameWishlist_snes_wishlist_output.pdf) that I had already created.

    CREATE TABLE snes_wishlist (
    title TEXT
    );

    INSERT INTO snes_wishlist
    VALUES ('Secret of Mana'),('Final Fantasy III (VI)'),('Super Castlevania 4'),('Tetris Attack'),('Turtles in Time'),('Chrono Trigger'),('Super Mario RPG'),('Megaman X');

    SELECT * FROM snes_wishlist;

I wanted to incorporate these games into the larger 'games' table. For JOIN practice, I joined the tables to check if any Super Nintendo Wishlist were missing from the 'games' table. The [output](https://github.com/mwdemos/Data-Analysis-Portfolio/blob/main/Video%20Game%20Wishlist/SQL%20Code%20Outputs/VideoGameWishlist_games_snes_wishlist_join.pdf) showed that there were some missing titles, which told me that I needed to add to the 'games' table.

    SELECT title FROM snes_wishlist
    LEFT JOIN games ON snes_wishlist.title = games.title
    WHERE games.title IS NULL;

That concludes my work with this project for now. In playing around with SQL I got some more experience and practice with writing basic queries, creating and editing tables, filtering and aggregating data, and making a simple join. I'm looking forward to referring back to my code here and using them as examples to help with future projects!
