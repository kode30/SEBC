Show the hostname of the database server

mysql> show variables where Variable_name like '%host%';
+---------------+----------+
| Variable_name | Value    |
+---------------+----------+
| hostname      | cdh-srv1 |
| report_host   |          |
+---------------+----------+
2 rows in set (0.00 sec)
Show the database server version

$ mysql -V
mysql  Ver 14.14 Distrib 5.1.73, for redhat-linux-gnu (x86_64) using readline 5.1
Lists all the databases in the server

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
