# Introduction to SQL
- based off code school's SQL Course: http://campus.codeschool.com/courses/try-sql/

### Seeing Data
```
use [database_name]
select [column_name]
from [table];
where 
order by
```
- "Order by DESC" allows you to sort by largest value first.
- "Where" uses the =, >, >=, <, <=, and <> operators.

### Insert Data
```
insert into [table_name] (column1name, column2name, etc)
values ('column1data', 'colum2data');
```
- You don't have to specify columns, but then doubly make sure that your values are in the correct order to match column insertion.
- You only need to specify which columns you are affecting. Columns not used will be left blank, if nulls are allowed.

### Update Existing Data

```
update [table_name]
set [column_name] = [column_value], [column_name] = [column_value]
where (clause for limit to the specific cells you need)
```





