# Table

- 產生表格：`CREATE TABLE <table_name> (<column_name> <column_type>)`
- 刪除表格：`DROP TABLE <table_name>`

```
DROP TABLE IF EXISTS `tutorials_tbl`;

CREATE TABLE `tutorials_tbl` (
  `tutorial_id` int(11) NOT NULL AUTO_INCREMENT,
  `tutorial_title` varchar(100) NOT NULL,
  `tutorial_author` varchar(40) NOT NULL,
  `submission_date` date DEFAULT NULL,
  PRIMARY KEY (`tutorial_id`)
) ENGINE=InnoDB AUTO_INCREMENT=2 DEFAULT CHARSET=latin1;
```