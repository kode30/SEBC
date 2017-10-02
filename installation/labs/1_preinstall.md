1. Check vm.swappiness on all your nodes
sudo nano /proc/sys/vm/swappiness
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
