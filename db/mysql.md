# 数据库通用规范指导

采用MySQL5.7的版本
编码采用utf8编码
大小写不敏感
一个数据库一个用户

## 数据库更新流程

【开发人员】----【技术主管审批】-----【项目经理审批】----【架构组审批】----【运维组执行】



## MySQL创建数据库/用户，并授权

``` sql
create database xx default character set utf8mb4 collate utf8mb4_unicode_ci;
grant all on xx.* to 'xx'@'%' identified by 'xx@123';
```

## Oracle创建数据库/用户，并授权

``` sql
create user 用户名 identified by "密码";
grant dba to 用户名;
```

## SQL脚本文件规范

SQL脚本文件规范，

- SQL脚本文件名称：<数据库名称>-<时间>-[编号].sql，比如：xx-20210520-1.sql
- SQL脚本使用UTF-8编码，不要使用gbk等其它编码格式
- SQL脚本使用SQL格式化（选用）


## 执行DDL语句规范

DDL脚本语句规范：

    CREATE语句不需要特别说明
    有DROP，TRUNCATE等语句需要特别说明原因


## 执行DML语句规范

执行DML语句规范：

    DELETE语句需要特殊说明



## SQL语句错误



