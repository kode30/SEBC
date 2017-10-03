HDFS Lab: Test HDFS throughput

Create an end-user Linux account named with your GitHub handle
Make sure this Linux account is added to all cluster nodes

Create an HDFS directory under /user
$ hdfs dfs -ls /
Found 2 items
drwxrwxrwt   - hdfs supergroup          0 2017-10-03 15:55 /tmp
drwxr-xr-x   - hdfs supergroup          0 2017-10-03 15:55 /user

$ hdfs dfs -ls /user/
Found 6 items
drwxr-xr-x   - admin  admin               0 2017-10-03 15:55 /user/admin
drwxr-xr-x   - hdfs   supergroup          0 2017-10-03 15:55 /user/hdfs
drwxrwxrwx   - mapred hadoop              0 2017-10-03 14:15 /user/history
drwxrwxr-t   - hive   hive                0 2017-10-03 14:15 /user/hive
drwxrwxr-x   - hue    hue                 0 2017-10-03 14:16 /user/hue
drwxrwxr-x   - oozie  oozie               0 2017-10-03 14:16 /user/oozie

$ sudo su - hdfs
$ hdfs dfs -mkdir /user/andreswagner
$ hdfs dfs -chown andreswagner:andreswagner /user/andreswagner
$ exit
$ hdfs dfs -ls /user/

Found 7 items
drwxr-xr-x   - admin        admin                 0 2017-10-03 15:55 /user/admin
drwxr-xr-x   - andreswagner andreswagner          0 2017-10-03 16:48 /user/andreswagner
drwxr-xr-x   - hdfs         supergroup            0 2017-10-03 15:55 /user/hdfs
drwxrwxrwx   - mapred       hadoop                0 2017-10-03 14:15 /user/history
drwxrwxr-t   - hive         hive                  0 2017-10-03 14:15 /user/hive
drwxrwxr-x   - hue          hue                   0 2017-10-03 14:16 /user/hue
drwxrwxr-x   - oozie        oozie                 0 2017-10-03 14:16 /user/oozie

Create a 10 GB file using teragen
Set the number of mappers to four
Limit the block size to 32 MB
Land the output in your user's home directory
Use the time command to report the job's duration

Teragen
Command line

./hadoop jar ../hadoop-examples-1.2.1.jar teragen \
    -Ddfs.block.size=536870912 \
    -Dmapred.map.tasks=32 \
    -Dmapred.reduce.tasks=16 \
    -Dmapred.map.tasks.speculative.execution=true \
    -Dmapred.compress.map.output=true \
    1000000 \
    /Workloads/teragen.data


parameters

dfs.block.size=536870912	The size of blocks in Hadoop (here 512MB)
mapred.map.tasks=32	The number of map tasks per job (size of mapper, each one will generate 512MB)
mapred.reduce.tasks=16	The number of reduce tasks per job
mapred.map.tasks.speculative.execution=true	Multiple instances of some map tasks may be executed in parallel
mapred.compress.map.output=true	Should the outputs of the maps be compressed before being sent across the network (uses SequenceFile compression)
1000000	Size of generated files in 100-byte chuncks
/Workloads/teragen.data	Path of file to write

$ hadoop jar /opt/cloudera/parcels/CDH/lib/hadoop-0.20-mapreduce/hadoop-examples.jar teragen -Dmapreduce.job.maps=5 -Ddfs.block.size=32000000 100000000 /user/andreswagner/teraInput2


Terasort
Command line

./hadoop jar ../hadoop-examples-1.2.1.jar terasort \
    -Ddfs.block.size=536870912 \
    -Dio.file.buffer.size=32768 \
    -Dmapred.map.tasks=32 \
    -Dmapred.reduce.tasks=16 \
    -Dio.sort.factor=48 \
    -Dio.sort.record.percent=0.138 \
    /Workloads/teragen.data \
    /Workloads/terasort.data
parameters

dfs.block.size=536870912	The size of blocks in Hadoop (here 512MB)
mapred.map.tasks=32	The number of map tasks per job (size of mapper, each one will generate 512MB)
mapred.reduce.tasks=16	The number of reduce tasks per job
io.file.buffer.size=32768	The size of buffer for use in sequence files; it determines how much data is buffered during read and write operations
io.sort.factor=48	The number of streams to merge at once while sorting files; this determines the number of open file handles
io.sort.record.percent=0.138	The percentage of io.sort.mb dedicated to tracking record boundaries
1000000	Size of generated file multiplied in 100-byte chuncks
/Workloads/teragen.data	Path of file to read
/Workloads/terasort.data	Path of file to write


$ test hadoop jar /opt/cloudera/parcels/CDH/lib/hadoop-0.20-mapreduce/hadoop-examples.jar terasort /user/andreswagner/teraInput3 /user/andreswagner/teraOutput3

INFO terasort.TeraSort: done

real	4m38.259s
user	0m7.850s
sys	0m0.454s

links de interés: 
* http://blobseer.gforge.inria.fr/doku.php?id=tutorial:terabenchmark
* http://www.nagazuka.nl/2013/06/running-hadoop-examples-on-cloudera.html
* https://discuss.pivotal.io/hc/en-us/articles/200927666-Running-TeraSort-MapReduce-Benchmark

