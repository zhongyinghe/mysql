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
3、同一字段同时使用unique和key
```
mysql会选择unique,因为它们都是使用二叉树，都能实现快速查找；不同的是: unique强调唯一性

参考: https://blog.csdn.net/qq591840685/article/details/53349717
```
