# Database

## 創建資料庫

### 透過 mysqladmin
```shell
# mysqladmin -u root -p create TUTORIALS
```

### 透過 SQL statement
```mysql
mysql> CREATE DATABASE `TUTORIALS`;
```

## 刪除資料庫

### 透過 mysqladmin
```shell
# mysqladmin -u root -p drop TUTORIALS
```

### 透過 SQL statement
```mysql
mysql> DROP DATABASE `TUTORIALS`;
```

## 選擇資料庫

### 透過 SQL statement
```mysql
mysql> USE `TUTORIALS`;
```
