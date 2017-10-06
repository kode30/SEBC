The full teragen command and output
```
hadoop jar /opt/cloudera/parcels/CDH/lib/hadoop-0.20-mapreduce/hadoop-examples.jar teragen -Dmapreduce.job.maps=5 -Ddfs.block.size=32000000 100000000 /user/saturn/tgen
```

```
17/10/06 16:13:52 INFO Configuration.deprecation: session.id is deprecated. Instead, use dfs.metrics.session-id
17/10/06 16:13:52 INFO jvm.JvmMetrics: Initializing JVM Metrics with processName=JobTracker, sessionId=
17/10/06 16:13:52 INFO terasort.TeraSort: Generating 100000000 using 1
17/10/06 16:13:52 INFO mapreduce.JobSubmitter: number of splits:1
17/10/06 16:13:52 INFO Configuration.deprecation: dfs.block.size is deprecated. Instead, use dfs.blocksize
17/10/06 16:13:52 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_local214979226_0001
17/10/06 16:13:52 INFO mapreduce.Job: The url to track the job: http://localhost:8080/
17/10/06 16:13:52 INFO mapreduce.Job: Running job: job_local214979226_0001
17/10/06 16:13:52 INFO mapred.LocalJobRunner: OutputCommitter set in config null
17/10/06 16:13:52 INFO output.FileOutputCommitter: File Output Committer Algorithm version is 1
17/10/06 16:13:52 INFO mapred.LocalJobRunner: OutputCommitter is org.apache.hadoop.mapreduce.lib.output.FileOutputCommitter
17/10/06 16:13:52 INFO mapred.LocalJobRunner: Waiting for map tasks
17/10/06 16:13:52 INFO mapred.LocalJobRunner: Starting task: attempt_local214979226_0001_m_000000_0
17/10/06 16:13:53 INFO output.FileOutputCommitter: File Output Committer Algorithm version is 1
17/10/06 16:13:53 INFO mapred.Task:  Using ResourceCalculatorProcessTree : [ ]
17/10/06 16:13:53 INFO mapred.MapTask: Processing split: org.apache.hadoop.examples.terasort.TeraGen$RangeInputFormat$RangeInputSplit@3e7dcf00
17/10/06 16:13:53 INFO mapreduce.Job: Job job_local214979226_0001 running in uber mode : false
17/10/06 16:13:53 INFO mapreduce.Job:  map 0% reduce 0%
17/10/06 16:13:59 INFO mapred.LocalJobRunner: map > map
17/10/06 16:13:59 INFO mapreduce.Job:  map 6% reduce 0%
17/10/06 16:14:02 INFO mapred.LocalJobRunner: map > map
17/10/06 16:14:02 INFO mapreduce.Job:  map 10% reduce 0%
17/10/06 16:14:05 INFO mapred.LocalJobRunner: map > map
17/10/06 16:14:05 INFO mapreduce.Job:  map 13% reduce 0%
17/10/06 16:14:08 INFO mapred.LocalJobRunner: map > map
17/10/06 16:14:08 INFO mapreduce.Job:  map 17% reduce 0%
17/10/06 16:14:11 INFO mapred.LocalJobRunner: map > map
17/10/06 16:14:11 INFO mapreduce.Job:  map 20% reduce 0%
17/10/06 16:14:14 INFO mapred.LocalJobRunner: map > map
17/10/06 16:14:14 INFO mapreduce.Job:  map 24% reduce 0%
17/10/06 16:14:17 INFO mapred.LocalJobRunner: map > map
17/10/06 16:14:17 INFO mapreduce.Job:  map 27% reduce 0%
17/10/06 16:14:20 INFO mapred.LocalJobRunner: map > map
17/10/06 16:14:20 INFO mapreduce.Job:  map 31% reduce 0%
17/10/06 16:14:23 INFO mapred.LocalJobRunner: map > map
17/10/06 16:14:23 INFO mapreduce.Job:  map 34% reduce 0%
17/10/06 16:14:26 INFO mapred.LocalJobRunner: map > map
17/10/06 16:14:26 INFO mapreduce.Job:  map 38% reduce 0%
17/10/06 16:14:29 INFO mapred.LocalJobRunner: map > map
17/10/06 16:14:29 INFO mapreduce.Job:  map 41% reduce 0%
17/10/06 16:14:32 INFO mapred.LocalJobRunner: map > map
17/10/06 16:14:32 INFO mapreduce.Job:  map 44% reduce 0%
17/10/06 16:14:35 INFO mapred.LocalJobRunner: map > map
17/10/06 16:14:35 INFO mapreduce.Job:  map 48% reduce 0%
17/10/06 16:14:38 INFO mapred.LocalJobRunner: map > map
17/10/06 16:14:38 INFO mapreduce.Job:  map 51% reduce 0%
17/10/06 16:14:41 INFO mapred.LocalJobRunner: map > map
17/10/06 16:14:41 INFO mapreduce.Job:  map 54% reduce 0%
17/10/06 16:14:44 INFO mapred.LocalJobRunner: map > map
17/10/06 16:14:44 INFO mapreduce.Job:  map 58% reduce 0%
17/10/06 16:14:47 INFO mapred.LocalJobRunner: map > map
17/10/06 16:14:47 INFO mapreduce.Job:  map 61% reduce 0%
17/10/06 16:14:50 INFO mapred.LocalJobRunner: map > map
17/10/06 16:14:50 INFO mapreduce.Job:  map 65% reduce 0%
17/10/06 16:14:53 INFO mapred.LocalJobRunner: map > map
17/10/06 16:14:53 INFO mapreduce.Job:  map 68% reduce 0%
17/10/06 16:14:56 INFO mapred.LocalJobRunner: map > map
17/10/06 16:14:56 INFO mapreduce.Job:  map 71% reduce 0%
17/10/06 16:14:59 INFO mapred.LocalJobRunner: map > map
17/10/06 16:14:59 INFO mapreduce.Job:  map 75% reduce 0%
17/10/06 16:15:02 INFO mapred.LocalJobRunner: map > map
17/10/06 16:15:02 INFO mapreduce.Job:  map 78% reduce 0%
17/10/06 16:15:05 INFO mapred.LocalJobRunner: map > map
17/10/06 16:15:05 INFO mapreduce.Job:  map 81% reduce 0%
17/10/06 16:15:08 INFO mapred.LocalJobRunner: map > map
17/10/06 16:15:08 INFO mapreduce.Job:  map 85% reduce 0%
17/10/06 16:15:11 INFO mapred.LocalJobRunner: map > map
17/10/06 16:15:11 INFO mapreduce.Job:  map 88% reduce 0%
17/10/06 16:15:14 INFO mapred.LocalJobRunner: map > map
17/10/06 16:15:14 INFO mapreduce.Job:  map 92% reduce 0%
17/10/06 16:15:17 INFO mapred.LocalJobRunner: map > map
17/10/06 16:15:17 INFO mapreduce.Job:  map 95% reduce 0%
17/10/06 16:15:20 INFO mapred.LocalJobRunner: map > map
17/10/06 16:15:20 INFO mapreduce.Job:  map 99% reduce 0%
17/10/06 16:15:21 INFO mapred.LocalJobRunner: map > map
17/10/06 16:15:21 INFO mapred.Task: Task:attempt_local214979226_0001_m_000000_0 is done. And is in the process of committing
17/10/06 16:15:21 INFO mapred.LocalJobRunner: map > map
17/10/06 16:15:21 INFO mapred.Task: Task attempt_local214979226_0001_m_000000_0 is allowed to commit now
17/10/06 16:15:21 INFO output.FileOutputCommitter: Saved output of task 'attempt_local214979226_0001_m_000000_0' to hdfs://cdh-srv1.c.safari-lab.internal:8020/user/saturn/tgen/_temporary/0/task_local214979226_0001_m_000000
17/10/06 16:15:21 INFO mapred.LocalJobRunner: map
17/10/06 16:15:21 INFO mapred.Task: Task 'attempt_local214979226_0001_m_000000_0' done.
17/10/06 16:15:21 INFO mapred.LocalJobRunner: Finishing task: attempt_local214979226_0001_m_000000_0
17/10/06 16:15:21 INFO mapred.LocalJobRunner: map task executor complete.
17/10/06 16:15:21 INFO mapreduce.Job:  map 100% reduce 0%
17/10/06 16:15:21 INFO mapreduce.Job: Job job_local214979226_0001 completed successfully
17/10/06 16:15:21 INFO mapreduce.Job: Counters: 21
	File System Counters
		FILE: Number of bytes read=276333
		FILE: Number of bytes written=566859
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=0
		HDFS: Number of bytes written=10000000000
		HDFS: Number of read operations=4
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=3
	Map-Reduce Framework
		Map input records=100000000
		Map output records=100000000
		Input split bytes=83
		Spilled Records=0
		Failed Shuffles=0
		Merged Map outputs=0
		GC time elapsed (ms)=868
		Total committed heap usage (bytes)=233832448
	org.apache.hadoop.examples.terasort.TeraGen$Counters
		CHECKSUM=214760662691937609
	File Input Format Counters 
		Bytes Read=0
	File Output Format Counters 
		Bytes Written=10000000000
 ```
