---
layout: post
title:      "Relational Elation"
date:       2019-01-19 01:00:45 +0000
permalink:  relational_elation
---

## Learning the bones of SQL in SQLite

### Hooray for SQL!

These past few weeks Flatiron Learn-Co coursework has brought me to the fundamentals of SQL and relational databases. I get the feeling that [SQL](https://www.linkedin.com/pulse/why-you-should-learn-sql-brewster-knowlton/) [is] (https://tableplus.io/blog/2018/08/why-sql-is-the-most-important-skill-to-learn.html) [considered](https://codingsight.com/structured-query-language-importance-of-learning-sql/) [pretty](https://www.dataquest.io/blog/why-sql-is-the-most-important-language-to-learn/) [important](http://blog.stoneriverelearning.com/6-reasons-why-you-should-learn-sql/) for tech-related workers, so I'm excited to dive in to it.

### Specifically, SQLite

The SQL being dove into is [SQLite](https://www.sqlite.org/), a version that claims to have the tradeoff of requiring no configuration in return for being fairly bare-bones. The advantage checks out for me so far, as setting it up on my Windows machine was fairly trivial. The [pre-compiled binary](https://www.sqlite.org/download.html) adds sqlite3 as a PATH command, allowing cmd or powershell immediate access.

From there, you can create a database immediately and easily:
```
> sqlite3 new_database_name.db
```
will create a new empty database if none of that name are in the current directory, and load the sqlite program, giving you this prompt:
```
SQLite version 3.7.12 2013-03-19 12:42:02
Enter ".help" for instructions
Enter SQL statements terminated with a ";"
sqlite>
```
While there are various tools that may make working with a SQLite database easier (like [DB Browser](https://sqlitebrowser.org/) or [SQLite Studio](https://sqlitestudio.pl/index.rvt)), you can work from the command line immediately. Here's a brief rundown of SQL use in SQLite that I've learned so far:

### Using SQL for simple table creation and querying

SQL's strength and biggest use case involves large tables of data that relate to each other in complex ways. But to get there, you still must first be able to create tables that could be represented almost as well in an array, hash, dictionary, or the like. This is done with the following command: 

```
sqlite>CREATE TABLE table_name (column_1 TYPE, column_2 TYPE, ..., column_n TYPE);
```
(note: SQLite does not actually check for capitalization in commands, though it will save the capitalization of named items like tables and columns. This command could also be input as `create table table_name (etc...)` with the same result.)
This creates an empty data structure called a table, which will in its simplest uses contains a number of records, or rows, each of which has a number of values, one for each column in the table. Each column specifies a type for the value, which in SQLite is one of the following:
```
INTEGER
TEXT
REAL
NULL
BLOB
```
Columns need not be given a type, nor indeed store the type they are given. However, every value in a record is one of these types, which is partially determined by the type its column is.

Actual data is put into tables with the INSERT command as follows:
```
sqlite>INSERT into table_name (column_1, column_2) VALUES (column_1_val, column_2_val);
```

And retrieved most simply with the SELECT command:
```
sqlite>SELECT column_1, column_2 FROM table_name;
column_1           column_2
----------------   ----------------
column_1_val       column_2_val
```

But SELECT can do much more than simply that. Coming closer to the true power of databases, we can add a WHERE statement to get only certain records (and use the * operator to SELECT all the columns in a table):
```
sqlite>SELECT * FROM table_name WHERE column_1 = value;
```

This is still only the very beginning. Stay tuned for aggregate functions, JOINS, and more, or check out [SQLite tutorial](http://www.sqlitetutorial.net) from whom I have learned much.



