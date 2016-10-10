# Alter

準備測試資料
```
MariaDB [test]> CREATE TABLE TBL (i INT, c CHAR(1));
MariaDB [test]> DESC TBL;
+-------+---------+------+-----+---------+-------+
| Field | Type    | Null | Key | Default | Extra |
+-------+---------+------+-----+---------+-------+
| i     | int(11) | YES  |     | NULL    |       |
| c     | char(1) | YES  |     | NULL    |       |
+-------+---------+------+-----+---------+-------+
```

## 修改欄位

```
ALTER TABLE tbl_name ADD [COLUMN] col_name column_definition [FIRST | AFTER col_name]
ALTER TABLE tbl_name DROP [COLUMN] col_name
```

### 刪除欄位
```
MariaDB [test]> ALTER TABLE TBL DROP i;
MariaDB [test]> DESC TBL;
+-------+---------+------+-----+---------+-------+
| Field | Type    | Null | Key | Default | Extra |
+-------+---------+------+-----+---------+-------+
| c     | char(1) | YES  |     | NULL    |       |
+-------+---------+------+-----+---------+-------+
```

### 增加欄位
```
MariaDB [test]> ALTER TABLE TBL ADD i INT;
MariaDB [test]> DESC TBL;
+-------+---------+------+-----+---------+-------+
| Field | Type    | Null | Key | Default | Extra |
+-------+---------+------+-----+---------+-------+
| c     | char(1) | YES  |     | NULL    |       |
| i     | int(11) | YES  |     | NULL    |       |
+-------+---------+------+-----+---------+-------+
```

### 改變位置
```
MariaDB [test]> ALTER TABLE TBL DROP i;
MariaDB [test]> ALTER TABLE TBL ADD i INT FIRST;
MariaDB [test]> DESC TBL;
+-------+---------+------+-----+---------+-------+
| Field | Type    | Null | Key | Default | Extra |
+-------+---------+------+-----+---------+-------+
| i     | int(11) | YES  |     | NULL    |       |
| c     | char(1) | YES  |     | NULL    |       |
+-------+---------+------+-----+---------+-------+
```

```
MariaDB [test]> ALTER TABLE TBL DROP i;
MariaDB [test]> ALTER TABLE TBL ADD i INT AFTER c;
MariaDB [test]> DESC TBL;
+-------+---------+------+-----+---------+-------+
| Field | Type    | Null | Key | Default | Extra |
+-------+---------+------+-----+---------+-------+
| c     | char(1) | YES  |     | NULL    |       |
| i     | int(11) | YES  |     | NULL    |       |
+-------+---------+------+-----+---------+-------+
```

## 變更欄位定義或名稱

### 修改欄位定義
```
MariaDB [test]> ALTER TABLE TESTALTER MODIFY c CHAR(10);
MariaDB [test]> SHOW COLUMNS FROM TESTALTER;
+-------+----------+------+-----+---------+-------+
| Field | Type     | Null | Key | Default | Extra |
+-------+----------+------+-----+---------+-------+
| c     | char(10) | YES  |     | NULL    |       |
| i     | int(11)  | YES  |     | NULL    |       |
+-------+----------+------+-----+---------+-------+
```

### 變更欄位名稱/定義
```
MariaDB [test]> ALTER TABLE TESTALTER CHANGE i j BIGINT;
MariaDB [test]> SHOW COLUMNS FROM TESTALTER;
+-------+------------+------+-----+---------+-------+
| Field | Type       | Null | Key | Default | Extra |
+-------+------------+------+-----+---------+-------+
| c     | char(10)   | YES  |     | NULL    |       |
| j     | bigint(20) | YES  |     | NULL    |       |
+-------+------------+------+-----+---------+-------+
```

```
MariaDB [test]> ALTER TABLE TESTALTER CHANGE j j INT;
MariaDB [test]> SHOW COLUMNS FROM TESTALTER;
+-------+----------+------+-----+---------+-------+
| Field | Type     | Null | Key | Default | Extra |
+-------+----------+------+-----+---------+-------+
| c     | char(10) | YES  |     | NULL    |       |
| j     | int(11)  | YES  |     | NULL    |       |
+-------+----------+------+-----+---------+-------+
```

## 設定欄位預設值
```
MariaDB [test]> ALTER TABLE TESTALTER MODIFY j BIGINT NOT NULL DEFAULT 100;
MariaDB [test]> SHOW COLUMNS FROM TESTALTER;
+-------+------------+------+-----+---------+-------+
| Field | Type       | Null | Key | Default | Extra |
+-------+------------+------+-----+---------+-------+
| c     | char(10)   | YES  |     | NULL    |       |
| j     | bigint(20) | NO   |     | 100     |       |
+-------+------------+------+-----+---------+-------+
```

## 改變欄位預設值
```
MariaDB [test]> ALTER TABLE TESTALTER ALTER j SET DEFAULT 1000;
MariaDB [test]> SHOW COLUMNS FROM TESTALTER;
+-------+------------+------+-----+---------+-------+
| Field | Type       | Null | Key | Default | Extra |
+-------+------------+------+-----+---------+-------+
| c     | char(10)   | YES  |     | NULL    |       |
| j     | bigint(20) | NO   |     | 1000    |       |
+-------+------------+------+-----+---------+-------+
```

```
MariaDB [test]> ALTER TABLE TESTALTER ALTER j DROP DEFAULT;
MariaDB [test]> SHOW COLUMNS FROM TESTALTER;
+-------+------------+------+-----+---------+-------+
| Field | Type       | Null | Key | Default | Extra |
+-------+------------+------+-----+---------+-------+
| c     | char(10)   | YES  |     | NULL    |       |
| j     | bigint(20) | NO   |     | NULL    |       |
+-------+------------+------+-----+---------+-------+
```

## 變更表格型態
```
MariaDB [test]> SHOW TABLE STATUS LIKE 'TESTALTER'\G
*************************** 1. row ***************************
           Name: TESTALTER
         Engine: InnoDB
              ...

MariaDB [test]> ALTER TABLE TESTALTER ENGINE = MYISAM;

MariaDB [test]> SHOW TABLE STATUS LIKE 'TESTALTER'\G
*************************** 1. row ***************************
           Name: TESTALTER
         Engine: MyISAM
              ...
```

## 變更表格名稱
```
MariaDB [test]> ALTER TABLE TESTALTER RENAME TO TESTALTER2;
```
