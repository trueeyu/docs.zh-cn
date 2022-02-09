# array_agg

## description

### Syntax

`ANY_ARRAY array_agg(ANY_ELEMENT)`

用于列转数组的聚合函数, array_agg 将结果集中一列的多行结果转成一个数组.

生成的结果数组中元素的类型和函数中参数的列类型一致.

> 注意: 数组中元素不保证顺序

## example

```Plain Text
mysql> select * from test;
+------+------+
| c1   | c2   |
+------+------+
|    1 | a    |
|    1 | b    |
|    2 | c    |
|    2 | NULL |
|    3 | NULL |
+------+------+
5 rows in set (0.01 sec)

mysql> select c1, array_agg(c2) from test group by c1;
+------+-----------------+
| c1   | array_agg(`c2`) |
+------+-----------------+
|    1 | ["a","b"]       |
|    2 | [null,"c"]      |
|    3 | [null]          |
+------+-----------------+
3 rows in set (0.01 sec)

mysql> select c1, array_agg(c2) from test where c1>4 group by c1;
Empty set (0.01 sec)

mysql> select array_agg(c2) from test where c1>4;
+-----------------+
| array_agg(`c2`) |
+-----------------+
| NULL            |
+-----------------+
1 row in set (0.01 sec)
```

## keyword

ARRAY_AGG, ARRAY
