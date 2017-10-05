### Verify user privileges

* Authenticate your user as a Kerberos principal
* Use beeline to confirm your principal sees no tables
  * !connect jdbc:hive2://localhost:10000/default;principal=hive/fdqn@REALM.COM
    * Replace fqdn with your host's fully-qualified domain name
  * Use your Linux account/password to authenticate when prompted
  * Enter SHOW TABLES;
  * The statement should return an empty set because no authorizations are in place
* Copy the transcript of this section to security/labs/sentry-test.md

```
$ beeline
Beeline version 1.1.0-cdh5.11.2 by Apache Hive
```

```
beeline> !connect jdbc:hive2://cdh-srv4.c.safari-lab.internal:10000/default;principal=hive/cdh-srv4.c.safari-lab.internal@C.SAFARI-LAB.INTERNAL
scan complete in 2ms
Connecting to jdbc:hive2://cdh-srv4.c.safari-lab.internal:10000/default;principal=hive/cdh-srv4.c.safari-lab.internal@C.SAFARI-LAB.INTERNAL
Connected to: Apache Hive (version 1.1.0-cdh5.11.2)
Driver: Hive JDBC (version 1.1.0-cdh5.11.2)
Transaction isolation: TRANSACTION_REPEATABLE_READ
```
```
0: jdbc:hive2://cdh-srv4.c.safari-lab.interna> SHOW TABLES;
INFO  : Compiling command(queryId=hive_20171005200606_a854967b-8a42-4247-b68e-bae6ae863d18): SHOW TABLES
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20171005200606_a854967b-8a42-4247-b68e-bae6ae863d18); Time taken: 0.77 seconds
INFO  : Executing command(queryId=hive_20171005200606_a854967b-8a42-4247-b68e-bae6ae863d18): SHOW TABLES
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20171005200606_a854967b-8a42-4247-b68e-bae6ae863d18); Time taken: 0.436 seconds
INFO  : OK
+-----------+--+
| tab_name  |
+-----------+--+
+-----------+--+
No rows selected (2.637 seconds)
0: jdbc:hive2://cdh-srv4.c.safari-lab.interna> 
```
### Create a Sentry role with full authorization 
* In `beeline`:
    * `CREATE ROLE sentry_admin;`
    * `GRANT ALL ON SERVER server1 TO ROLE sentry_admin;`
    * `GRANT ROLE sentry_admin TO GROUP {your_primary};`
    * `SHOW TABLES;`
* The statement should now return all tables


```
$ beeline
Beeline version 1.1.0-cdh5.11.2 by Apache Hive
beeline> !connect jdbc:hive2://cdh-srv4.c.safari-lab.internal:10000/default;principal=hive/cdh-srv4.c.safari-lab.internal@C.SAFARI-LAB.INTERNAL
scan complete in 3ms
Connecting to jdbc:hive2://cdh-srv4.c.safari-lab.internal:10000/default;principal=hive/cdh-srv4.c.safari-lab.internal@C.SAFARI-LAB.INTERNAL
Connected to: Apache Hive (version 1.1.0-cdh5.11.2)
Driver: Hive JDBC (version 1.1.0-cdh5.11.2)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://cdh-srv4.c.safari-lab.interna> SHOW TABLES;
INFO  : Compiling command(queryId=hive_20171005185555_8cba6bb2-8217-428b-b5bb-11138d86a999): SHOW TABLES
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20171005185555_8cba6bb2-8217-428b-b5bb-11138d86a999); Time taken: 0.049 seconds
INFO  : Executing command(queryId=hive_20171005185555_8cba6bb2-8217-428b-b5bb-11138d86a999): SHOW TABLES
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20171005185555_8cba6bb2-8217-428b-b5bb-11138d86a999); Time taken: 0.05 seconds
INFO  : OK
+------------+--+
|  tab_name  |
+------------+--+
| customers  |
| sample_07  |
| sample_08  |
| web_logs   |
+------------+--+
4 rows selected (0.376 seconds)
0: jdbc:hive2://cdh-srv4.c.safari-lab.interna> !quit
Closing: 0: jdbc:hive2://cdh-srv4.c.safari-lab.internal:10000/default;principal=hive/cdh-srv4.c.safari-lab.internal@C.SAFARI-LAB.INTERNAL
```

Create additional test users

Add new users to all cluster nodes
$ sudo groupadd selector
$ sudo groupadd inserters
$ sudo useradd -u 1100 -g selector george
$ sudo useradd -u 1200 -g inserters ferdinand


add_principal george and ferdinand
```
add_principal george
$ sudo kadmin.local
Authenticating as principal cloudera-scm/admin@C.SAFARI-LAB.INTERNAL with password.
kadmin.local:  add_principal george
WARNING: no policy specified for george@C.SAFARI-LAB.INTERNAL; defaulting to no policy
Enter password for principal "george@C.SAFARI-LAB.INTERNAL": 
Re-enter password for principal "george@C.SAFARI-LAB.INTERNAL": 
Principal "george@C.SAFARI-LAB.INTERNAL" created.
kadmin.local:  add_principal ferdinand
WARNING: no policy specified for ferdinand@C.SAFARI-LAB.INTERNAL; defaulting to no policy
Enter password for principal "ferdinand@C.SAFARI-LAB.INTERNAL": 
Re-enter password for principal "ferdinand@C.SAFARI-LAB.INTERNAL": 
Principal "ferdinand@C.SAFARI-LAB.INTERNAL" created.
```

```
kadmin.local:  quit
```

Create test roles

Login to beeline as your admin user
```
$ beeline
```

```
!connect jdbc:hive2://cdh-srv4.c.safari-lab.internal:10000/default;principal=hive/cdh-srv4.c.safari-lab.internal@C.SAFARI-LAB.INTERNAL

scan complete in 2ms
Connecting to jdbc:hive2://cdh-srv4.c.safari-lab.internal:10000/default;principal=hive/cdh-srv4.c.safari-lab.internal@C.SAFARI-LAB.INTERNAL
Connected to: Apache Hive (version 1.1.0-cdh5.11.2)
Driver: Hive JDBC (version 1.1.0-cdh5.11.2)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://cdh-srv4.c.safari-lab.interna> 
```

CREATE ROLE reads;
CREATE ROLE writes;
