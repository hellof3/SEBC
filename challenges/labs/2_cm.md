## 1. Display repos
<pre><code>
cat cloudera-manager.repo
[cloudera-manager]
name = Cloudera Manager, Version 5.11.0
baseurl = https://archive.cloudera.com/cm5/redhat/6/x86_64/cm/5.11.0/
gpgkey = https://archive.cloudera.com/redhat/cdh/RPM-GPG-KEY-cloudera
gpgcheck = 1
</code></pre>

## 2. Config Mysql-server for CM
<pre><code>
/usr/share/cmf/schema/scm_prepare_database.sh mysql scm scm cloudera-scm -h ec2-54-223-247-81.cn-north-1.compute.amazonaws.com.cn

JAVA_HOME=/usr/java/jdk1.7.0_67-cloudera
Verifying that we can write to /etc/cloudera-scm-server
Creating SCM configuration file in /etc/cloudera-scm-server
Executing:  /usr/java/jdk1.7.0_67-cloudera/bin/java -cp /usr/share/java/mysql-connector-java.jar:/usr/share/java/oracle-connector-java.jar:/usr/share/cmf/schema/../lib/* com.cloudera.enterprise.dbutil.DbCommandExecutor /etc/cloudera-scm-server/db.properties com.cloudera.cmf.db.
2017-05-12 02:40:38,174 [main] INFO  com.cloudera.enterprise.dbutil.DbCommandExecutor  - Successfully connected to database.
All done, your SCM database is configured correctly!
</code></pre>