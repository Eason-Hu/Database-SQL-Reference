# Database-SQL-Reference

```sql
with temp as
(
    select 108 Name, 'test' Project, 'Err1, Err2, Err3' Error  from dual
    union all
    select 109, 'test2', 'Err1' from dual
)
select distinct
  t.name, 
  t.project,
  trim(regexp_substr(t.error, '[^,]+', 1, levels.column_value))  as error
from 
  temp t,
  table(cast(multiset(select level from dual connect by  level <= length (regexp_replace(t.error, '[^,]+'))  + 1) as sys.OdciNumberList)) levels
order by name
```
