# 從頭開始

- [SQL語言的動詞](#sql語言的動詞)
- [SQL連線](#sql連線)
- [SQL備份與還原](#sql備份與還原)

## SQL語言的動詞

|SQL功能|動詞|
|---|---|
|資料定義|CREATE, DROP, ALTER|
|資料操作|INSERT, UPDATE, DELETE|
|資料查詢|SELECT|
|資料控制|GRANT, REVOKE|

## SQL連線

登入：`mysql -h <host name> -u <user name> -p`

- `-h <host name>` 主機名稱
- `-u <user name>` 用戶名稱
- `-p` 登入密碼

登出：`mysql> quit;`

- 登入後，執行`quit`結束連線

```mysql
$ mysql -h localhost -u root -p
Enter password:
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 57
Server version: 5.5.43-0+deb7u1 (Debian)

Copyright (c) 2000, 2015, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> quit;
Bye
```

## SQL備份與還原

### 備份

|動作|範例|
|---|---|
|備份所有資料庫|# mysqldump -u root -p --all-databases > add_db.sql;|
|備份某個資料庫|# mysqldump -u root -p --databases db_name > db_name.sql;|
|備份某個資料表|# mysqldump -u root -p --tables db_name table_name > db_name.table_name.sql;|

### 還原

|動作|範例|
|---|---|
|還原一個資料表|# mysql -u root -p db_name < db_name.table_name.sql;|
|還原一個資料庫|# mysql -u root -p db_name < db_name.sql;|
|復原多個資料庫|# mysql -u root -p < add_db.sql;|

### Schema

|動作|範例|
|---|---|
|備份Schema|# mysqldump -u root -p db_name --no-data > db_name.schema.sql;|
|還原Schema|# mysql -u root -p db_name < db_name.schema.sql;|

