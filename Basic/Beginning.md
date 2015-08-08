# 從頭開始

- [SQL語言的動詞](#Verbs)
- [SQL資料型別](#DataTypes)
- [SQL連線](#Connection)

<a name="Verbs"></a>
## SQL語言的動詞

|SQL功能|動詞|
|---|---|
|資料定義|CREATE, DROP, ALTER|
|資料操作|INSERT, UPDATE, DELETE|
|資料查詢|SELECT|
|資料控制|GRANT, REVOKE|

<a name="DataTypes"></a>
## SQL資料型別

### 整字

|Type|Byte(s)|Digits|signed|unsigned|
|---|---|---|---|---|
|TINYINT|1|4|-128 ~ 127|0 ~ 255|
|SMALLINT|2|5|-32768 ~ 32767|0 ~ 65535|
|MEDIUMINT|3|9|-8388608 ~ 8388607|0 ~ 16777215|
|INT|4|11|-2147483648 ~ 2147483647|0 ~ 4294967295|
|BIGINT|8|20|-9223372036854775808 ~ 9223372036854775807|0 ~ 18446744073709551615|

### 浮點數

|Type|Byte(s)|Default|Max|Synonym|Note|
|---|---|---|---|---|---|
|FLOAT(M,D)|4|10,2|255, 30|-|單精確度浮點數(近似值)|
|DOUBLE(M,D)|8|16,4|255, 30|REAL|雙精確度浮點數(近似值)|
|DECIMAL(M,D)|||65, 30|NUMERIC|自行指定位數的精確值|

- M：所有數字的長度，不含小數點
- D：小數點後面數字的個數

### 日期時間

|Type|Byte(s)|Format|Range|
|---|---|---|---|
|DATE|3|YYYY-MM-DD|'1000-01-01' ~ '9999-12-31'|
|TIME|3|HH:MM:SS|'-838:59:59' ~ '838:59:59'|
|YEAR[2]|1|YY|70~69 (1970~2069)|
|YEAR[4]|1|YYYY|1901~2155|
|DATETIME|8|YYYY-MM-DD HH:MM:SS|'1000-01-01 00:00:00' ~ '9999-12-31 23:59:59'|
|TIMESTAMP|4|YYYY-MM-DD HH:MM:SS|'1970-01-01 00:00:01' ~ '2038-01-19 03:14:07'|

### 字串


<a name="Connection"></a>
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