## 1. Create Root Dir
<pre><code>
sudo -u hdfs hadoop fs -mkdir /user/root
sudo -u hdfs hadoop fs -chown -R root:root /user/root
</code></pre>

## 2. Teragen Test
### Create A 500MB file
<pre><code>
hadoop jar /opt/cloudera/parcels/CDH/jars/hadoop-mapreduce-examples-2.6.0-cdh5.9.0.jar teragen 5000000 /user/root/hellof3

hadoop fs -du -s -h hellof3
476.8 M  1.4 G  hellof3
</code></pre>

## 3. Distcp Test
### Distcp To Local Dir
<pre><code>
hadoop distcp hellof3 hdfs://172.31.13.65/user/root/houjun
</code></pre>

### Validate
<code></pre>
hdfs fsck /user/root/houjun -files -blocks
#hdfs fsck /user/root/hellof3 -files -blocks
Connecting to namenode via http://ip-172-31-13-65.cn-north-1.compute.internal:50070
FSCK started by root (auth:SIMPLE) from /172.31.3.76 for path /user/root/houjun at Thu May 11 04:45:30 UTC 2017
/user/root/houjun <dir>
/user/root/houjun/_SUCCESS 0 bytes, 0 block(s):  OK

/user/root/houjun/part-m-00000 250000000 bytes, 2 block(s):  OK
0. BP-1579790194-172.31.13.65-1494473150281:blk_1073741924_1100 len=134217728 Live_repl=3
1. BP-1579790194-172.31.13.65-1494473150281:blk_1073741927_1103 len=115782272 Live_repl=3

/user/root/houjun/part-m-00001 250000000 bytes, 2 block(s):  OK
0. BP-1579790194-172.31.13.65-1494473150281:blk_1073741923_1099 len=134217728 Live_repl=3
1. BP-1579790194-172.31.13.65-1494473150281:blk_1073741926_1102 len=115782272 Live_repl=3

Status: HEALTHY
 Total size:    500000000 B
 Total dirs:    1
 Total files:   3
 Total symlinks:                0
 Total blocks (validated):      4 (avg. block size 125000000 B)
 Minimally replicated blocks:   4 (100.0 %)
 Over-replicated blocks:        0 (0.0 %)
 Under-replicated blocks:       0 (0.0 %)
 Mis-replicated blocks:         0 (0.0 %)
 Default replication factor:    3
 Average block replication:     3.0
 Corrupt blocks:                0
 Missing replicas:              0 (0.0 %)
 Number of data-nodes:          5
 Number of racks:               1
FSCK ended at Thu May 11 04:45:30 UTC 2017 in 3 milliseconds


The filesystem under path '/user/root/houjun' is HEALTHY
</code></pre>