# Query

- [Insert](#Insert)
- [Select](#Select)
- [Update](#Update)
- [Delete](#Delete)

<a name="Insert"></a>
## Insert

### 在表格中插入資料

語法：

```
INSERT INTO table_name ( field1, field2,...fieldN )
                       VALUES
                       ( value1, value2,...valueN );
```

範例：

```
INSERT INTO tutorials_tbl
(tutorial_title, tutorial_author, submission_date)
VALUES
("Learn PHP", "John Poul", NOW()),
("Learn MySQL", "Abdul S", NOW()),
("JAVA Tutorial", "Sanjay", '2007-05-06');
```

<a name="Select"></a>
## Select

### 在表格中選擇資料

語法：

```
SELECT field1, field2,...fieldN table_name1, table_name2...
[WHERE Clause]
[OFFSET M ][LIMIT N]
```

範例：

```
mysql> SELECT * FROM tutorials_tbl;
+-------------+----------------+-----------------+-----------------+
| tutorial_id | tutorial_title | tutorial_author | submission_date |
+-------------+----------------+-----------------+-----------------+
|           1 | Learn PHP      | John Poul       | 2015-08-09      |
|           2 | Learn MySQL    | Abdul S         | 2015-08-09      |
|           3 | JAVA Tutorial  | Sanjay          | 2007-05-06      |
+-------------+----------------+-----------------+-----------------+
3 rows in set (0.00 sec)
```

### 加上 WHERE 條件

語法：

```
SELECT field1, field2,...fieldN table_name1, table_name2...
[WHERE condition1 [AND [OR]] condition2.....
```

範例：

```
mysql> SELECT * from tutorials_tbl WHERE tutorial_author='Sanjay';
+-------------+----------------+-----------------+-----------------+
| tutorial_id | tutorial_title | tutorial_author | submission_date |
+-------------+----------------+-----------------+-----------------+
|           3 | JAVA Tutorial  | Sanjay          | 2007-05-06      |
+-------------+----------------+-----------------+-----------------+
1 row in set (0.00 sec)
```

### 使用 LIKE 規則

語法：

```
SELECT field1, field2,...fieldN table_name1, table_name2...
WHERE field1 LIKE condition1 [AND [OR]] filed2 = 'somevalue'
```

範例：

```
mysql> SELECT * from tutorials_tbl WHERE tutorial_author LIKE '%jay';
+-------------+----------------+-----------------+-----------------+
| tutorial_id | tutorial_title | tutorial_author | submission_date |
+-------------+----------------+-----------------+-----------------+
|           3 | Learning JAVA  | Sanjay          | 2007-05-06      |
+-------------+----------------+-----------------+-----------------+
1 row in set (0.00 sec)
```

### 排序

語法：

```
SELECT field1, field2,...fieldN table_name1, table_name2...
ORDER BY field1, [field2...] [ASC [DESC]]
```

範例：

```
mysql> SELECT * from tutorials_tbl ORDER BY tutorial_author ASC;
+-------------+----------------+-----------------+-----------------+
| tutorial_id | tutorial_title | tutorial_author | submission_date |
+-------------+----------------+-----------------+-----------------+
|           2 | Learn MySQL    | Abdul S         | 2015-08-09      |
|           1 | Learn PHP      | John Poul       | 2015-08-09      |
|           3 | JAVA Tutorial  | Sanjay          | 2007-05-06      |
+-------------+----------------+-----------------+-----------------+
3 rows in set (0.00 sec)
```

<a name="Update"></a>
## Update

### 在表格中更新資料

語法：

```
UPDATE table_name SET field1=new-value1, field2=new-value2
[WHERE Clause]
```

範例：

```
UPDATE tutorials_tbl
SET tutorial_title='Learning JAVA'
WHERE tutorial_id=3;
```

<a name="Delete"></a>
## Delete

### 在表格中刪除資料

語法：

```
DELETE FROM table_name [WHERE Clause]
```

範例：

```
mysql> DELETE FROM tutorials_tbl WHERE tutorial_id=3;
Query OK, 1 row affected (0.01 sec)
```