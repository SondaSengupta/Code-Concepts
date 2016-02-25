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
Drop [database_name]
```

#### Create a database and tables
```
create [database_name]






