## <center> System Configuration Checks
1. Check vm.swappiness on all your nodes
$ cat /proc/sys/vm/swappiness

60

$sudo nano /proc/sys/vm/swappiness

1

$ cat /proc/sys/vm/swappiness

1

2. mount attributes of your volume(s)
lsblk

NAME   MAJ:MIN RM SIZE RO TYPE MOUNTPOINT
sdc      8:32   0  80G  0 disk /mnt/data_log
sdb      8:16   0  80G  0 disk /mnt/data_cloudera
sda      8:0    0  80G  0 disk 
└─sda1   8:1    0  80G  0 part /

3. ext-based volumes, list the reserve space setting

4. Disable transparent hugepage support
sudo nano /etc/rc.local
echo never > /sys/kernel/mm/transparent_hugepage/defrag
echo never > /sys/kernel/mm/transparent_hugepage/enabled

5. List your network interface configuration
$ ip link show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1460 qdisc mq state UP qlen 1000
    link/ether 42:01:0a:80:00:0b brd ff:ff:ff:ff:ff:ff


6. Show that forward and reverse host lookups are correctly resolved

$ hostname -f
cdh-i1.c.safari-lab.internal

$ nslookup cdh-i1.c.safari-lab.internal
Server:         169.254.169.254
Address:        169.254.169.254#53
Non-authoritative answer:
Name:   cdh-i1.c.safari-lab.internal
Address: 10.128.0.11

$ nslookup cdh-i1.c.safari-lab.internal
Server:         169.254.169.254
Address:        169.254.169.254#53
Non-authoritative answer:
Name:   cdh-i1.c.safari-lab.internal
Address: 10.128.0.11

$ nslookup 10.128.0.11
Server:         169.254.169.254
Address:        169.254.169.254#53
Non-authoritative answer:
11.0.128.10.in-addr.arpa        name = cdh-i1.c.safari-lab.internal.

7. Show the nscd service is running

$ sudo nscd -g

nscd: nscd not running!

$ sudo service nscd start

Starting nscd:                                             [  OK  ]

$ sudo nscd -g

nscd configuration:

              0  server debug level
            52s  server runtime
              5  current number of threads
             32  maximum number of threads
              0  number of times clients had to wait
             no  paranoia mode enabled
           3600  restart internal
              5  reload count

passwd cache:

            yes  cache is enabled
            yes  cache is persistent
            yes  cache is shared
            211  suggested size
         216064  total data pool size
            344  used data pool size
            600  seconds time to live for positive entries
             20  seconds time to live for negative entries
              0  cache hits on positive entries
              0  cache hits on negative entries
              2  cache misses on positive entries
              0  cache misses on negative entries
              0% cache hit rate
              4  current number of cached values
              4  maximum number of cached values
              0  maximum chain length searched
              0  number of delays on rdlock
              0  number of delays on wrlock
              0  memory allocations failed
            yes  check /etc/passwd for changes

group cache:

            yes  cache is enabled
            yes  cache is persistent
            yes  cache is shared
            211  suggested size
         216064  total data pool size
            248  used data pool size
           3600  seconds time to live for positive entries
             60  seconds time to live for negative entries
              0  cache hits on positive entries
              0  cache hits on negative entries
              1  cache misses on positive entries
              1  cache misses on negative entries
              0% cache hit rate
              3  current number of cached values
              3  maximum number of cached values
              0  maximum chain length searched
              0  number of delays on rdlock
              0  number of delays on wrlock
              0  memory allocations failed
            yes  check /etc/group for changes

hosts cache:

            yes  cache is enabled
            yes  cache is persistent
            yes  cache is shared
            211  suggested size
         216064  total data pool size
              0  used data pool size
           3600  seconds time to live for positive entries
             20  seconds time to live for negative entries
              0  cache hits on positive entries
              0  cache hits on negative entries
              0  cache misses on positive entries
              0  cache misses on negative entries
              0% cache hit rate
              0  current number of cached values
              0  maximum number of cached values
              0  maximum chain length searched
              0  number of delays on rdlock
              0  number of delays on wrlock
              0  memory allocations failed
            yes  check /etc/hosts for changes

