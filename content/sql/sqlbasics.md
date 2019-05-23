---
title: "SQL Basics"
date: 2019-05-22T22:16:36-04:00
draft: false
---

Ok if you've read the [first tutorial]({{< ref "/sql/install" >}}) on installing Postgres
and getting your first database up and running, you're now wondering "So how do I access all
this data?" Well that's where this tutorial comes in as we are going to cover some of the basic
commands in SQL to get the data we want. Ok let's get started and dive right in to our data.

<h2>SELECT</h2>
<p>The <code>SELECT</code> command is going to be your workhorse command when working with
SQL. It's the command that tells Postgres to pull the data from the table and return it to you
so you can use it. The <code>SELECT</code> is always paired with a <code>FROM</code> clause
so you can tell Postgres exactly what table you want to select your data. Let's take a look
at the command I used at the end of the first tutorial:</p>
<pre><code class='Command Line'>
SELECT * FROM appearances LIMIT 10;
</code></pre>
<p>Ok let's break it down piece by piece. <code>SELECT</code> tells Postgres that we want to
pull data. The <code>\*</code> tells Postgres that we want the data from every column in the
table. You can choose whatever columns you want the data from and it doesn't have to be all of
them, but this example we are taking all of them. Next is the <code>FROM</code> clause that tells
Postgres we want to pull all the columns from the <code>appearances</code> table.</p>
<p>If you have multiple tables you would change the name of the table to whatever table you wanted
data from. In order to get a list of all the tables you can select form type `\dt` and hit enter and
Postgres will list all the tables in the public schema. The <code>LIMIT</code> clause while technically not needed
for a <code>SELECT</code> query is very important here. If we had just entered in the command without
using the <code>LIMIT</code> Postgres would have returned every single row in the table and you almost
never want to do that when just trying to look at the data in a table. So I added the <code>LIMIT</code>
clause and passed it the number 1 telling Postgres to limit the results to 10 rows. Pretty simple eh?</p>
<p>Ok lets do a couple other <code>SELECT</code> queries to get the hang of it. First though
lets get a list of the columns in our table with the <code>\d+ appearances</code> which will produce
and output similar to this:</p>

```
      Column   |       Type       | Collation | Nullable | Default | Storage  | Stats target | Description
    -----------+------------------+-----------+----------+---------+----------+--------------+-------------
     yearID    | bigint           |           |          |         | plain    |              |
     teamID    | text             |           |          |         | extended |              |
     lgID      | text             |           |          |         | extended |              |
     playerID  | text             |           |          |         | extended |              |
     G_all     | bigint           |           |          |         | plain    |              |
     GS        | double precision |           |          |         | plain    |              |
     G_batting | bigint           |           |          |         | plain    |              |
     G_defense | double precision |           |          |         | plain    |              |
     G_p       | bigint           |           |          |         | plain    |              |
     G_c       | bigint           |           |          |         | plain    |              |
     G_1b      | bigint           |           |          |         | plain    |              |
     G_2b      | bigint           |           |          |         | plain    |              |
     G_3b      | bigint           |           |          |         | plain    |              |
     G_ss      | bigint           |           |          |         | plain    |              |
     G_lf      | bigint           |           |          |         | plain    |              |
     G_cf      | bigint           |           |          |         | plain    |              |
     G_rf      | bigint           |           |          |         | plain    |              |
     G_of      | bigint           |           |          |         | plain    |              |
     G_dh      | double precision |           |          |         | plain    |              |
     G_ph      | double precision |           |          |         | plain    |              |
     G_pr      | double precision |           |          |         | plain    |              |
```

