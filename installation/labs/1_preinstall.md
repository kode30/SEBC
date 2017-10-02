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


$ sudo yum install mysql.x86_64 -y

Installed:
  mysql.x86_64 0:5.1.73-8.el6_8                                                                                    
Complete!

###  <center> Download and copy the JDBC connector to all nodes.
