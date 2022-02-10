# array_agg

## Description

将一列中的值（包括空值）串联成一个数组，可以用于列转行。

## Syntax

`ARRAY_AGG(col)`

## Arguments

* `col` `BOOLEAN/TINYINT/SMALLINT/INT/BIGINT/LARGEINT/FLOAT/DOUBLE/VARCHAR/CHAR/DATETIME/DATE`

需要转换的列。

## Return value

* 返回类型: ARRAY
* 返回转换生成的数组, 数组中的元素类型与 col 类型一致。

## Example

下面的示例使用如下数据表进行介绍

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
```

```Plain Text
-- 根据 c1 列分组，对 c2 执行列转行
mysql> select c1, array_agg(c2) from test group by c1;
+------+-----------------+
| c1   | array_agg(`c2`) |
+------+-----------------+
|    1 | ["a","b"]       |
|    2 | [null,"c"]      |
|    3 | [null]          |
+------+-----------------+
```

```Plain Text
-- 对全表执行列转行，但是没有符合过滤条件的数据
mysql> select array_agg(c2) from test where c1>4;
+-----------------+
| array_agg(`c2`) |
+-----------------+
| NULL            |
+-----------------+
```

## Usage notes

数组中元素不保证顺序。

## keyword

ARRAY_AGG, ARRAY
