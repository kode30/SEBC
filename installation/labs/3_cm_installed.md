## Establish Your Cloudera Manager Repository Strategy
Standard Cloudera repositories. For this method, ensure you have added the required repository information to your systems.
### RHEL-compatible
1. Save the appropriate Cloudera Manager repo file (cloudera-manager.repo) for your system.
2. Copy the repo file to the /etc/yum.repos.d/ directory.
``` 
$ sudo wget https://archive.cloudera.com/cm5/redhat/6/x86_64/cm/cloudera-manager.repo
```
```
$ sudo wget https://archive.cloudera.com/cm5/redhat/7/x86_64/cm/cloudera-manager.repo
``` 


``` 
$ sudo nano cloudera-manager.repo 

   [cloudera-manager]
   # Packages for Cloudera Manager, Version 5, on RedHat or CentOS 6 x86_64
   name=Cloudera Manager
   baseurl=https://archive.cloudera.com/cm5/redhat/6/x86_64/cm/5.11/
   gpgkey =https://archive.cloudera.com/cm5/redhat/6/x86_64/cm/RPM-GPG-KEY-cloudera
   gpgcheck = 1
``` 

``` 
$ sudo nano cloudera-manager.repo 

   [cloudera-manager]
   # Packages for Cloudera Manager, Version 5, on RedHat or CentOS 6 x86_64
   name=Cloudera Manager
   baseurl=https://archive.cloudera.com/cm5/redhat/6/x86_64/cm/5.13.1/
   gpgkey =https://archive.cloudera.com/cm5/redhat/6/x86_64/cm/RPM-GPG-KEY-cloudera
   gpgcheck = 1
``` 


## Install a supported Oracle JDK on your first node
``` 
$ wget https://archive.cloudera.com/cm5/redhat/6/x86_64/cm/5.11/RPMS/x86_64/oracle-j2sd
k1.7-1.7.0+update67-1.x86_64.rpm
--2017-10-02 20:14:39--  https://archive.cloudera.com/cm5/redhat/6/x86_64/cm/5.11/RPMS/x86_64/oracle-j2sdk1.7-1
.7.0+update67-1.x86_64.rpm
Resolving archive.cloudera.com... 151.101.0.167, 151.101.64.167, 151.101.128.167, ...
Connecting to archive.cloudera.com|151.101.0.167|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 142039186 (135M) [application/x-redhat-package-manager]
Saving to: “oracle-j2sdk1.7-1.7.0+update67-1.x86_64.rpm”
100%[=====================================================================>] 142,039,186 68.8M/s   in 2.0s    
2017-10-02 20:14:41 (68.8 MB/s) - “oracle-j2sdk1.7-1.7.0+update67-1.x86_64.rpm” saved [142039186/142039186]
``` 

``` 
$ sudo gsutil cp gs://mktg-pov.bigdata.clemerin.com/install/jdk-8u151-linux-x64.rpm jdk-8u151-linux-x64.rpm


Copying gs://mktg-pov.bigdata.clemerin.com/install/jdk-8u151-linux-x64.rpm...
==> NOTE: You are downloading one or more large file(s), which would            
run significantly faster if you enabled sliced object downloads. This
feature is enabled by default but requires that compiled crcmod be
installed (see "gsutil help crcmod").
\ [1 files][166.1 MiB/166.1 MiB]                                                
Operation completed over 1 objects/166.1 MiB.  
```

```
$ sudo mkdir /usr/java
$ cd /usr/java
$ sudo rpm -ivh /tmp/jdk-8u151-linux-x64.rpm

Preparing...                          ################################# [100%]
Updating / installing...
   1:jdk1.8-2000:1.8.0_151-fcs        ################################# [100%]
Unpacking JAR files...
        tools.jar...
        plugin.jar...
        javaws.jar...
        deploy.jar...
        rt.jar...
        jsse.jar...
        charsets.jar...
        localedata.jar...
```