services cache:

            yes  cache is enabled
            yes  cache is persistent
            yes  cache is shared
            211  suggested size
         216064  total data pool size
              0  used data pool size
          28800  seconds time to live for positive entries
             20  seconds time to live for negative entries
              0  cache hits on positive entries
              0  cache hits on negative entries
              0  cache misses on positive entries
              0  cache misses on negative entries
              0% cache hit rate
              0  current number of cached values
              0  maximum number of cached values
              0  maximum chain length searched
              0  number of delays on rdlock
              0  number of delays on wrlock
              0  memory allocations failed
            yes  check /etc/services for changes
              5  reload count
netgroup cache:
            yes  cache is enabled
            yes  cache is persistent
            yes  cache is shared
            211  suggested size
         216064  total data pool size
              0  used data pool size
          28800  seconds time to live for positive entries
             20  seconds time to live for negative entries
              0  cache hits on positive entries
              0  cache hits on negative entries
              0  cache misses on positive entries
              0  cache misses on negative entries
              0% cache hit rate
              0  current number of cached values
              0  maximum number of cached values
              0  maximum chain length searched
              0  number of delays on rdlock
              0  number of delays on wrlock
              0  memory allocations failed
            yes  check /etc/netgroup for changes
SELinux AVC Statistics:
             11  entry lookups
              8  entry hits
              3  entry misses
              2  entry discards
              3  CAV lookups
              1  CAV hits
              2  CAV probes
              2  CAV misses
              
8. Show the ntpd service is running

$ chkconfig --list ntpd

    ntpd            0:off   1:off   2:on    3:on    4:on    5:on    6:off

$ ntpq -p

    remote           refid      st t when poll reach   delay   offset  jitter
    ==============================================================================
    *metadata.google 71.79.79.71      2 u   92  128  377    0.331   -1.494   0.187
    
## <center> MySQL/MariaDB Installation Lab
### <center> Enable the repo to install MySQL 5.5
$ yum --showduplicates list mysql

Loaded plugins: fastestmirror, security
Loading mirror speeds from cached hostfile
 * base: centos.mirrors.tds.net
 * epel: mirror.steadfast.net
 * extras: repos.dfw.quadranet.com
 * updates: mirror.tzulo.com
 * webtatic: us-east.repo.webtatic.com
webtatic                                                                                    | 3.6 kB     00:00     
webtatic/primary_db                                                                         | 208 kB     00:00     
Available Packages
mysql.x86_64                                          5.1.73-8.el6_8                                           base


$ sudo yum install mysql mysql-server -y
                                                                                  
Complete!

$ sudo service mysqld start

$ service mysqld status

mysqld (pid  708) is running...

### Use /usr/bin/mysql_secure_installation to:
$ sudo /usr/bin/mysql_secure_installation

NOTE: RUNNING ALL PARTS OF THIS SCRIPT IS RECOMMENDED FOR ALL MySQL
      SERVERS IN PRODUCTION USE!  PLEASE READ EACH STEP CAREFULLY!
In order to log into MySQL to secure it, we'll need the current
password for the root user.  If you've just installed MySQL, and
you haven't set the root password yet, the password will be blank,
so you should just press enter here.
Enter current password for root (enter for none): 

#### Set password protection for the server
Set root password? [Y/n] y
New password: 
Re-enter new password: 
Password updated successfully!
Reloading privilege tables..
 ... Success!
 
#### b. Revoke permissions for anonymous users
 By default, a MySQL installation has an anonymous user, allowing anyone
to log into MySQL without having to have a user account created for
them.  This is intended only for testing, and to make the installation
go a bit smoother.  You should remove them before moving into a
production environment.

Remove anonymous users? [Y/n] n

#### c. Permit remote privileged login

Normally, root should only be allowed to connect from 'localhost'.  This
ensures that someone cannot guess at the root password from the network.

Disallow root login remotely? [Y/n] n

#### d. Remove test databases
By default, MySQL comes with a database named 'test' that anyone can
access.  This is also intended only for testing, and should be removed
before moving into a production environment.

Remove test database and access to it? [Y/n] n

#### e. Refresh privileges in memory
Reloading the privilege tables will ensure that all changes made so far
will take effect immediately.

Reload privilege tables now? [Y/n] y

#### f. Refreshes the mysqld service

$ sudo service mysqld restart
Stopping mysqld:                                           [  OK  ]
No such file or directory
Starting mysqld:                                           [  OK  ]


Move old InnoDB log files /var/lib/mysql/ib_logfile0 and /var/lib/mysql/ib_logfile1 out of /var/lib/mysql/ to a backup location.

