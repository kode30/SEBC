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
```

```
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

### Create additional test users

Add new users to all cluster nodes
$ sudo groupadd selector
$ sudo groupadd inserters
$ sudo useradd -u 1100 -g selector george
$ sudo useradd -u 1200 -g inserters ferdinand


add_principal george and ferdinand
```
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

```

0: jdbc:hive2://cdh-srv4.c.safari-lab.interna> CREATE ROLE reads;
INFO  : Compiling command(queryId=hive_20171005201313_78f4749d-4d0b-4716-944b-4e202d3dbf98): CREATE ROLE reads
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20171005201313_78f4749d-4d0b-4716-944b-4e202d3dbf98); Time taken: 0.101 seconds
INFO  : Executing command(queryId=hive_20171005201313_78f4749d-4d0b-4716-944b-4e202d3dbf98): CREATE ROLE reads
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20171005201313_78f4749d-4d0b-4716-944b-4e202d3dbf98); Time taken: 0.034 seconds
INFO  : OK
No rows affected (0.154 seconds)
0: jdbc:hive2://cdh-srv4.c.safari-lab.interna> 
```

CREATE ROLE writes;
```
 
0: jdbc:hive2://cdh-srv4.c.safari-lab.interna> CREATE ROLE writes;
INFO  : Compiling command(queryId=hive_20171005201313_326cfb7a-dde1-4a37-951c-4c46daffc4bf): CREATE ROLE writes
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20171005201313_326cfb7a-dde1-4a37-951c-4c46daffc4bf); Time taken: 0.081 seconds
INFO  : Executing command(queryId=hive_20171005201313_326cfb7a-dde1-4a37-951c-4c46daffc4bf): CREATE ROLE writes
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20171005201313_326cfb7a-dde1-4a37-951c-4c46daffc4bf); Time taken: 0.033 seconds
INFO  : OK
No rows affected (0.13 seconds)
0: jdbc:hive2://cdh-srv4.c.safari-lab.interna> 
```
Grant read privilege for all tables to reads

GRANT SELECT ON DATABASE default TO ROLE reads;
```
0: jdbc:hive2://cdh-srv4.c.safari-lab.interna> GRANT SELECT ON DATABASE default TO ROLE reads;
INFO  : Compiling command(queryId=hive_20171005201515_6f0952c1-0fef-44c2-b358-bff5f59ed661): GRANT SELECT ON DATABASE default TO ROLE reads
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20171005201515_6f0952c1-0fef-44c2-b358-bff5f59ed661); Time taken: 0.078 seconds
INFO  : Executing command(queryId=hive_20171005201515_6f0952c1-0fef-44c2-b358-bff5f59ed661): GRANT SELECT ON DATABASE default TO ROLE reads
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20171005201515_6f0952c1-0fef-44c2-b358-bff5f59ed661); Time taken: 0.033 seconds
INFO  : OK
No rows affected (0.131 seconds)
0: jdbc:hive2://cdh-srv4.c.safari-lab.interna> 

```

GRANT ROLE reads TO GROUP selector;
```
0: jdbc:hive2://cdh-srv4.c.safari-lab.interna> GRANT ROLE reads TO GROUP selector;
INFO  : Compiling command(queryId=hive_20171005201717_9f5c8263-9fcc-45de-b4fc-76cc762988d5): GRANT ROLE reads TO GROUP selector
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20171005201717_9f5c8263-9fcc-45de-b4fc-76cc762988d5); Time taken: 0.085 seconds
INFO  : Executing command(queryId=hive_20171005201717_9f5c8263-9fcc-45de-b4fc-76cc762988d5): GRANT ROLE reads TO GROUP selector
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20171005201717_9f5c8263-9fcc-45de-b4fc-76cc762988d5); Time taken: 0.038 seconds
INFO  : OK
No rows affected (0.143 seconds)
0: jdbc:hive2://cdh-srv4.c.safari-lab.interna> 
```
Grant read privilege for default.sample07 only to 'writes':

REVOKE ALL ON DATABASE default FROM ROLE writes;
```

0: jdbc:hive2://cdh-srv4.c.safari-lab.interna> REVOKE ALL ON DATABASE default FROM ROLE writes;
INFO  : Compiling command(queryId=hive_20171005201818_392f9a02-b750-4353-8a60-c48012603feb): REVOKE ALL ON DATABASE default FROM ROLE writes
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20171005201818_392f9a02-b750-4353-8a60-c48012603feb); Time taken: 0.08 seconds
INFO  : Executing command(queryId=hive_20171005201818_392f9a02-b750-4353-8a60-c48012603feb): REVOKE ALL ON DATABASE default FROM ROLE writes
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20171005201818_392f9a02-b750-4353-8a60-c48012603feb); Time taken: 0.134 seconds
INFO  : OK
No rows affected (0.23 seconds)

```
GRANT SELECT ON default.sample_07 TO ROLE writes;
```

0: jdbc:hive2://cdh-srv4.c.safari-lab.interna> GRANT SELECT ON default.sample_07 TO ROLE writes;
INFO  : Compiling command(queryId=hive_20171005201818_f40c7b9a-17c0-4510-9e1d-77256adfcdf5): GRANT SELECT ON default.sample_07 TO ROLE writes
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20171005201818_f40c7b9a-17c0-4510-9e1d-77256adfcdf5); Time taken: 0.093 seconds
INFO  : Executing command(queryId=hive_20171005201818_f40c7b9a-17c0-4510-9e1d-77256adfcdf5): GRANT SELECT ON default.sample_07 TO ROLE writes
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20171005201818_f40c7b9a-17c0-4510-9e1d-77256adfcdf5); Time taken: 0.047 seconds
INFO  : OK
No rows affected (0.157 seconds)
0: jdbc:hive2://cdh-srv4.c.safari-lab.interna> 
```
GRANT ROLE writes TO GROUP inserters;
```
0: jdbc:hive2://cdh-srv4.c.safari-lab.interna> GRANT ROLE writes TO GROUP inserters;
INFO  : Compiling command(queryId=hive_20171005201818_b74c0865-8357-4c6b-acb9-337a4170ba54): GRANT ROLE writes TO GROUP inserters
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:null, properties:null)
INFO  : Completed compiling command(queryId=hive_20171005201818_b74c0865-8357-4c6b-acb9-337a4170ba54); Time taken: 0.082 seconds
INFO  : Executing command(queryId=hive_20171005201818_b74c0865-8357-4c6b-acb9-337a4170ba54): GRANT ROLE writes TO GROUP inserters
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20171005201818_b74c0865-8357-4c6b-acb9-337a4170ba54); Time taken: 0.031 seconds
INFO  : OK
No rows affected (0.133 seconds)
0: jdbc:hive2://cdh-srv4.c.safari-lab.interna> 
```

```
0: jdbc:hive2://cdh-srv4.c.safari-lab.interna> !quit
Closing: 0: jdbc:hive2://cdh-srv4.c.safari-lab.internal:10000/default;principal=hive/cdh-srv4.c.safari-lab.internal@C.SAFARI-LAB.INTERNAL
```
### kinit as george, then login to beeline

kinit as george, login to beeline, and use SHOW TABLES;
george should be able to see all tables



Repeat the process as ferdinand
ferdinand should see sample_07

Add the transcripts of these sessions to security/labs/sentry-test.md