``` 
$ sudo mkdir /usr/java
$ cd /usr/java
$ sudo rpm -ivh /home/andres_wagner/oracle-j2sdk1.7-1.7.0+update67-1.x86_64.rpm 

warning: /home/andres_wagner/oracle-j2sdk1.7-1.7.0+update67-1.x86_64.rpm: Header V4 DSA/SHA1 Signature, key ID 
e8f86acd: NOKEY
Preparing...                ########################################### [100%]
   1:oracle-j2sdk1.7        ########################################### [100%]
``` 

# Edit the system PATH file /etc/profile and add the following system variables to your system path
``` 
$ sudo nano /etc/profile
  JAVA_HOME=/usr/java/jdk1.7.0_67-cloudera 
  JRE_HOME=/usr/java/jdk1.7.0_67-cloudera 
  PATH=$PATH:$JRE_HOME/bin:$JAVA_HOME/bin
  export JAVA_HOME
  export JRE_HOME
  export PATH
``` 

##### Inform where your Oracle Java JDK/JRE is located. 
``` 
$ sudo update-alternatives --install "/usr/bin/java" "java" "/usr/local/java/jdk1.7.0_67/bin/java" 1
$ sudo update-alternatives --install "/usr/bin/javac" "javac" "/usr/local/java/jdk1.7.0_67/bin/javac" 1
$ sudo update-alternatives --install "/usr/bin/javaws" "javaws" "/usr/local/java/jdk1.7.0_67/bin/javaws" 1
``` 

##### Inform that Oracle Java JDK/JRE must be the default Java.
``` 
$ sudo update-alternatives --set java /usr/java/jdk1.7.0_67-cloudera/bin/java   
$ sudo update-alternatives --set javac /usr/java/jdk1.7.0_67-cloudera/bin/javac 
$ sudo update-alternatives --set javaws /usr/java/jdk1.7.0_67-cloudera/bin/javaws
``` 

##### Reload your system wide PATH /etc/profile by typing the following command:
``` 
$ source /etc/profile

$ java -version
``` 

## Install the Cloudera Manager Server Packages
``` 
   $ sudo yum install cloudera-manager-daemons cloudera-manager-server

     Installing : cloudera-manager-daemons-5.11.2-1.cm5112.p0.6.el6.x86_64                                       1/2 
     Installing : cloudera-manager-server-5.11.2-1.cm5112.p0.6.el6.x86_64                                        2/2 
     Verifying  : cloudera-manager-server-5.11.2-1.cm5112.p0.6.el6.x86_64                                        1/2 
     Verifying  : cloudera-manager-daemons-5.11.2-1.cm5112.p0.6.el6.x86_64                                       2/2 
   Installed:
     cloudera-manager-daemons.x86_64 0:5.11.2-1.cm5112.p0.6.el6                                                      
     cloudera-manager-server.x86_64 0:5.11.2-1.cm5112.p0.6.el6                                                       
   Complete!
``` 

``` 
$ sudo /usr/share/cmf/schema/scm_prepare_database.sh --user root -pcloudera mysql cloudera_manager cloudera_manager cloudera
y

JAVA_HOME=/usr/java/jdk1.7.0_67-cloudera
Verifying that we can write to /etc/cloudera-scm-server
Creating SCM configuration file in /etc/cloudera-scm-server
Executing:  /usr/java/jdk1.7.0_67-cloudera/bin/java -cp /usr/share/java/mysql-connector-java.jar:/usr/share/java/oracle-connector-java.jar:/usr/share/cmf/sc
hema/../lib/* com.cloudera.enterprise.dbutil.DbCommandExecutor /etc/cloudera-scm-server/db.properties com.cloudera.cmf.db.
[                          main] DbCommandExecutor              INFO  Successfully connected to database.
All done, your SCM database is configured correctly!

$ sudo service cloudera-scm-server start
``` 
