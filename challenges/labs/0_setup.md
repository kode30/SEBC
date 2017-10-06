* cloud provider: GCE

* instances by IP address and DNS
  * 
  *
  *
  *

* Linux release: centos-release-6-9.el6.12.3.x86_64

* File system capacity for the first node: 
```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       296G  1.3G  279G   1% /
tmpfs            15G     0   15G   0% /dev/shm
```

* command and output for yum repolist enabled:
```
$ yum repolist enabled
Loaded plugins: fastestmirror, security
Loading mirror speeds from cached hostfile
 * base: mirrors.thaidns.co.th
 * epel: mirror.steadfast.net
 * extras: mirrors.liquidweb.com
 * updates: mirror.us.oneandone.net
repo id                 repo name                                         status
base                    CentOS-6 - Base                                    6,706
centos-sclo-rh          CentOS-6 - SCLo rh                                 5,785
centos-sclo-sclo        CentOS-6 - SCLo sclo                                 460
epel                    Extra Packages for Enterprise Linux 6 - x86_64    12,402
extras                  CentOS-6 - Extras                                     46
google-cloud-compute    Google Cloud Compute                                   7
updates                 CentOS-6 - Updates                                   697
repolist: 26,103
```

* Add the haley and saturnm Linux accounts to all nodes
```  
$ sudo groupadd comets
$ sudo groupadd planets
$ sudo useradd -u 2800 -g comets haley
$ sudo useradd -u 2900 -g planets saturn
```
* List the /etc/passwd entries for saturn and haley
```
haley:x:2800:503::/home/haley:/bin/bash
saturn:x:2900:504::/home/saturn:/bin/bash
```
* List the /etc/group entries for comets and planets
```
comets:x:503:
planets:x:504:
```
