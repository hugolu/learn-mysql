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
### FIRST 取得第一筆資料
### LAST 取得最末筆資料
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
