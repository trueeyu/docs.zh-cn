# isnull

## 功能

判断是否为 `NULL`，如果是 `NULL` 返回 1，如果不是 `NULL`，返回 0。

## 语法

```Haskell
isnull(v)
```

## 参数说明

`v`: 所有数据类型

## 语法说明

如果 `v` 是 `NULL` 返回 1，如果 `v` 不是 `NULL`，返回 0。

## 示例

```Plain Text
MYSQL > SELECT c2, isnull(c2) FROM t1;
+------+--------------+
| c2   | `c2` IS NULL |
+------+--------------+
| NULL |            1 |
|    1 |            0 |
+------+--------------+
```
