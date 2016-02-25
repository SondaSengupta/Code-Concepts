# Introduction to SQL
- based off code school's SQL Course: http://campus.codeschool.com/courses/try-sql/

#### Selecting Data to See
```
use [database_name]
select [column_name]
from [table];
where 
order by
```
- "Order by DESC" allows you to sort by largest value first.
- "Where" uses the =, >, >=, <, <=, and <> operators.

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

#### Create a database and tables
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
#### Simple Aggregate Functions
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
--Use the GROUP BY clause to write a query that returns the country name 
--and total salary paid to actors for each country
-- for countries with more than one actor.
```


















