# SQL
#database

##  Query order of execution

Complete SELECT query:
```sql
SELECT DISTINCT column, AGG_FUNC(_column_or_expression_), … FROM mytable 
JOIN another_table ON mytable.column = another_table.column 
WHERE _constraint_expression_ 
GROUP BY column HAVING _constraint_expression_ 
ORDER BY _column_ ASC/DESC 
LIMIT count OFFSET COUNT;
```

![[difference between having and where clause5a.png]]


## JOINs
1. INNER JOIN - zwraca rekordy, które mają pasujące wartości w obu tabelach
2. OUTER JOINs:
- LEFT JOIN - zwraca wszystkie rekordy z lewej tabeli i dopasowane rekordy z prawej tabeli
- RIGHT JOIN - zwraca wszystkie rekordy z prawej tabeli i dopasowane rekordy z lewej tabeli
- FULL JOIN - zwraca wszystkie rekordy, niezależnie od tego, czy pasujący rekord istnieje w drugiej tabeli.

![[Pasted image 20220915110439.png]]

```sql
SELECT up.email, up.fullname, up.function_id, f.name
FROM user_profile up
LEFT JOIN function f ON up.function_id = f.id;
```