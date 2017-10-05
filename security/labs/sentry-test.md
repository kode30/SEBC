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
0: jdbc:hive2://cdh-srv4.c.safari-lab.interna> CREATE ROLE sentry_admin;
INFO  : Compiling command(queryId=hive_20171005200808_64750aeb-1155-448f-a0a1-03608c1d3afa): CREATE ROLE sentry_admin
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20171005200808_64750aeb-1155-448f-a0a1-03608c1d3afa); Time taken: 0.096 seconds
INFO  : Executing command(queryId=hive_20171005200808_64750aeb-1155-448f-a0a1-03608c1d3afa): CREATE ROLE sentry_admin
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20171005200808_64750aeb-1155-448f-a0a1-03608c1d3afa); Time taken: 0.435 seconds
INFO  : OK
No rows affected (0.551 seconds)
0: jdbc:hive2://cdh-srv4.c.safari-lab.interna> GRANT ALL ON SERVER server1 TO ROLE sentry_admin;
INFO  : Compiling command(queryId=hive_20171005200808_42afd560-7b91-46a2-9638-340428ecdcd8): GRANT ALL ON SERVER server1 TO ROLE sentry_admin
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20171005200808_42afd560-7b91-46a2-9638-340428ecdcd8); Time taken: 0.12 seconds
INFO  : Executing command(queryId=hive_20171005200808_42afd560-7b91-46a2-9638-340428ecdcd8): GRANT ALL ON SERVER server1 TO ROLE sentry_admin
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20171005200808_42afd560-7b91-46a2-9638-340428ecdcd8); Time taken: 0.153 seconds
INFO  : OK
No rows affected (0.288 seconds)
```
```
0: jdbc:hive2://cdh-srv4.c.safari-lab.interna> GRANT ROLE sentry_admin TO GROUP andreswagner;
INFO  : Compiling command(queryId=hive_20171005200909_19a223fa-e4be-49e0-8417-713dc8405ea9): GRANT ROLE sentry_admin TO GROUP andreswagner
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20171005200909_19a223fa-e4be-49e0-8417-713dc8405ea9); Time taken: 0.089 seconds
INFO  : Executing command(queryId=hive_20171005200909_19a223fa-e4be-49e0-8417-713dc8405ea9): GRANT ROLE sentry_admin TO GROUP andreswagner
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20171005200909_19a223fa-e4be-49e0-8417-713dc8405ea9); Time taken: 0.081 seconds
INFO  : OK
No rows affected (0.187 seconds)
```
```
0: jdbc:hive2://cdh-srv4.c.safari-lab.interna> SHOW TABLES;
INFO  : Compiling command(queryId=hive_20171005200909_e43d0b71-6213-49b1-ae5b-968aef0384fc): SHOW TABLES
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20171005200909_e43d0b71-6213-49b1-ae5b-968aef0384fc); Time taken: 0.086 seconds
INFO  : Executing command(queryId=hive_20171005200909_e43d0b71-6213-49b1-ae5b-968aef0384fc): SHOW TABLES
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20171005200909_e43d0b71-6213-49b1-ae5b-968aef0384fc); Time taken: 0.197 seconds
INFO  : OK
+------------+--+
|  tab_name  |
+------------+--+
| customers  |
| sample_07  |
| sample_08  |
| web_logs   |
+------------+--+
4 rows selected (0.361 seconds)
0: jdbc:hive2://cdh-srv4.c.safari-lab.interna> 
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
