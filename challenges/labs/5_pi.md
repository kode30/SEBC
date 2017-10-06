```
# sudo su - haley
[haley@cdh-srv2 ~]$ kinit haley
Password for haley@ANDRESWAGNER.HQ: 
[haley@cdh-srv2 ~]$ hadoop jar /opt/cloudera/parcels/CDH/lib/hadoop-mapreduce/hadoop-mapreduce-examples.jar pi 10 100
Number of Maps  = 10
Samples per Map = 100
Wrote input for Map #0
Wrote input for Map #1
Wrote input for Map #2
Wrote input for Map #3
Wrote input for Map #4
Wrote input for Map #5
Wrote input for Map #6
Wrote input for Map #7
Wrote input for Map #8
Wrote input for Map #9
Starting Job
17/10/06 16:48:24 INFO client.RMProxy: Connecting to ResourceManager at cdh-srv3.c.safari-lab.internal/10.128.0.7:8032
17/10/06 16:48:24 INFO hdfs.DFSClient: Created token for haley: HDFS_DELEGATION_TOKEN owner=haley@ANDRESWAGNER.HQ, renewer=yarn, realUser=, issueDate=1507308504215, maxDate=1507913304215, sequenceNumber=3, masterKeyId=2 on 10.128.0.5:8020
17/10/06 16:48:24 INFO security.TokenCache: Got dt for hdfs://cdh-srv1.c.safari-lab.internal:8020; Kind: HDFS_DELEGATION_TOKEN, Service: 10.128.0.5:8020, Ident: (token for haley: HDFS_DELEGATION_TOKEN owner=haley@ANDRESWAGNER.HQ, renewer=yarn, realUser=, issueDate=1507308504215, maxDate=1507913304215, sequenceNumber=3, masterKeyId=2)
17/10/06 16:48:24 INFO input.FileInputFormat: Total input paths to process : 10
17/10/06 16:48:24 INFO mapreduce.JobSubmitter: number of splits:10
17/10/06 16:48:25 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1507307843362_0003
17/10/06 16:48:25 INFO mapreduce.JobSubmitter: Kind: HDFS_DELEGATION_TOKEN, Service: 10.128.0.5:8020, Ident: (token for haley: HDFS_DELEGATION_TOKEN owner=haley@ANDRESWAGNER.HQ, renewer=yarn, realUser=, issueDate=1507308504215, maxDate=1507913304215, sequenceNumber=3, masterKeyId=2)
17/10/06 16:48:25 INFO impl.YarnClientImpl: Submitted application application_1507307843362_0003
17/10/06 16:48:25 INFO mapreduce.Job: The url to track the job: http://cdh-srv3.c.safari-lab.internal:8088/proxy/application_1507307843362_0003/
17/10/06 16:48:25 INFO mapreduce.Job: Running job: job_1507307843362_0003
17/10/06 16:48:33 INFO mapreduce.Job: Job job_1507307843362_0003 running in uber mode : false
17/10/06 16:48:33 INFO mapreduce.Job:  map 0% reduce 0%
17/10/06 16:48:44 INFO mapreduce.Job:  map 80% reduce 0%
17/10/06 16:48:45 INFO mapreduce.Job:  map 100% reduce 0%
17/10/06 16:48:51 INFO mapreduce.Job:  map 100% reduce 100%
17/10/06 16:48:51 INFO mapreduce.Job: Job job_1507307843362_0003 completed successfully
17/10/06 16:48:52 INFO mapreduce.Job: Counters: 49
	File System Counters
		FILE: Number of bytes read=98
		FILE: Number of bytes written=1372743
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=2860
		HDFS: Number of bytes written=215
		HDFS: Number of read operations=43
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=3
	Job Counters 
		Launched map tasks=10
		Launched reduce tasks=1
		Data-local map tasks=10
		Total time spent by all maps in occupied slots (ms)=98585
		Total time spent by all reduces in occupied slots (ms)=3262
		Total time spent by all map tasks (ms)=98585
		Total time spent by all reduce tasks (ms)=3262
		Total vcore-seconds taken by all map tasks=98585
		Total vcore-seconds taken by all reduce tasks=3262
		Total megabyte-seconds taken by all map tasks=100951040
		Total megabyte-seconds taken by all reduce tasks=3340288
	Map-Reduce Framework
		Map input records=10
		Map output records=20
		Map output bytes=180
		Map output materialized bytes=340
		Input split bytes=1680
		Combine input records=0
		Combine output records=0
		Reduce input groups=2
		Reduce shuffle bytes=340
		Reduce input records=20
		Reduce output records=0
		Spilled Records=40
		Shuffled Maps =10
		Failed Shuffles=0
		Merged Map outputs=10
		GC time elapsed (ms)=391
		CPU time spent (ms)=8680
		Physical memory (bytes) snapshot=5186441216
		Virtual memory (bytes) snapshot=17415430144
		Total committed heap usage (bytes)=5219287040
	Shuffle Errors
		BAD_ID=0
		CONNECTION=0
		IO_ERROR=0
		WRONG_LENGTH=0
		WRONG_MAP=0
		WRONG_REDUCE=0
	File Input Format Counters 
		Bytes Read=1180
	File Output Format Counters 
		Bytes Written=97
Job Finished in 28.11 seconds
Estimated value of Pi is 3.14800000000000000000

```
