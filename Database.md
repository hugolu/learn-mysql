# Database

- [Create](#Create)
- [Drop](#Drop)
- [Select](#Select)

<a name="Create"></a>
## Create

透過 mysqladmin 創建資料庫：`mysqladmin create <db name>`

```
# mysqladmin -u root -p create TUTORIALS
Enter password:
#
```

連線後，創建資料庫：`CREATE DATABASE <db name>;`

```mysql
# mysql -u root -p
Enter password:

mysql> CREATE DATABASE `TUTORIALS`;
Query OK, 1 row affected (0.00 sec)
```

<a name="Drop"></a>
## Drop

透過 mysqladmin 刪除資料庫：`mysqladmin drop <db name>`

```
# mysqladmin -u root -p drop TUTORIALS
Enter password:
Dropping the database is potentially a very bad thing to do.
Any data stored in the database will be destroyed.

Do you really want to drop the 'TUTORIALS' database [y/N] y
Database "TUTORIALS" dropped
```

連線後，刪除資料庫：`DROP DATABASE <db name>;`

```mysql
# mysql -u root -p
Enter password:

mysql> DROP DATABASE `TUTORIALS`;
Query OK, 0 rows affected (0.00 sec)
```

<a name="Select"></a>
## Select

連線後，選擇資料庫：`USE <db name>;`

```mysql
# mysql -u root -p
Enter password:

mysql> USE `TUTORIALS`;
Database changed
```