This table in the database lists the number of appearances at each position for each player, each season
and each team. G\_1b is games at first base and so on. If you need more info about the data
in the database the data dictionary can be found [here](http://www.seanlahman.com/files/database/readme2012.txt)
<p>So now we have some columns lets adjust our <code>SELECT</code> statement to just include a few
of them instead of all of them:</p>

Side note here. When I was creating this database file for you I forgot that Postgres only stores column names
in lower case. As you can see above it does recognize upper case when displaying the column. The problem comes
when you want to select a column. If you tried to execute `SELECT playerID from appearances limit 10;` you would
get an error saying `HINT:  Perhaps you meant to reference the column "appearances.playerID"`. But even if you added
appearances to your column selection you would still get the same error. THe solution is to add `""` around each
column name so that the column is searched for on a case sensitive basis. But that's annoying so lets fix it.

Logout of your current account with `\q` and log back in with the superuser account that is the same
name as your computer user name and run this code:

    \t on
    select 'ALTER TABLE '||'"'||table_name||'"'||' RENAME COLUMN '||'"'||column_name||'"'||' TO ' || lower(column_name)||';'
    from information_schema.columns
    where table_schema = 'public' and lower(column_name) != column_name
    \g /tmp/go_to_lower
    \i /tmp/go_to_lower

Copy this and paste it into the terminal and hit enter and all your column names will be in lower case. I put this
in the tutorial for a very good reason. I could have gone back and fixed the file and changed a couple
things and made it look like I'm perfect, but I'm not. Mistakes happen. A lot. Things are going
break and a vital skill is to learn how to fix them. In this case I literally googled
'convert all columnames to lowercase postgres' and the answer was the [second link](https://stackoverflow.com/questions/10086532/how-can-i-convert-all-columns-in-my-database-to-case-insensitive)
on google.

Do I know exactly what that code does? Nope but what better place to learn than in a situation
with no ramifications for it being wrong. Now knowing what to google comes with experience,
but a good place to start is to just cut and paste the error into google and start clicking.
This is what every professional programmer does and the ones that say they don't are lying.
Ok back to the tutorial.

<pre><code class='Command Line'>
SELECT playerid, teamid, g\_1b, g\_2b, g\_cf FROM appearances LIMIT 10;
</code></pre>
<p>Which will produce an output similar to this:</p>

    playerid  | teamid | g_1b | g_2b | g_cf
    -----------+--------+------+------+------
     abercda01 | TRO    |    0 |    0 |    0
     addybo01  | RC1    |    0 |   22 |    0
     allisar01 | CL1    |    0 |    2 |   29
     allisdo01 | WS3    |    0 |    0 |    0
     ansonca01 | RC1    |    1 |    2 |    0
     armstbo01 | FW1    |    0 |    0 |   11
     barkeal01 | RC1    |    0 |    0 |    0
     barnero01 | BS1    |    0 |   16 |    0
     barrebi01 | FW1    |    0 |    0 |    0
     barrofr01 | BS1    |    0 |    1 |    0
    (10 rows)

<p>You can play around with the columns as much as you want and see the different outputs.
So now we're getting some more info that is something we can work with but nothing we can actually
draw insights from. The next clause though will help us narrow our data even more.</p>
<h2>WHERE</h2>
<p>So above we learned how to limit the columns the SQL query returns so now lets learn how to
limit the rows that are returned. This is done in SQL by using the <code>WHERE</code> clause
with your <code>SELECT</code>. <code>WHERE</code> gives your an SQL query a condition that it
checks every row against in the table and if the condition is met it returns the row and if it
isn't then the row is excluded. Let's look at it in action:

    SELECT playerid, teamid, g_1b, g_2b, g_cf from appearances WHERE yearid = 2016 limit 10;

<p>Now there is a order in which clauses go where in the SQL queries. Generally its SELECT, FROM,
WHERE, GROUP BY, HAVING, ORDER BY, LIMIT. So when playing around with your queries if you don't stick
to the order Postgres will throw an error. Obviously you don't know what all of those clauses do, but
just keep in mind for now that <code>WHERE</code> clauses will go before `LIMIT` clauses. So if you ran
command above this should be your output:</p>

     yearid | playerid  | teamid | g_1b | g_2b | g_cf
    --------+-----------+--------+------+------+------
       2016 | abadfe01  | BOS    |    0 |    0 |    0
       2016 | abadfe01  | MIN    |    0 |    0 |    0
       2016 | abreujo02 | CHA    |  152 |    0 |    0
       2016 | achteaj01 | LAA    |    0 |    0 |    0
       2016 | ackledu01 | NYA    |   13 |    1 |    0
       2016 | adamecr01 | COL    |    0 |   11 |    0
       2016 | adamsau01 | CLE    |    0 |    0 |    0
       2016 | adamsma01 | SLN    |   86 |    0 |    0
       2016 | adlemti01 | CIN    |    0 |    0 |    0
       2016 | adriaeh01 | SFN    |    0 |    7 |    0
    (10 rows)

This has returned all the players that had an appearance in the 2016 baseball season.
You can also chain these commands as well using logical switches such as AND or OR like so:

    SELECT playerid, teamid, g_1b, g_2b, g_cf from appearances WHERE yearid = 2016 AND g_1b > 100;

<p>This will give us all the rows where the <code>yearid</code> is 2016 and games played at first base is
over 100 games. There are many more ways to combine these as well to help select the data that you are looking
for but this is the basics. There will be a lot of trial and error at the beginning as you get
used to it so don't despair and just keep at it.
<h2>Aggregate Functions</h2>
<p>Ok so we've learned how to select the appropriate columns and rows that we want from our data, but
how do we look at the overall picture? How do we look at say the total goals scored or assists earned over
a season or even a certain time frame? This is done with our powerful aggregate functions and the
<code>GROUP BY</code>.</p>
<p>As you can see with the data each row is an individual game for an individual player so just using
<code>WHERE</code>won't tell you the whole story. So let's try and see if we can calculate
who had the most hits last season in the MLB.

    SELECT playerid, sum(h) FROM batting WHERE yearid=2017 GROUP BY playerid ORDER BY sum(h) DESC LIMIT 10;

Which gives us this output:

     playerid  | sum
    -----------+-----
     blackch02 | 213
     altuvjo01 | 204
     inciaen01 | 201
     gordode01 | 201
     hosmeer01 | 192
     ozunama01 | 191
     andruel01 | 191
     abreujo02 | 189
     lemahdj01 | 189
     arenano01 | 187

<p>Well that column name isn't very helpful. However there is a simple way to change that using the <code>AS</code>
command in your query:

    SELECT playerid, sum(h) AS Hits FROM batting WHERE yearid=2017 GROUP BY playerid ORDER BY sum(h) DESC LIMIT 10;

<p>And now your output looks much nicer:</p>

     playerid  | hits
    -----------+------
     blackch02 |  213
     altuvjo01 |  204
     inciaen01 |  201
     gordode01 |  201
     hosmeer01 |  192
     ozunama01 |  191
     andruel01 |  191
     abreujo02 |  189
     lemahdj01 |  189
     arenano01 |  187
    (10 rows)

<p>All <code>AS</code> does is just create an alias for the column. You can do this with any column you want
along with tables as well. It just creates another name for something that you can refer to later on in the query.
In many newer flavors of SQL you can leave out the `AS` and just put a name next to the column, but I wanted to
show the `AS` incase something breaks if  you do that.
This won't work with <code>WHERE</code> statements because the <code>WHERE</code> clause references the raw data
and your alias is created after the fact.</p>

A couple other notes on this query. We have to do the `GROUP BY` because this table has a row for each player for each team
they played for in the season. A lot of players do play for the same team all season but a lot don't. If you didn't do
the group by you would miss out on those other team hits for that player. The next is the `ORDER BY` this tells
the database how to sort the results in this case by hits descending, i.e. from largest to smallest, with the
`DESC` keyword. When you alias the `sum(h)` column you can just using `ORDER BY hits` next time. `ORDER BY` will
sort ascending by default unless you tell it otherwise

<p>There several aggregate functions in SQL with the most common being <code>sum, avg, min, max, count</code>. Respectively
those add the values, average the values, find the minimum value, the maximum value, and last counts the number of values i.e.
the of rows in a column.</p>
<p>The next and most important part of an aggregate function is the <code>GROUP BY</code> clause. This tells
Postgres how we want to calculate the aggregate functions. If we left out the <code>player</code> column then
the functions would just sum the total goals and assists of every player after the date we gave it. <code>GROUP BY</code>
though allows us to tell Postgres that we want to group the sums by each player.
<code>GROUP BY</code> doesn't just work
for players we can use it on the <code>teamid</code> column as well or any other categorical column in your database.
In this one that is just mainly our teams and players, but if you were working with another database with
different categorical columns <code>GROUP BY</code> would work just as well on those with calculating aggregate
stats. If you have some experinece with pandas or R dataframes <code>GROUP BY</code> in SQL works basically the same
as <code>.groupby</code> and <code>group_by</code> respectively in those langauges.</p>

Our next tutorial will cover `JOIN` so you can finall tell which players are actually accumulating the stats
you are calculating in you queries.

<h2>Sources</h2>
<p><a href='https://www.postgresql.org/docs/9.5/static/functions-aggregate.html'>Postgres Aggregate Functions</a></p>
<p><a href='https://stackoverflow.com/questions/9532668/list-rows-after-specific-date'>List Rows after Specific Date in SQL</a></p>
<p><a href='https://dba.stackexchange.com/questions/22362/how-do-i-list-all-columns-for-a-specified-table'>List All Columns of Table</a></p>
