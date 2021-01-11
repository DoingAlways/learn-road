# SQL

## 其他SQL语句

### 1. INSERT INTO ... SELECT ...

可将一个表复制到另一个表

```
例如：
INSERT INTO table_bak SELECT * FROM table;
```

### 2. UNION 与 UNION ALL

`Union` 将两张表的结果整合在一个结果集下，相同的两条记录会合并成一条，而`UNION ALL`相同记录不会

### 3. TRUNCATE TABLE 语句

清空表内容。不带`WHERE`条件子句的`DELETE`语句也表示清空表的内容。从执行结果看，两者实现了相同的功能，但两者实现的原理是不一样的。

`TRUNCATE TABLE`是DDL语句，即数据定义语句，相当于用重新定义一个新表的方法把原先表的内容直接丢弃，所以执行起来很快。