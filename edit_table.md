1、修改自增开始值
```
ALTER TABLE `t_order_no` auto_increment=1;
```
2、添加或者删除索引
```
#添加索引的语法
ALTER TABLE 表名 ADD INDEX/UNIQUE/FULLTEXT [索引名](字段名)
#删除索引的语法
ALTER TABLE 表名 DROP INDEX 索引名
#查看表的所有索引
SHOW INDEX FROM 表名
```
