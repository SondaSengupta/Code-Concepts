# Introduction to SQL
- based off code school's SQL Course: http://campus.codeschool.com/courses/try-sql/
- more info: http://stackoverflow.com/questions/2054130/what-is-advanced-sql

### Selecting Data
```
use [database_name]
select [column_name]
from [table];
where 
order by
```
- "Order by DESC" allows you to sort by largest value first.
- "Where" uses the =, >, >=, <, <=, and <> operators.
- "Where" can use and/or for multiple statements. You can also do "where column_name in (number, number) to search for one number Or the other.

### Changing Data

#### Insert Data with Insert Statement
```
insert into [table_name] (column1name, column2name, etc)
values ('column1data', 'colum2data');
```
- You don't have to specify columns, but then doubly make sure that your values are in the correct order to match column insertion.
- You only need to specify which columns you are affecting. Columns not used will be left blank, if nulls are allowed.

#### Generally Updating Data
- general update statement
```
update [table_name]
set [column_name] = [column_value], [column_name] = [column_value]
where (clause for limit to the specific cells you need)
```
#### Update Data expanded to multiple selections
- "or" allows you expand you selection to update
```
update [table_name]
set [column_name] = [column_value], [column_name] = [column_value]
where ... or ...
```
#### Update data limited to match a specific criteria
- "and" allows you to limit to specific cells that must match all criteria
```
update [table_name]
set [column_name] = [column_value], [column_name] = [column_value]
where ... and ...
```

#### Delete cells from a table
```
Delete from [table_name]
where ...
```

#### Deleting (dropping) a database
- once deleted, you cannot get the data back unless it has been backed up.
```
Drop database [database_name]
```

### Create a database and tables
```
create database [database_name]

create table [table_name]
(
column_name, int,
column_name2, varchar(20),
);
```
- note the table or database will start off empty until you use update to update it with data.

#### Altering Columns
- **add** a column. Example:
```
ALTER TABLE table_name
ADD column_name datatype
```
- **delete** a column. Example:
```
ALTER TABLE table_name
DROP column_name datatype
```
### Simple Aggregate Functions
```
select count(colum_name)
from table_name;

select sum(colum_name)
from table_name;

select avg(colum_name)
from table_name;

select max(colum_name), min(colum_name)
from table_name;

```
- the count(*) will count all rows, including null ones. If you do count(column_name) it will return non-null rows of that column.
- sum, avg, max, and min will only work if the specified column is a number.
- you can put multiple queries into one such as the very last example that does min and max at the same time.

### Aggregate Functions using GroupBy and Having
- **group by** :  The GROUP BY statement is used in conjunction with the aggregate functions to group the result-set by one or more columns.
- **having** : Used to restrict the group by to only those that meet a specified condition.

```
select columnNameYouWantToSee, aggregateFunction (column_name)
from table_name
group by column_name
having aggregate(column_name) with specific condition
```

```
CREATE TABLE Actors (
  name varchar(50),
  country varchar(50),
  salary integer,
  role varchar(50)
);

INSERT INTO Actors (name, country, salary, role) VALUES
  ('Vivien Leigh',          'IN',     150000,   'leading'),
  ('Clark Gable',           'USA',    120000,   'leading'),
  ('Olivia de Havilland',   'Japan',  30000,    'leading'),
  ('Hattie McDaniel',       'USA',    45000,    'supporting'),
  ('Leslie Howard',         'UK',     50000,    'leading'),
  ('Alicia Rhett',          'USA',    97000,    'supporting'),
  ('Lillian Kemble-Cooper', 'UK',     95000,    'supporting');
  
select country, sum(salary)
from actors
group by country
having count(name) > 1;
-- Use the GROUP BY clause to write a query that returns the country name 
-- and total salary paid to actors for each country
-- for countries with more than one actor.
```
### Adding Constraints to Column
- "not null" prevents a column from having null values
- "unique" specifies that there cannot be duplicate values within a column
```
create table table_name,
(
  id int not null,
  name varchar(20) unique,
)

--A Unique Table Constraint to personalize the error message with the name of the constraint name you've provided.
create table table_name,
(
  id int not null,
  name varchar(20),
  constraint unique_constraint_name unique(specified_column_name);
)

--checking for a unique combination
create table table_name,
(
  id int not null,
  name varchar(20)
  constraint unique_constraint_name unique(column_name1, column_name2)
)

--making sure that no negative gets inside with a 'CHECK' constraint
create table table_name,
(
  id int NOT NULL CHECK (id > 0),
  name varchar(20)
)

```