$ sudo service mysqld stop

$ sudo nano /etc/my.cnf
    [mysqld]
    transaction-isolation = READ-COMMITTED
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

$ sudo mv /var/lib/mysql/ib_logfile0 /var/lib/mysql.bak
$ sudo mv /var/lib/mysql/ib_logfile1 /var/lib/mysql_ib_logfile1.bak


### Ensure the MySQL server starts at boot.
$ sudo /sbin/chkconfig mysqld on 
$ sudo /sbin/chkconfig --list mysqld
    ysqld          0:off   1:off   2:on    3:on    4:on    5:on    6:off

$ sudo service mysqld start
    starting mysqld:                                           [  OK  ]
    
###  <center> Installing the MySQL JDBC Driver

$ wget https://dev.mysql.com/get/Downloads/Connector-J/mysql-connector-java-5.1.44.zip -O m
ysql_jdbc.zip

sudo cp -pR mysql-connector-java-5.1.44 /usr/share/java/
$unzip mysql_jdbc.zip 

$ cd /usr/share/java/
$ ls
build.xml  CHANGES  COPYING  mysql-connector-java-5.1.44-bin.jar  README  README.txt  src

$ mv mysql-connector-java-5.1.44-bin.jar mysql-connector-java.jar
$ ls
build.xml  CHANGES  COPYING  mysql-connector-java.jar  README  README.txt  src


## Creating Databases
Log into MySQL as the root user:
    $ mysql -u root -p
    
Create databases for the Activity Monitor, Reports Manager, Hive Metastore Server, Sentry Server, Cloudera Navigator Audit Server, and Cloudera Navigator Metadata Server:
    create database amon DEFAULT CHARACTER SET utf8;
    create database rman DEFAULT CHARACTER SET utf8;
    create database metastore DEFAULT CHARACTER SET utf8;
    create database sentry DEFAULT CHARACTER SET utf8;
    create database nav DEFAULT CHARACTER SET utf8;
    create database navms DEFAULT CHARACTER SET utf8;
    
    mysql>     create database amon DEFAULT CHARACTER SET utf8;
    Query OK, 1 row affected (0.00 sec)
    mysql>     create database rman DEFAULT CHARACTER SET utf8;
    Query OK, 1 row affected (0.00 sec)
    mysql>     create database metastore DEFAULT CHARACTER SET utf8;
    Query OK, 1 row affected (0.00 sec)
    mysql>     create database sentry DEFAULT CHARACTER SET utf8;
    Query OK, 1 row affected (0.00 sec)
    mysql>     create database nav DEFAULT CHARACTER SET utf8;
    Query OK, 1 row affected (0.00 sec)
    mysql>     create database navms DEFAULT CHARACTER SET utf8;
    Query OK, 1 row affected (0.00 sec)
    
    
    grant all on amon.* TO 'amon'@'%' IDENTIFIED BY 'cloudera';
    grant all on rman.* TO 'rman'@'%' IDENTIFIED BY 'cloudera';
    grant all on metastore.* TO 'metastore'@'%' IDENTIFIED BY 'cloudera';
    grant all on sentry.* TO 'sentry'@'%' IDENTIFIED BY 'cloudera';
    grant all on nav.* TO 'nav'@'%' IDENTIFIED BY 'cloudera';
    grant all on navms.* TO 'navms'@'%' IDENTIFIED BY 'cloudera';
    
    mysql> grant all on amon.* TO 'amon'@'%' IDENTIFIED BY 'cloudera';
    Query OK, 0 rows affected (0.00 sec)
    mysql>     grant all on rman.* TO 'rman'@'%' IDENTIFIED BY 'cloudera';
    Query OK, 0 rows affected (0.00 sec)
    mysql>     grant all on metastore.* TO 'metastore'@'%' IDENTIFIED BY 'cloudera';
    Query OK, 0 rows affected (0.00 sec)
    mysql>     grant all on sentry.* TO 'sentry'@'%' IDENTIFIED BY 'cloudera';
    Query OK, 0 rows affected (0.00 sec)
    mysql>     grant all on nav.* TO 'nav'@'%' IDENTIFIED BY 'cloudera';
    Query OK, 0 rows affected (0.00 sec)
    mysql>     grant all on navms.* TO 'navms'@'%' IDENTIFIED BY 'cloudera';
    Query OK, 0 rows affected (0.00 sec)
