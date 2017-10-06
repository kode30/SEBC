# Challenge 2: Install Cloudera Manager 5.11

List the command and output for ls /etc/yum.repos.d
```
$ ls /etc/yum.repos.d
CentOS-Base.repo       CentOS-SCLo-scl.repo     epel-testing.repo
CentOS-Debuginfo.repo  CentOS-SCLo-scl-rh.repo  google-cloud.repo
CentOS-fasttrack.repo  CentOS-Vault.repo
CentOS-Media.repo      epel.repo
```

Connect Cloudera Manager Server to its database
Use the scm_prepare_database.sh script to create the db.properties file
List the full command and its output

```
$ sudo /usr/share/cmf/schema/scm_prepare_database.sh -hcdh-srv1 -uroot -pcloudera mysql cloudera_manager cloudera_manager cloudera
JAVA_HOME=/usr/java/jdk1.7.0_67-cloudera
Verifying that we can write to /etc/cloudera-scm-server
Creating SCM configuration file in /etc/cloudera-scm-server
Executing:  /usr/java/jdk1.7.0_67-cloudera/bin/java -cp /usr/share/java/mysql-connector-java.jar:/usr/share/java/oracle-connector-java.jar:/usr/share/cmf/schema/../lib/* com.cloudera.enterprise.dbutil.DbCommandExecutor /etc/cloudera-scm-server/db.properties com.cloudera.cmf.db.
[                          main] DbCommandExecutor              INFO  Successfully connected to database.
All done, your SCM database is configured correctly!
``` 
```
[andreswagner@cdh-srv2 java]$ sudo service cloudera-scm-server start
Starting cloudera-scm-server:                              [  OK  ]
```