### Adding Constraints for Primary and Foreign Keys

```
--specifying a column as the primary key
create table table_name,
(
  id int NOT NULL CHECK (id > 0) primary key,
  name varchar(20)
)

--specifying a column as the foregin key using 'references'
create table table_name,
(
  id int NOT NULL CHECK (id > 0) references other_table_name
  name varchar(20)
)

--OR in table constraint syntax
create table table_name,
(
  id int NOT NULL CHECK (id > 0)
  name varchar(20)
  foreign key (the_column_name_that's_foreign) references other_table;
)

```

### Inner Joins
- "Inner Join" and "Join" are the same keyword action.
```
**inner join** when you want to know what both sets have without nulls
SELECT column_name(s)
FROM table1
INNER JOIN table2
ON table1.column_name=table2.column_name;
``

select movies.title, genres.name
from movies
inner join genres
on movies_genres.movie_id = movies_genre.genre_id;
```

```
--Example: Make a table of actors and movies that have a 
--many to many relationship. Select the actor names relating to the movies they have played in.

CREATE TABLE Actors (
  id int PRIMARY KEY,
  name varchar(50) NOT NULL
);

CREATE TABLE Movies (
  id int PRIMARY KEY,
  title varchar(50) NOT NULL
);

CREATE TABLE Actors_Movies (
  actor_id int REFERENCES Actors,
  movie_id int REFERENCES Movies
);

INSERT INTO Actors (id, name) VALUES
  (1, 'Vivien Leigh'),
  (2, 'Clark Gable'),
  (3, 'Olivia de Havilland');

INSERT INTO Movies (id, title) VALUES
  (1, 'Don Juan'),
  (2, 'The Lost World'),
  (3, 'Peter Pan'),
  (4, 'Robin Hood');

INSERT INTO Actors_Movies (actor_id, movie_id) VALUES
  (1, 1),
  (1, 2),
  (2, 3),
  (3, 2),
  (3, 4);
  
  --SQL QUERY--
SELECT Actors.name, Movies.title 
FROM Actors
Inner Join Actors_Movies
on Actors.id = Actors_Movies.actor_id
Inner Join Movies
on Actors_Movies.movie_id = movies.id
order by title;
```
### Subqueries
- Subqueries (also known as inner queries or nested queries) are a tool for performing operations in multiple steps.
- The IN operator allows you to specify multiple values in a WHERE clause.
```

CREATE TABLE Movies (
  id int PRIMARY KEY,
  title varchar(50) NOT NULL
);

INSERT INTO Movies (id, title) VALUES
  (1, 'Don Juan'),
  (2, 'The Lost World'),
  (3, 'Peter Pan'),
  (4, 'Robin Hood');

CREATE TABLE Rooms (
  id INT PRIMARY KEY,
  seats int,
  movie_id int,
  FOREIGN KEY (movie_id) REFERENCES Movies
);

INSERT INTO Rooms (id, seats, movie_id) VALUES
  (1, 50, 2),
  (2, 100, 1),
  (3, 100, NULL),
  (4, 150, 3);
  
EXAMPLE: First, let's write a query that returns every movie_id from the Rooms table that has more than 75 seats. That will be the subquery. Next, turn this query into a subquery by wrapping it in parentheses. Then use the returned ids to find the matching movies and return their titles.

Answer:
select movies.title
from movies
where movies.id in
(select r.movie_id
from rooms as r
where r.seats > 75);

Example: Aggregate Subquery: Write a subquery that returns the id of the rooms that have greater than the average number of seats.

Query Answer:
select rooms.id
from rooms
where seats > 
(
 select avg(seats)
 from rooms
)
```


















