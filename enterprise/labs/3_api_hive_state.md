Stop Hive service.
```
$ curl -X POST -u admin:admin 'http://localhost:7180/api/v1/clusters/andreswagner/services/hive/commands/stop'
{
  "id" : 1055,
  "name" : "Stop",
  "startTime" : "2017-10-05T15:17:09.898Z",
  "active" : true,
  "serviceRef" : {
    "clusterName" : "cluster",
    "serviceName" : "hive"
  }
```
Start Hive service.
```
$ curl -X POST -u admin:admin 'http://localhost:7180/api/v1/clusters/andreswagner/services/hive/commands/start'
{
  "id" : 1061,
  "name" : "Start",
  "startTime" : "2017-10-05T15:18:12.654Z",
  "active" : true,
  "serviceRef" : {
    "clusterName" : "cluster",
    "serviceName" : "hive"
  }
```
Check the current state of  Hive service
```
$ curl -u admin:admin 'http://localhost:7180/api/v1/clusters/andreswagner/services/hive'
{
  "name" : "hive",
  "type" : "HIVE",
  "clusterRef" : {
    "clusterName" : "cluster"
  },
  "serviceUrl" : "http://cdh-srv1.c.safari-lab.internal:7180/cmf/serviceRedirect/hive",
  "serviceState" : "STARTED",
  "healthSummary" : "GOOD",
  "healthChecks" : [ {
    "name" : "HIVE_HIVEMETASTORES_HEALTHY",
    "summary" : "GOOD"
  }, {
    "name" : "HIVE_HIVESERVER2S_HEALTHY",
    "summary" : "GOOD"
  } ],
  "configStale" : false
}

```
