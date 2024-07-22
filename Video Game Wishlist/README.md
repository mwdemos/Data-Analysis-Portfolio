Before this project, I kept a list of games I wanted but didn't own, or owned but didn't finish playing. I kept it in the notes app on my phone. After some time, the list got long and disorganized. If I'm in the mood for a platformer, I want to be able to reorder my list by genre. If I'm curious how many Mario games I own and haven't finished playing, I want to be able to sort my list by franchise. If I'm trying to justify buying a new console like a PlayStation 5, maybe I want to see how many of my wishlist games are PS5 exclusives. So, the notes app didn't cut it. SQL did though! It didn't hurt that I wanted extra practice writing SQL queries anyways. So, I created the table below.

    CREATE TABLE games (
    title TEXT UNIQUE, /*Having the title be unique is handy for stopping me when I accidentally try to add a game  twice.*/
    console TEXT,
    release_date YEAR,
    genre TEXT,
    owned TEXT,
    started_playing TEXT,
    franchise TEXT
    );

I actually used the following INSERT query to add a multitude of games into my table but kept it to one here for the sake of brevity.

    INSERT INTO games
    VALUES ('Demon''s Souls', 'PS5', 2020, 'RPG', 'no', 'no', 'Soulsborne');

After adding so much, I needed to check the [final resulting table](https://github.com/mwdemos/Data-Analysis-Portfolio/blob/main/Video%20Game%20Wishlist/SQL%20Code%20Outputs/VideoGameWishlist_games_output_orderByFranchise.pdf).

    SELECT * FROM games
    ORDER BY franchise;

It looks like the majority of the games might be RPGs. I can use the following query to find out the [percentage](https://github.com/mwdemos/Data-Analysis-Portfolio/blob/main/Video%20Game%20Wishlist/SQL%20Code%20Outputs/VideoGameWishlist_games_output_rpg_percentage.pdf), which is about 46%. I suppose I have a genre preference.

    SELECT (SELECT COUNT(*) FROM games WHERE genre = 'RPG')*100.0 / (SELECT COUNT(*) FROM games) AS rpg_percentage;

To determine which game to play next, it helps to know which of my games I've started but haven't finished: The [resulting list](https://github.com/mwdemos/Data-Analysis-Portfolio/blob/main/Video%20Game%20Wishlist/SQL%20Code%20Outputs/VideoGameWishlist_games_output_started.pdf) tells me that I have some unfinished business!

    SELECT * FROM games
    WHERE started='yes'
    ORDER BY franchise;

The following are few queries I wrote to practice changing tables, such as updating the list to include games I recently purchased from the Steam Summer Sale, and deleting The Outer Worlds from the list once I completed it.

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

I had a smaller list of specifically Super Nintendo games that I decided to switch over to SQL too.

    CREATE TABLE snes_wishlist (
    title TEXT
    );

    INSERT INTO snes_wishlist
    VALUES ('Megaman X');

    SELECT * FROM snes_wishlist;
