## 1. Add User hellof3
<pre><code>
useradd hellof3
sudo -u hdfs hadoop fs -mkdir /user/hellof3
sudo -u hdfs hadoop chown hellof3:hellof3 /user/hellof3
</code></pre>

## 2. Test HDFS Performance
### Generate 10GB file using Teragen
<pre><code>
su - hellof3

time hadoop jar /opt/cloudera/parcels/CDH/jars/hadoop-mapreduce-examples-2.6.0-cdh5.9.0.jar teragen -Dmapreduce.map.jobs=4 -D dfs.blocksize=32m 107374182 teragen
real    1m28.904s
user    0m5.135s
sys     0m0.253s
</code></pre>

### Terasort Test
<pre><code>
time hadoop jar /opt/cloudera/parcels/CDH/jars/hadoop-mapreduce-examples-2.6.0-cdh5.9.0.jar terasort teragen terasort
real    7m33.353s
user    0m9.062s
sys     0m0.358s
</code></pre>
