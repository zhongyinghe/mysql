MariaDB的安装和使用
-----
### 目录
```
    1、安装
    2、设置管理员密码
    3、去掉空用户
    4、对外授权
```
##### 1、安装
```
#安装命令
yum -y install mariadb mariadb-server

#启动MariaDb
systemctl start mariadb

#开机启动
systemctl enable mariadb
```
##### 2、设置管理员密码
```
mysqladmin -u root password 'xxxx'
```
##### 3、去掉空用户
```
use mysql;
#删除空用户
delete from user where user='';
#刷新MariaDB的系统权限相关表
FLUSH PRIVILEGES;
```
##### 4、对外进行远程授权
```
#对任意ip的授权
GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' IDENTIFIED BY 'password' WITH GRANT OPTION;
#对特定ip的授权
GRANT ALL PRIVILEGES ON *.* TO 'root'@'192.168.100.%' IDENTIFIED BY 'my-new-password' WITH GRANT OPTION;

#刷新MariaDB的系统权限相关表
FLUSH PRIVILEGES;

#检验授权是否远程授权是否成功
show grants for 'root'@'%';
#类似的
show grants for 'root'@'127.0.0.1';
#类似的
show grants for 'root'@'localhost';

#或者
select user,host from mysql.user;

#注意:如果使用云主机，则要开放相应的3306端口，否则即使本机开放了远程连接，远程也是连接不了的
```
