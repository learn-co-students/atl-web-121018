# Intro to SQL

## Objectives

* Be able to define CRUD
* Be able to define Foreign Key
* Recognize Normalized vs Denormalized data
* Recognize Client Commands vs Table Operations vs Data Operations


### Thus Far...

* In-Memory - (RAM) The data or memory is lost when the program exits.
* Persistent - (Disk) The data is kept if power is lost or the program is exited and reopened.

Now, SQL is introduced to let us work with RDBMS systems:
* MySQL
* PostgreSQL
* Oracle SQL database
* MS SQL Server
* Sqlite ( <-- we'll spend most of our time with this one )

SQL databases are organized in tables:
* Spreadsheel (excel or CSV)
* rows and columns
* column is a particular attribute of data we want to capture
* row is a single entry or record in the table

What are the four common tasks we refer to when working with data?
CRUD:
* C - Create (`INSERT`)
* R - Read (`SELECT`)
* U - Update (`UPDATE`)
* D - Delete (`DELETE`)

## Directives

1. Install the SQLite Browser if you haven't already [here](http://sqlitebrowser.org/)
2. Open the SQLite Browser and click 'File -> Open Database'
3. Choose the `chinook.db` file from this repo. This database is open source and maintained by Microsoft (SQL is no fun if you don't have any data)
4. Click the tab that says 'Execute SQL'. Type SQL queries in the box above. Press the play button. See the results of that query in the box below


## Challenges

1. Write the SQL to return all of the rows in the artists table?

```SQL
SELECT * FROM artists;
```

2. Write the SQL to select the artist with the name "Black Sabbath"

```SQL
SELECT * FROM artists WHERE name="Black Sabbath";
```

3. Write the SQL to create a table named 'fans' with an autoincrementing ID that's a primary key and a name field of type text

```sql
CREATE TABLE IF NOT EXISTS "fans" (
  "fanId" INTEGER PRIMARY KEY NOT NULL,
  "name"  VARCHAR(200)
);
```

4. Write the SQL to alter the fans table to have a artist_id column type integer?

```sql
ALTER TABLE "fans" ADD "artist_id" INTEGER;
```

5. Write the SQL to add yourself as a fan of the Black Eyed Peas? ArtistId **169**

```sql
INSERT INTO "fans" (name, artistId) VALUES ("brit", 169);
```

6. Check out the [Faker gem](https://github.com/stympy/faker). `gem install faker`, open up irb, run `require 'faker'` and then generate a fake name for yourself using `Faker::Name.name`. How would you update your name in the fans table to be your new name?

   ```sql
UPDATE fans SET name="Dwayne Kunze" WHERE fanId=1;
   ```

7. Write the SQL to return fans that are not fans of the black eyed peas.

```sql
SELECT * FROM fans WHERE NOT(artistId=169);
```

8. Write the SQL to display an artists name next to their album title

```sql
SELECT albums.title, artists.name FROM albums
  JOIN artists ON albums.artistId=artists.artistId;
```

OR

```sql
SELECT albums.title, artists.name FROM artists
  JOIN albums ON artists.artistId=albums.artistId;
```

9. Write the SQL to display artist name, album name and number of tracks on that album

```sql
sqlite> SELECT artists.name, albums.title, COUNT(*) FROM albums
   ...>   JOIN artists ON albums.artistId=artists.artistId
   ...>   JOIN tracks ON tracks.albumId=albums.albumId
   ...>   GROUP BY tracks.albumId;
```

10. Write the SQL to return the name of all of the artists in the 'Pop' Genre

```sql

```

## BONUS (very hard)

11. I want to return the names of the artists and their number of rock tracks
    who play Rock music
    and have move than 30 tracks
    in order of the number of rock tracks that they have
    from greatest to least

```sql

```
