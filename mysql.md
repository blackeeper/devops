### mysql common guide

MySQL



## 创建数据库，并授权

``` sql
create database xx default character set utf8mb4 collate utf8mb4_unicode_ci;
grant all on xx.* to 'xx'@'%' identified by 'xx@123';

```


## MySQL主从配置，基于GTID

配置步骤：

- 修改root密码
- 授权root登录
- 创建slave用户
- 配置主从同步

``` sql

ALTER USER 'root'@'localhost' IDENTIFIED BY '4Rfv@1118#'; 

grant all on *.* to 'root'@'%' IDENTIFIED BY '4Rfv@1118#';

grant replication slave on *.* to 'repl'@'%' identified by '4Rfv@1118#';

CHANGE MASTER TO MASTER_HOST='10.10.0.163',MASTER_USER='repl',MASTER_PASSWORD='4Rfv@1118#',MASTER_AUTO_POSITION=1;

```


## 主配置

``` 
[mysqld]
datadir=/data/mysql/data
socket=/var/lib/mysql/mysql.sock
character-set-server=utf8

skip_ssl
server-id=163
gtid_mode=on
enforce_gtid_consistency=on
log_bin=master-binlog
log-slave-updates=1    
binlog_format=row 
skip_slave_start=1 

# Disabling symbolic-links is recommended to prevent assorted security risks
symbolic-links=0

log-error=/var/log/mysqld.log
pid-file=/var/run/mysqld/mysqld.pid

```

## 从配置

```
[mysqld]
datadir=/data/mysql/data
socket=/var/lib/mysql/mysql.sock
gtid_mode=on
enforce_gtid_consistency=on
server_id=88
read_only = ON
skip_ssl

#binlog
log-bin=slave-binlog
log-slave-updates=1
binlog_format=row
#
##relay log
skip_slave_start=1

# Disabling symbolic-links is recommended to prevent assorted security risks
symbolic-links=0

log-error=/var/log/mysqld.log
pid-file=/var/run/mysqld/mysqld.pid

```

