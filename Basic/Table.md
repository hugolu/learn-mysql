# Table

- [CREATE](#CREATE)
- [DROP](#DROP)

## CREATE

 產生表格：`CREATE TABLE <table_name> (<column_name> <column_type>);`

```MySQL
mysql> use TUTORIALS;
Database changed
mysql> CREATE TABLE tutorials_tbl(
    -> tutorial_id INT NOT NULL AUTO_INCREMENT,
    -> tutorial_title VARCHAR(100) NOT NULL,
    -> tutorial_author VARCHAR(40) NOT NULL,
    -> submission_date DATE,
    -> PRIMARY KEY ( tutorial_id )
    -> );
Query OK, 0 rows affected (0.03 sec)
```

## DROP

刪除表格：`DROP TABLE <table_name>;`

```MySQL
mysql> use TUTORIALS;
Database changed
mysql> DROP TABLE tutorials_tbl;
Query OK, 0 rows affected (0.01 sec)
```