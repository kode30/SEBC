```
$ sudo su - saturn

[saturn@cdh-srv2 ~]$ kinit saturn
Password for saturn@ANDRESWAGNER.HQ: 
[saturn@cdh-srv2 ~]$ hadoop jar /opt/cloudera/parcels/CDH/lib/hadoop-0.20-mapreduce/hadoop-examples.jar terasort /user/saturn/tgen /user/saturn/tsort
17/10/06 16:42:07 INFO terasort.TeraSort: starting
17/10/06 16:42:08 INFO hdfs.DFSClient: Created token for saturn: HDFS_DELEGATION_TOKEN owner=saturn@ANDRESWAGNER.HQ, renewer=yarn, realUser=, issueDate=1507308128755, maxDate=1507912928755, sequenceNumber=1, masterKeyId=2 on 10.128.0.5:8020
17/10/06 16:42:08 INFO security.TokenCache: Got dt for hdfs://cdh-srv1.c.safari-lab.internal:8020; Kind: HDFS_DELEGATION_TOKEN, Service: 10.128.0.5:8020, Ident: (token for saturn: HDFS_DELEGATION_TOKEN owner=saturn@ANDRESWAGNER.HQ, renewer=yarn, realUser=, issueDate=1507308128755, maxDate=1507912928755, sequenceNumber=1, masterKeyId=2)
17/10/06 16:42:09 INFO input.FileInputFormat: Total input paths to process : 1
Spent 422ms computing base-splits.
Spent 7ms computing TeraScheduler splits.
Computing input splits took 430ms
Sampling 10 splits of 313
Making 12 from 100000 sampled records
Computing parititions took 602ms
Spent 1035ms computing partitions.
17/10/06 16:42:09 INFO client.RMProxy: Connecting to ResourceManager at cdh-srv3.c.safari-lab.internal/10.128.0.7:8032
17/10/06 16:42:10 INFO mapreduce.JobSubmitter: number of splits:313
17/10/06 16:42:10 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1507307843362_0001
17/10/06 16:42:10 INFO mapreduce.JobSubmitter: Kind: HDFS_DELEGATION_TOKEN, Service: 10.128.0.5:8020, Ident: (token for saturn: HDFS_DELEGATION_TOKEN owner=saturn@ANDRESWAGNER.HQ, renewer=yarn, realUser=, issueDate=1507308128755, maxDate=1507912928755, sequenceNumber=1, masterKeyId=2)
17/10/06 16:42:11 INFO impl.YarnClientImpl: Submitted application application_1507307843362_0001
17/10/06 16:42:11 INFO mapreduce.Job: The url to track the job: http://cdh-srv3.c.safari-lab.internal:8088/proxy/application_1507307843362_0001/
17/10/06 16:42:11 INFO mapreduce.Job: Running job: job_1507307843362_0001
17/10/06 16:42:20 INFO mapreduce.Job: Job job_1507307843362_0001 running in uber mode : false
17/10/06 16:42:20 INFO mapreduce.Job:  map 0% reduce 0%
17/10/06 16:42:34 INFO mapreduce.Job:  map 2% reduce 0%
17/10/06 16:42:43 INFO mapreduce.Job:  map 7% reduce 0%
17/10/06 16:42:44 INFO mapreduce.Job:  map 8% reduce 0%
17/10/06 16:42:46 INFO mapreduce.Job:  map 9% reduce 0%
17/10/06 16:42:47 INFO mapreduce.Job:  map 10% reduce 0%
17/10/06 16:42:57 INFO mapreduce.Job:  map 12% reduce 0%
17/10/06 16:42:58 INFO mapreduce.Job:  map 17% reduce 0%
17/10/06 16:43:05 INFO mapreduce.Job:  map 18% reduce 0%
17/10/06 16:43:10 INFO mapreduce.Job:  map 19% reduce 0%
17/10/06 16:43:11 INFO mapreduce.Job:  map 21% reduce 0%
17/10/06 16:43:12 INFO mapreduce.Job:  map 23% reduce 0%
17/10/06 16:43:13 INFO mapreduce.Job:  map 24% reduce 0%
17/10/06 16:43:17 INFO mapreduce.Job:  map 25% reduce 0%
17/10/06 16:43:20 INFO mapreduce.Job:  map 26% reduce 0%
17/10/06 16:43:21 INFO mapreduce.Job:  map 27% reduce 0%
17/10/06 16:43:24 INFO mapreduce.Job:  map 28% reduce 0%
17/10/06 16:43:26 INFO mapreduce.Job:  map 31% reduce 0%
17/10/06 16:43:27 INFO mapreduce.Job:  map 32% reduce 0%
17/10/06 16:43:31 INFO mapreduce.Job:  map 33% reduce 0%
17/10/06 16:43:32 INFO mapreduce.Job:  map 34% reduce 0%
17/10/06 16:43:36 INFO mapreduce.Job:  map 35% reduce 0%
17/10/06 16:43:38 INFO mapreduce.Job:  map 36% reduce 0%
17/10/06 16:43:40 INFO mapreduce.Job:  map 38% reduce 0%
17/10/06 16:43:41 INFO mapreduce.Job:  map 40% reduce 0%
17/10/06 16:43:44 INFO mapreduce.Job:  map 41% reduce 0%
17/10/06 16:43:49 INFO mapreduce.Job:  map 42% reduce 0%
17/10/06 16:43:50 INFO mapreduce.Job:  map 43% reduce 0%
17/10/06 16:43:52 INFO mapreduce.Job:  map 44% reduce 0%
17/10/06 16:43:53 INFO mapreduce.Job:  map 45% reduce 0%
17/10/06 16:43:54 INFO mapreduce.Job:  map 48% reduce 0%
17/10/06 16:43:55 INFO mapreduce.Job:  map 49% reduce 0%
17/10/06 16:44:02 INFO mapreduce.Job:  map 50% reduce 0%
17/10/06 16:44:05 INFO mapreduce.Job:  map 51% reduce 0%
17/10/06 16:44:06 INFO mapreduce.Job:  map 53% reduce 0%
17/10/06 16:44:07 INFO mapreduce.Job:  map 54% reduce 0%
17/10/06 16:44:08 INFO mapreduce.Job:  map 56% reduce 0%
17/10/06 16:44:14 INFO mapreduce.Job:  map 57% reduce 0%
17/10/06 16:44:17 INFO mapreduce.Job:  map 58% reduce 0%
17/10/06 16:44:19 INFO mapreduce.Job:  map 59% reduce 0%
17/10/06 16:44:20 INFO mapreduce.Job:  map 60% reduce 0%
17/10/06 16:44:21 INFO mapreduce.Job:  map 62% reduce 0%
17/10/06 16:44:22 INFO mapreduce.Job:  map 63% reduce 0%
17/10/06 16:44:23 INFO mapreduce.Job:  map 64% reduce 0%
17/10/06 16:44:29 INFO mapreduce.Job:  map 65% reduce 0%
17/10/06 16:44:31 INFO mapreduce.Job:  map 66% reduce 0%
17/10/06 16:44:32 INFO mapreduce.Job:  map 67% reduce 0%
17/10/06 16:44:34 INFO mapreduce.Job:  map 68% reduce 0%
17/10/06 16:44:35 INFO mapreduce.Job:  map 70% reduce 0%
17/10/06 16:44:36 INFO mapreduce.Job:  map 71% reduce 0%
17/10/06 16:44:39 INFO mapreduce.Job:  map 72% reduce 0%
17/10/06 16:44:41 INFO mapreduce.Job:  map 73% reduce 0%
17/10/06 16:44:43 INFO mapreduce.Job:  map 74% reduce 0%
17/10/06 16:44:45 INFO mapreduce.Job:  map 75% reduce 0%
17/10/06 16:44:47 INFO mapreduce.Job:  map 76% reduce 0%
17/10/06 16:44:49 INFO mapreduce.Job:  map 78% reduce 0%
17/10/06 16:44:50 INFO mapreduce.Job:  map 79% reduce 0%
17/10/06 16:44:52 INFO mapreduce.Job:  map 80% reduce 0%
17/10/06 16:44:54 INFO mapreduce.Job:  map 81% reduce 0%
17/10/06 16:44:57 INFO mapreduce.Job:  map 82% reduce 0%
17/10/06 16:45:00 INFO mapreduce.Job:  map 83% reduce 0%
17/10/06 16:45:01 INFO mapreduce.Job:  map 84% reduce 0%
17/10/06 16:45:03 INFO mapreduce.Job:  map 86% reduce 0%
17/10/06 16:45:04 INFO mapreduce.Job:  map 87% reduce 0%
17/10/06 16:45:05 INFO mapreduce.Job:  map 88% reduce 0%
17/10/06 16:45:09 INFO mapreduce.Job:  map 88% reduce 2%
17/10/06 16:45:11 INFO mapreduce.Job:  map 89% reduce 2%
17/10/06 16:45:13 INFO mapreduce.Job:  map 89% reduce 3%
17/10/06 16:45:14 INFO mapreduce.Job:  map 89% reduce 10%
17/10/06 16:45:16 INFO mapreduce.Job:  map 89% reduce 13%
17/10/06 16:45:17 INFO mapreduce.Job:  map 90% reduce 14%
17/10/06 16:45:18 INFO mapreduce.Job:  map 90% reduce 18%
17/10/06 16:45:19 INFO mapreduce.Job:  map 91% reduce 21%
17/10/06 16:45:20 INFO mapreduce.Job:  map 91% reduce 24%
17/10/06 16:45:21 INFO mapreduce.Job:  map 92% reduce 24%
17/10/06 16:45:22 INFO mapreduce.Job:  map 92% reduce 25%
17/10/06 16:45:23 INFO mapreduce.Job:  map 92% reduce 26%
17/10/06 16:45:24 INFO mapreduce.Job:  map 92% reduce 27%
17/10/06 16:45:26 INFO mapreduce.Job:  map 94% reduce 28%
17/10/06 16:45:29 INFO mapreduce.Job:  map 94% reduce 29%
17/10/06 16:45:30 INFO mapreduce.Job:  map 95% reduce 29%
17/10/06 16:45:32 INFO mapreduce.Job:  map 96% reduce 29%
17/10/06 16:45:34 INFO mapreduce.Job:  map 97% reduce 29%
17/10/06 16:45:35 INFO mapreduce.Job:  map 98% reduce 30%
17/10/06 16:45:38 INFO mapreduce.Job:  map 99% reduce 30%
17/10/06 16:45:40 INFO mapreduce.Job:  map 100% reduce 30%
17/10/06 16:45:42 INFO mapreduce.Job:  map 100% reduce 40%
17/10/06 16:45:43 INFO mapreduce.Job:  map 100% reduce 43%
17/10/06 16:45:44 INFO mapreduce.Job:  map 100% reduce 60%
17/10/06 16:45:45 INFO mapreduce.Job:  map 100% reduce 65%
17/10/06 16:45:47 INFO mapreduce.Job:  map 100% reduce 68%
17/10/06 16:45:48 INFO mapreduce.Job:  map 100% reduce 71%
17/10/06 16:45:49 INFO mapreduce.Job:  map 100% reduce 72%
17/10/06 16:45:50 INFO mapreduce.Job:  map 100% reduce 75%
17/10/06 16:45:51 INFO mapreduce.Job:  map 100% reduce 81%
17/10/06 16:45:52 INFO mapreduce.Job:  map 100% reduce 82%
17/10/06 16:45:53 INFO mapreduce.Job:  map 100% reduce 85%
17/10/06 16:45:54 INFO mapreduce.Job:  map 100% reduce 89%
17/10/06 16:45:55 INFO mapreduce.Job:  map 100% reduce 90%
17/10/06 16:45:56 INFO mapreduce.Job:  map 100% reduce 93%
17/10/06 16:45:57 INFO mapreduce.Job:  map 100% reduce 95%
17/10/06 16:45:59 INFO mapreduce.Job:  map 100% reduce 96%
17/10/06 16:46:00 INFO mapreduce.Job:  map 100% reduce 98%
17/10/06 16:46:02 INFO mapreduce.Job:  map 100% reduce 100%
17/10/06 16:46:05 INFO mapreduce.Job: Job job_1507307843362_0001 completed successfully
17/10/06 16:46:06 INFO mapreduce.Job: Counters: 49
	File System Counters
		FILE: Number of bytes read=4468195913
		FILE: Number of bytes written=8884064687
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=10000042881
		HDFS: Number of bytes written=10000000000
		HDFS: Number of read operations=975
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=24
	Job Counters 
		Launched map tasks=313
		Launched reduce tasks=12
		Data-local map tasks=313
		Total time spent by all maps in occupied slots (ms)=3717434
		Total time spent by all reduces in occupied slots (ms)=655791
		Total time spent by all map tasks (ms)=3717434
		Total time spent by all reduce tasks (ms)=655791
		Total vcore-seconds taken by all map tasks=3717434
		Total vcore-seconds taken by all reduce tasks=655791
		Total megabyte-seconds taken by all map tasks=3806652416
		Total megabyte-seconds taken by all reduce tasks=671529984
	Map-Reduce Framework
		Map input records=100000000
		Map output records=100000000
		Map output bytes=10200000000
		Map output materialized bytes=4375040557
		Input split bytes=42881
		Combine input records=0
		Combine output records=0
		Reduce input groups=100000000
		Reduce shuffle bytes=4375040557
		Reduce input records=100000000
		Reduce output records=100000000
		Spilled Records=200000000
		Shuffled Maps =3756
		Failed Shuffles=0
		Merged Map outputs=3756
		GC time elapsed (ms)=46525
		CPU time spent (ms)=1742880
		Physical memory (bytes) snapshot=171297218560
		Virtual memory (bytes) snapshot=514007134208
		Total committed heap usage (bytes)=168394489856
	Shuffle Errors
		BAD_ID=0
		CONNECTION=0
		IO_ERROR=0
		WRONG_LENGTH=0
		WRONG_MAP=0
		WRONG_REDUCE=0
	File Input Format Counters 
		Bytes Read=10000000000
	File Output Format Counters 
		Bytes Written=10000000000
17/10/06 16:46:06 INFO terasort.TeraSort: done
```
