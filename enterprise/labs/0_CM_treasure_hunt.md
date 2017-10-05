* What is ubertask optimization?
"ubertask" optimization, which runs "sufficiently small" jobs sequentially within a single JVM.

* Where in CM is the Kerberos Security Realm value displayed?
In the Cloudera Manager Admin Console, select Administration > Settings.
Then search for REALM
* Which CDH service(s) host a property for enabling Kerberos authentication?
The CM service

* How do you upgrade the CM agents?
on the Cloudera Manager host using operating system package commands from the command line (for example, yum on RHEL systems).
on all the other cluster hosts, using The Cloudera Manager upgrade wizard can upgrade the agent software

* Give the tsquery statement used to chart Hue's CPU utilization?
select agent_cpu_system_rate+agent_cpu_user_rate where category=ROLE and serviceName=hue

* Name all the roles that make up the Hive service
Hive Metastore Server
WebHCat Server
HiverServer2
Gateway

* What steps must be completed before integrating Cloudera Manager with Kerberos?
A working KDC with renewable tickets
Kerberos client libraries on all hosts
An account with permissions to create other accounts in KDC
Java Crypto Libraries available on all on all hosts
