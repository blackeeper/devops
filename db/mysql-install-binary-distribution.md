
mysql install binary distribution
==========================================

安装命令：

``` bash

    groupadd mysql
    useradd -r -g mysql -s /bin/false mysql
    cd /usr/local
    tar zxvf /path/to/mysql-VERSION-OS.tar.gz
    ln -s full-path-to-mysql-VERSION-OS mysql
    cd mysql
    mkdir mysql-files
    chown mysql:mysql mysql-files
    chmod 750 mysql-files
    bin/mysqld --initialize --user=mysql
    bin/mysql_ssl_rsa_setup
    bin/mysqld_safe --user=mysql &
    command is optional
    cp support-files/mysql.server /etc/init.d/mysql.server

```


