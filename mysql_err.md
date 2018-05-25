1、`报的错误`
```
Expression #2 of SELECT list is not in GROUP BY clause and contains 
nonaggregated column ‘test.user.id’ which is not functionally 
dependent on columns in GROUP BY clause; this is incompatible with 
sql_mode=only_full_group_by
```
`查看信息`:<br>
查询语句
```
select @@global.sql_mode
```
查询结果:
```
ONLY_FULL_GROUP_BY,STRICT_TRANS_TABLES,NO_ZERO_IN_DATE,NO_ZERO_DATE,ERROR_FOR_DIVISION_BY_ZERO,NO_AUTO_CREATE_USER,NO_ENGINE_SUBSTITUTION
```
`解决方法一`:<br>
去掉ONLY_FULL_GROUP_BY，重新设置值。
```
set @@global.sql_mode='STRICT_TRANS_TABLES,NO_ZERO_IN_DATE,NO_ZERO_DATE,ERROR_FOR_DIVISION_BY_ZERO,NO_AUTO_CREATE_USER,NO_ENGINE_SUBSTITUTION'
```
`解决方法二`:
在/etc/my.cnf文件下进行如下设置
```
[mysqld] 
sql_mode=STRICT_TRANS_TABLES,NO_ZERO_IN_DATE,NO_ZERO_DATE,ERROR_FOR_DIVISION_BY_ZERO,NO_AUTO_CREATE_USER,NO_ENGINE_SUBSTITUTION
```


参考:https://blog.csdn.net/hq091117/article/details/79065199
