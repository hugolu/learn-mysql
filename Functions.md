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

#### 語法
```sql
SELECT MAX(column_name) FROM table_name;
```

#### 找出最貴的商品
```sql
SELECT MAX(Price) AS HighestPrice FROM Products;
```

### MIN 找出最小值

#### 語法
```sql
SELECT MIN(column_name) FROM table_name;
```

#### 找出最便宜的商品
```sql
SELECT MIN(Price) AS SmallestOrderPrice FROM Products;
```

### SUM 計算總和

#### 語法
```sql
SELECT SUM(column_name) FROM table_name;
```

#### 計算物件總數
```sql
SELECT SUM(Quantity) AS TotalItemsOrdered FROM OrderDetails;
```

### GROUP BY

#### 語法
```sql
SELECT column_name, aggregate_function(column_name)
FROM table_name
WHERE column_name operator value
GROUP BY column_name;
```

#### 合併表格，算出每個 Shipper 的訂單數
```sql
SELECT Shippers.ShipperName,COUNT(Orders.OrderID) AS NumberOfOrders FROM Orders
LEFT JOIN Shippers
ON Orders.ShipperID=Shippers.ShipperID
GROUP BY ShipperName;
```

#### 合併表格，算出每個 Shipper 裡面每個 Employee 的訂單數
```sql
SELECT ShipperID, EmployeeID, COUNT(OrderID) AS NumberOforders FROM Orders GROUP BY ShipperID, EmployeeID;
```
```sql
SELECT Orders.ShipperID, Orders.EmployeeID, COUNT(Orders.OrderID) AS NumberOforders
FROM Orders
GROUP BY Orders.ShipperID, Orders.EmployeeID;
```
```sql
SELECT Shippers.ShipperName, Orders.EmployeeID, COUNT(Orders.OrderID) AS NumberOforders
FROM (Orders INNER JOIN Shippers ON Orders.ShipperID=Shippers.ShipperID)
GROUP BY Orders.ShipperID, Orders.EmployeeID;
```
```sql
SELECT Shippers.ShipperName, Employees.LastName, COUNT(Orders.OrderID) AS NumberOforders
FROM (Orders INNER JOIN Shippers ON Orders.ShipperID=Shippers.ShipperID) INNER JOIN Employees ON Orders.EmployeeID=Employees.EmployeeID
GROUP BY Orders.ShipperID, Orders.EmployeeID;
```

## SQL Scalar functions
根據輸入值，得到一個結果

### UCAS 將欄位字串轉為大寫

#### SQL 語法
```sql
SELECT UCASE(column_name) FROM table_name;
SELECT UPPER(column_name) FROM table_name;
```

#### 將客戶名字轉成大寫
```sql
SELECT UCASE(CustomerName) AS Customer, City FROM Customers;
```

### LCASE 將欄位字串轉為小寫

#### 語法
```sql
SELECT LCASE(column_name) FROM table_name;
SELECT LOWER(column_name) FROM table_name;
```

#### 將客戶名字轉成小寫
```sql
SELECT LCASE(CustomerName) AS Customer, City FROM Customers;
```

### MID 抽取欄位字串內的字元

#### 語法
```sql
SELECT MID(column_name,start,length) AS some_name FROM table_name;
SELECT SUBSTRING(column_name,start,length) AS some_name FROM table_name;
SELECT SUBSTR(column_name,start,length) AS some_name FROM table_name;
```

#### 取得城市名簡寫
```sql
SELECT MID(City,1,4) AS ShortCity FROM Customers;
```

### LEN 回傳字串長度

#### 語法
```sql
SELECT LEN(column_name) FROM table_name;
SELECT LENGTH(column_name) FROM table_name;
```

#### 取得地址字串長度
```sql
SELECT CustomerName, LENGTH(Address) as LengthOfAddress FROM Customers;
```

### ROUND 四捨五入

#### 語法
```sql
SELECT ROUND(column_name,decimals) FROM table_name;
```

#### 價格四捨五入
```sql
SELECT ProductName, ROUND(Price, 0) AS RoundedPrice FROM Products;
```

### NOW 取得目前系統日期與時間

#### 語法
```sql
SELECT NOW() FROM table_name;
```

#### 顯示目前系統時間
```sql
SELECT NOW();
```

### FORMAT 數值格式化

#### 語法
```sql
SELECT FORMAT(column_name,format) FROM table_name;
```

#### 格式化且四捨五入到小數後兩位
```sql
SELECT FORMAT(1234.5678, 2); # 1,234.57
SELECT FORMAT(8765.4321, 2); # 8,765.43
```

### DATE_FORMAT 日期格式化

#### 語法
```sql
SELECT DATE_FORMAT(column_name,format) FROM table_name;
```
- 格式參考 [MySQL DATE_FORMAT() Function](http://www.w3schools.com/sql/func_date_format.asp)

#### 格式化目前系統時間
```sql
SELECT DATE_FORMAT(NOW(), "%Y-%m-%d %H:%i:%s");
```
