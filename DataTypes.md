# 資料型別

- [整數](#Integer)
- [浮點數](#FloatingPoint)
- [日期時間](#DataTime)
- [字串](#String)

<a name="Integer"></a>
## 整數

|Type|Byte(s)|Digits|signed|unsigned|
|---|---|---|---|---|
|TINYINT|1|4|-128 ~ 127|0 ~ 255|
|SMALLINT|2|5|-32768 ~ 32767|0 ~ 65535|
|MEDIUMINT|3|9|-8388608 ~ 8388607|0 ~ 16777215|
|INT|4|11|-2147483648 ~ 2147483647|0 ~ 4294967295|
|BIGINT|8|20|-9223372036854775808 ~ 9223372036854775807|0 ~ 18446744073709551615|

<a name="FloatingPoint"></a>
## 浮點數

|Type|Byte(s)|Default|Max|Synonym|Note|
|---|---|---|---|---|---|
|FLOAT(M,D)|4|10,2|255, 30|-|單精確度浮點數(近似值)|
|DOUBLE(M,D)|8|16,4|255, 30|REAL|雙精確度浮點數(近似值)|
|DECIMAL(M,D)|||65, 30|NUMERIC|自行指定位數的精確值|

- M：所有數字的長度，不含小數點
- D：小數點後面數字的個數

<a name="DataTime"></a>
## 日期時間

|Type|Byte(s)|Format|Range|
|---|---|---|---|
|DATE|3|YYYY-MM-DD|'1000-01-01' ~ '9999-12-31'|
|TIME|3|HH:MM:SS|'-838:59:59' ~ '838:59:59'|
|YEAR[2]|1|YY|70~69 (1970~2069)|
|YEAR[4]|1|YYYY|1901~2155|
|DATETIME|8|YYYY-MM-DD HH:MM:SS|'1000-01-01 00:00:00' ~ '9999-12-31 23:59:59'|
|TIMESTAMP|4|YYYY-MM-DD HH:MM:SS|'1970-01-01 00:00:01' ~ '2038-01-19 03:14:07'|

<a name="String"></a>
## 字串

|Type|Length|Note|
|---|---|---|
|CHAR(M)|1 ~ 255|固定長度|
|VARCHAR(M)|1 ~ 255|可變長度|
|BLOB, TEXT|1 ~ 65535|使用者不定義長度|
|TINYBLOB, TINYTEXT|1 ~ 255|使用者不定義長度|
|MEDIUMBLOB, MEDIUMTEXT|1 ~ 16777215|使用者不定義長度|
|LONGBLOB, LONGTEXT|1 ~ 4294967295|使用者不定義長度|
|ENUM|1 ~ 65535|枚舉類型|

- BLOBs: "Binary Large Objects"

ENUM 是一個字元串對象，其值通常選自一個允許值列表中，該列表在表創建時的列規格說明中被明確地列舉。在下列某些情況下，值也可以是空串("") 或NULL。
例如，指定為 ENUM("one", "two", "three") 的一個列，可以有下面所顯示的任一值。

- NULL: NULL
- "": 0
- "one": 1
- "two": 2
- "three": 3