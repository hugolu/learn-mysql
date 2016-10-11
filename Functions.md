# Functions

參考 [SQL Functions](http://www.w3schools.com/sql/sql_functions.asp)

準備測試環境
```shell
$ mysql -uroot -p < Northwind.sql
```

## SQL Aggregate Functions
計算某欄位中多個值，得到一個結果。

### AVG 平均值

#### 語法
```sql
SELECT AVG(column_name) FROM table_name
```

#### 計算平均價格
```sql
SELECT AVG(Price) AS PriceAverage FROM Products;
```

#### 找出大於平均價格的商品
```sql
SELECT ProductName, Price FROM Products WHERE Price>(SELECT AVG(Price) FROM Products);
```

### COUNT 計算列數

#### 語法
```sql
SELECT COUNT(column_name) FROM table_name;
SELECT COUNT(DISTINCT column_name) FROM table_name;
```
#### 計算客戶#7的訂單數
```sql
SELECT COUNT(CustomerID) AS OrdersFromCustomerID7 FROM Orders
WHERE CustomerID=7;
```

#### 計算所有訂單數
```sql
SELECT COUNT(*) AS NumberOfOrders FROM Orders;
```

#### 計算所有訂單中客戶數
```sql
SELECT COUNT(DISTINCT CustomerID) AS NumberOfCustomers FROM Orders;
```

### FIRST 取得第一筆資料

#### SQL 語法
```sql
SELECT FIRST(column_name) FROM table_name;
```

#### MySQL 語法
```sql
SELECT column_name FROM table_name
ORDER BY column_name ASC
LIMIT 1;
```

#### 找出第一個客戶名字
```sql
SELECT CustomerName FROM Customers ORDER BY CustomerName ASC LIMIT 1;
```

### LAST 取得最末筆資料

#### SQL 語法
```sql
SELECT LAST(column_name) FROM table_name;
```

#### MySQL 語法
```sql
SELECT column_name FROM table_name
ORDER BY column_name DESC
LIMIT 1;
```

#### 找出最末個客戶名字
```sql
SELECT CustomerName FROM Customers ORDER BY CustomerName DESC LIMIT 1;
```

### MAX 找出最大值
### MIN 找出最小值
### SUM 計算總和

## SQL Scalar functions
根據輸入值，得到一個結果

### UCAS 將欄位字串轉為大寫
### LCASE 將欄位字串轉為小寫
### MID 抽取欄位字串內的字元
### LEN 回傳字串長度
### ROUND 四捨五入
### NOW 取得目前系統日期與時間
###FORMAT 格式化欄位表示方式
