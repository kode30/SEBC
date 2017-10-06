The command and output for hdfs dfs -ls /user
```
$ hdfs dfs -ls /user
Found 7 items
drwxr-xr-x   - hdfs   supergroup          0 2017-10-06 15:54 /user/haley
drwxrwxrwx   - mapred hadoop              0 2017-10-06 15:34 /user/history
drwxrwxr-t   - hive   hive                0 2017-10-06 15:36 /user/hive
drwxrwxr-x   - hue    hue                 0 2017-10-06 15:36 /user/hue
drwxrwxr-x   - oozie  oozie               0 2017-10-06 15:36 /user/oozie
drwxr-xr-x   - hdfs   supergroup          0 2017-10-06 15:54 /user/saturn
drwxr-x--x   - spark  spark               0 2017-10-06 15:35 /user/spark
```
The command and output from the CM API call ../api/v14/hosts
```
# curl -u admin:admin 'http://localhost:7180/api/v14/hosts'
{
  "items" : [ {
    "hostId" : "1e4cb4f5-f5a4-4d64-bc93-042a9db69f35",
    "ipAddress" : "10.128.0.5",
    "hostname" : "cdh-srv1.c.safari-lab.internal",
    "rackId" : "/default",
    "hostUrl" : "http://cdh-srv2.c.safari-lab.internal:7180/cmf/hostRedirect/1e4cb4f5-f5a4-4d64-bc93-042a9db69f35",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 8,
    "numPhysicalCores" : 4,
    "totalPhysMemBytes" : 31688794112
  }, {
    "hostId" : "8d54348e-b2b1-4ddd-a93d-8310f91c0e98",
    "ipAddress" : "10.128.0.6",
    "hostname" : "cdh-srv2.c.safari-lab.internal",
    "rackId" : "/default",
    "hostUrl" : "http://cdh-srv2.c.safari-lab.internal:7180/cmf/hostRedirect/8d54348e-b2b1-4ddd-a93d-8310f91c0e98",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 8,
    "numPhysicalCores" : 4,
    "totalPhysMemBytes" : 31688794112
  }, {
    "hostId" : "ebc1204f-2ac1-41df-906d-a1dd0685fc29",
    "ipAddress" : "10.128.0.7",
    "hostname" : "cdh-srv3.c.safari-lab.internal",
    "rackId" : "/default",
    "hostUrl" : "http://cdh-srv2.c.safari-lab.internal:7180/cmf/hostRedirect/ebc1204f-2ac1-41df-906d-a1dd0685fc29",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 8,
    "numPhysicalCores" : 4,
    "totalPhysMemBytes" : 31688794112
  }, {
    "hostId" : "9b9c235f-dec5-4528-9d12-6dca96738f16",
    "ipAddress" : "10.128.0.8",
    "hostname" : "cdh-srv4.c.safari-lab.internal",
    "rackId" : "/default",
    "hostUrl" : "http://cdh-srv2.c.safari-lab.internal:7180/cmf/hostRedirect/9b9c235f-dec5-4528-9d12-6dca96738f16",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 8,
    "numPhysicalCores" : 4,
    "totalPhysMemBytes" : 31688794112
  } ]
```
The command and output from the CM API call ../api/v8/clusters/<githubName>/services
```
# curl -u admin:admin 'http://localhost:7180/api/v8/clusters/andreswagner/services'
{
  "items" : [ {
    "name" : "hive",
    "type" : "HIVE",
    "clusterRef" : {
      "clusterName" : "cluster"
    },
    "serviceUrl" : "http://cdh-srv2.c.safari-lab.internal:7180/cmf/serviceRedirect/hive",
    "serviceState" : "STARTED",
    "healthSummary" : "GOOD",
    "healthChecks" : [ {
      "name" : "HIVE_HIVEMETASTORES_HEALTHY",
      "summary" : "GOOD"
    }, {
      "name" : "HIVE_HIVESERVER2S_HEALTHY",
      "summary" : "GOOD"
    } ],
    "configStalenessStatus" : "FRESH",
    "clientConfigStalenessStatus" : "FRESH",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "displayName" : "Hive"
  }, {
    "name" : "zookeeper",
    "type" : "ZOOKEEPER",
    "clusterRef" : {
      "clusterName" : "cluster"
    },
    "serviceUrl" : "http://cdh-srv2.c.safari-lab.internal:7180/cmf/serviceRedirect/zookeeper",
    "serviceState" : "STARTED",
    "healthSummary" : "GOOD",
    "healthChecks" : [ {
      "name" : "ZOOKEEPER_CANARY_HEALTH",
      "summary" : "GOOD"
    }, {
      "name" : "ZOOKEEPER_SERVERS_HEALTHY",
      "summary" : "GOOD"
    } ],
    "configStalenessStatus" : "FRESH",
    "clientConfigStalenessStatus" : "FRESH",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "displayName" : "ZooKeeper"
  }, {
    "name" : "hue",
    "type" : "HUE",
    "clusterRef" : {
      "clusterName" : "cluster"
    },
    "serviceUrl" : "http://cdh-srv2.c.safari-lab.internal:7180/cmf/serviceRedirect/hue",
    "serviceState" : "STARTED",
    "healthSummary" : "GOOD",
    "healthChecks" : [ {
      "name" : "HUE_HUE_SERVERS_HEALTHY",
      "summary" : "GOOD"
    } ],
    "configStalenessStatus" : "FRESH",
    "clientConfigStalenessStatus" : "FRESH",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "displayName" : "Hue"
  }, {
    "name" : "oozie",
    "type" : "OOZIE",
    "clusterRef" : {
      "clusterName" : "cluster"
    },
    "serviceUrl" : "http://cdh-srv2.c.safari-lab.internal:7180/cmf/serviceRedirect/oozie",
    "serviceState" : "STARTED",
    "healthSummary" : "GOOD",
    "healthChecks" : [ {
      "name" : "OOZIE_OOZIE_SERVERS_HEALTHY",
      "summary" : "GOOD"
    } ],
    "configStalenessStatus" : "FRESH",
    "clientConfigStalenessStatus" : "FRESH",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "displayName" : "Oozie"
  }, {
    "name" : "yarn",
    "type" : "YARN",
    "clusterRef" : {
      "clusterName" : "cluster"
    },
    "serviceUrl" : "http://cdh-srv2.c.safari-lab.internal:7180/cmf/serviceRedirect/yarn",
    "serviceState" : "STARTED",
    "healthSummary" : "GOOD",
    "healthChecks" : [ {
      "name" : "YARN_JOBHISTORY_HEALTH",
      "summary" : "GOOD"
    }, {
      "name" : "YARN_NODE_MANAGERS_HEALTHY",
      "summary" : "GOOD"
    }, {
      "name" : "YARN_RESOURCEMANAGERS_HEALTH",
      "summary" : "GOOD"
    }, {
      "name" : "YARN_USAGE_AGGREGATION_HEALTH",
      "summary" : "DISABLED"
    } ],
    "configStalenessStatus" : "FRESH",
    "clientConfigStalenessStatus" : "FRESH",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "displayName" : "YARN (MR2 Included)"
  }, {
    "name" : "spark_on_yarn",
    "type" : "SPARK_ON_YARN",
    "clusterRef" : {
      "clusterName" : "cluster"
    },
    "serviceUrl" : "http://cdh-srv2.c.safari-lab.internal:7180/cmf/serviceRedirect/spark_on_yarn",
    "serviceState" : "STARTED",
    "healthSummary" : "GOOD",
    "healthChecks" : [ ],
    "configStalenessStatus" : "FRESH",
    "clientConfigStalenessStatus" : "FRESH",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "displayName" : "Spark"
  }, {
    "name" : "hdfs",
    "type" : "HDFS",
    "clusterRef" : {
      "clusterName" : "cluster"
    },
    "serviceUrl" : "http://cdh-srv2.c.safari-lab.internal:7180/cmf/serviceRedirect/hdfs",
    "serviceState" : "STARTED",
    "healthSummary" : "GOOD",
    "healthChecks" : [ {
      "name" : "HDFS_BLOCKS_WITH_CORRUPT_REPLICAS",
      "summary" : "GOOD"
    }, {
      "name" : "HDFS_CANARY_HEALTH",
      "summary" : "GOOD"
    }, {
      "name" : "HDFS_DATA_NODES_HEALTHY",
      "summary" : "GOOD"
    }, {
      "name" : "HDFS_FREE_SPACE_REMAINING",
      "summary" : "GOOD"
    }, {
      "name" : "HDFS_HA_NAMENODE_HEALTH",
      "summary" : "GOOD"
    }, {
      "name" : "HDFS_MISSING_BLOCKS",
      "summary" : "GOOD"
    }, {
      "name" : "HDFS_UNDER_REPLICATED_BLOCKS",
      "summary" : "GOOD"
    } ],
    "configStalenessStatus" : "FRESH",
    "clientConfigStalenessStatus" : "FRESH",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "displayName" : "HDFS"
  } ]
}
```
