# STATS_MODE
## 语法
```sql
STATS_MODE(expr)
```
## 功能
  返回expr中最频繁出现的值。如果有多个最频繁值，Oracle随机返回一个。若需要返回多个最频繁值，请使用下面的语句：
```sql
SELECT x FROM (SELECT x, COUNT(x) AS cnt1
    FROM t GROUP　BY x )
    WHERE cnt1 = 
        (SELECT MAX(cnt2) FROM (SELECT COUNT(x) AS cnt2 FROM t GRUOP BY x));
```