```
real	0m2.240s
user	0m3.036s
sys	0m0.195s
```

```
$ hdfs dfs -ls /user/saturn/tgen
Found 2 items
-rw-r--r--   3 saturn saturn           0 2017-10-06 16:15 /user/saturn/tgen/_SUCCESS
-rw-r--r--   3 saturn saturn 10000000000 2017-10-06 16:15 /user/saturn/tgen/part-m-00000
```
```
$ hadoop fsck -blocks /user/saturn
DEPRECATED: Use of this script to execute hdfs command is deprecated.
Instead use the hdfs command for it.

Connecting to namenode via http://cdh-srv1.c.safari-lab.internal:50070
FSCK started by saturn (auth:SIMPLE) from /10.128.0.5 for path /user/saturn at Fri Oct 06 16:17:31 UTC 2017
..Status: HEALTHY
 Total size:	10000000000 B
 Total dirs:	2
 Total files:	2
 Total symlinks:		0
 Total blocks (validated):	313 (avg. block size 31948881 B)
 Minimally replicated blocks:	313 (100.0 %)
 Over-replicated blocks:	0 (0.0 %)
 Under-replicated blocks:	0 (0.0 %)
 Mis-replicated blocks:		0 (0.0 %)
 Default replication factor:	3
 Average block replication:	3.0
 Corrupt blocks:		0
 Missing replicas:		0 (0.0 %)
 Number of data-nodes:		3
 Number of racks:		1
FSCK ended at Fri Oct 06 16:17:31 UTC 2017 in 12 milliseconds


The filesystem under path '/user/saturn' is HEALTHY
```
		Bytes Written=10000000000
