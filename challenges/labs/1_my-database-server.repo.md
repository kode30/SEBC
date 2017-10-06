# Challenge 1: Install a MySQL server
```
$ sudo yum install mysql-server -y
$ sudo /sbin/chkconfig --levels 235 mysqld on
```

Then to start the MySQL server:
```
$ sudo service mysqld start
```

Harden MySQL Server
```
$ sudo mysql_secure_installation
```

Root Login
```
mysql -u root -p
```

Additional MySQL Server Config
```
$ sudo service mysqld stop
$ sudo mv /var/lib/mysql/ib_logfile0 /var/lib/mysql.bak 
$ sudo mv /var/lib/mysql/ib_logfile1 /var/lib/mysql_ib_logfile1.bak
```

Update configuration in /etc/my.cnf
```
$ sudo nano /etc/my.cnf

[mysqld] transaction-isolation = READ-COMMITTED 
# Disabling symbolic-links is recommended to prevent assorted security risks; 
# to do so, uncomment this line: 
# symbolic-links = 0

key_buffer_size = 32M
max_allowed_packet = 32M
thread_stack = 256K
thread_cache_size = 64
query_cache_limit = 8M
query_cache_size = 64M
query_cache_type = 1

max_connections = 550
#expire_logs_days = 10
#max_binlog_size = 100M

#log_bin should be on a disk with enough free space. Replace '/var/lib/mysql/mysql_binary_log' with an appropriate path for your system
#and chown the specified folder to the mysql user.
log_bin=/var/lib/mysql/mysql_binary_log

# For MySQL version 5.1.8 or later. For older versions, reference MySQL documentation for configuration help.
binlog_format = mixed

read_buffer_size = 2M
read_rnd_buffer_size = 16M
sort_buffer_size = 8M
join_buffer_size = 8M

# InnoDB settings
innodb_file_per_table = 1
innodb_flush_log_at_trx_commit  = 2
innodb_log_buffer_size = 64M
innodb_buffer_pool_size = 4G
innodb_thread_concurrency = 8
innodb_flush_method = O_DIRECT
innodb_log_file_size = 512M

[mysqld_safe]
log-error=/var/log/mysqld.log
pid-file=/var/run/mysqld/mysqld.pid

sql_mode=STRICT_ALL_TABLES
```

Start the service and check root login
```
$ sudo service mysqld start
$ mysql -u root -p
```

Install the database client package and JDBC connector jar
```
$ wget https://dev.mysql.com/get/Downloads/Connector-J/mysql-connector-java-5.1.44.zip
$ sudo unzip mysql-connector-java-5.1.44.zip
$ cd mysql-connector-java-5.1.44

$ sudo mkdir /usr/share/java/
$ sudo mv mysql-connector-java-5.1.44-bin.jar /usr/share/java/mysql-connector-java.jar
```

Start the database service and create these databases
* scm
* rman
* hive
* oozie
* hue

```
create database amon DEFAULT CHARACTER SET utf8;
create database rman DEFAULT CHARACTER SET utf8;
create database hive DEFAULT CHARACTER SET utf8;
create database sentry DEFAULT CHARACTER SET utf8;
create database hue DEFAULT CHARACTER SET utf8;
create database oozie DEFAULT CHARACTER SET utf8;

grant all on amon.* TO 'amon'@'%' IDENTIFIED BY 'cloudera';
grant all on rman.* TO 'rman'@'%' IDENTIFIED BY 'cloudera';
grant all on hive.* TO hive@'%' IDENTIFIED BY 'cloudera';
grant all on sentry.* TO 'sentry'@'%' IDENTIFIED BY 'cloudera';
grant all on hue.* TO 'hue'@'%' IDENTIFIED BY 'cloudera';
grant all on oozie.* TO 'oozie'@'%' IDENTIFIED BY 'cloudera';
```

Show the hostname of the database server
```
mysql> show variables where Variable_name like '%host%';
+---------------+----------+
| Variable_name | Value    |
+---------------+----------+
| hostname      | cdh-srv1 |
| report_host   |          |
+---------------+----------+
2 rows in set (0.00 sec)
``` 

Show the database server version
```
$ mysql -V
mysql  Ver 14.14 Distrib 5.1.73, for redhat-linux-gnu (x86_64) using readline 5.1
```

Lists all the databases in the server
```
mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| amon               |
| hive               |
| hue                |
| mysql              |
| oozie              |
| rman               |
| sentry             |
+--------------------+
8 rows in set (0.00 sec)
```
