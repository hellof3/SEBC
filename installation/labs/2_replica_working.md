## 1. Install Mysql-server On Master And Slave Node
<pre><code>
wget https://repo.mysql.com//mysql57-community-release-el6-11.noarch.rpm
rpm -ivh mysql57-community-release-el6-11.noarch.rpm
yum install mysql-server
</code></pre>

## 2. Config /etc/my.cf
### Master node  
<pre><code>
[mysqld]
bind-address = 0.0.0.0
server-id = 1
log-error=/var/log/mysql/mysql.err
log-bin = /var/log/mysql/mysql-replication.log
</code></pre>
### Slave node  
<pre><code>
bind-address = 0.0.0.0
server-id = 2
log-error=/var/log/mysql/mysql.err
log-bin = /var/log/mysql/mysql-replication.log
</code></pre>

## 3. Mysql Secure Installation
<pre><code>
mysql_secure_installation

Securing the MySQL server deployment.
Enter password for user root: 
The existing password for the user account root has expired. Please set a new password.
New password: 
Re-enter new password: 
The 'validate_password' plugin is installed on the server.
The subsequent steps will run with the existing configuration
of the plugin.
Using existing password for root.

......
</code></pre>

## 4. Start Mysql  
<pre><code>
service mysqld start
chkconfg mysqld on 
</code></pre>

## 5. Download Mysql JDBC Driver
<pre><code>
wget https://dev.mysql.com/get/Downloads/Connector-J/mysql-connector-java-5.1.42.zip
unzip mysql-connector-java-5.1.42.zip
mkdir /usr/share/java
cp mysql-connector-java-5.1.42/mysql-connector-java-5.1.42-bin.jar /usr/share/java/mysql-connector-java.jar
</code></pre>

## 6. Set up Mysql Master/Slave Mode
### Master Node
<pre><code>
GRANT REPLICATION SLAVE ON *.* TO 'replica'@'ip-172-31-13-65.cn-north-1.compute.internal' IDENTIFIED BY 'replica'
SET GLOBAL binlog_format = 'ROW'
FLUSH TABLES WITH READ LOCK

mysql> show master status\G;
*************************** 1. row ***************************
             File: mysql-bin.000004
         Position: 2283
     Binlog_Do_DB: 
 Binlog_Ignore_DB: 
Executed_Gtid_Set: 
1 row in set (0.00 sec)
</code></pre>

### Slave Node
<pre><code>
CHANGE MASTER TO MASTER_HOST='ip-172-31-3-76.cn-north-1.compute.internal', MASTER_USER='replica', MASTER_PASSWORD='replica', MASTER_LOG_FILE='mysql-bin.000004', MASTER_LOG_POS=2283;
START SLAVE
show slave status\G
*************************** 1. row ***************************
               Slave_IO_State: Waiting for master to send event
                  Master_Host: ip-172-31-3-76.cn-north-1.compute.internal
                  Master_User: replica
                  Master_Port: 3306
                Connect_Retry: 60
              Master_Log_File: mysql-bin.000004
          Read_Master_Log_Pos: 2283
               Relay_Log_File: ip-172-31-13-65-relay-bin.000002
                Relay_Log_Pos: 1963
        Relay_Master_Log_File: mysql-bin.000004
             Slave_IO_Running: Yes
            Slave_SQL_Running: Yes
              Replicate_Do_DB: 
          Replicate_Ignore_DB: 
           Replicate_Do_Table: 
       Replicate_Ignore_Table: 
      Replicate_Wild_Do_Table: 
  Replicate_Wild_Ignore_Table: 
                   Last_Errno: 0
                   Last_Error: 
                 Skip_Counter: 0
          Exec_Master_Log_Pos: 2283
              Relay_Log_Space: 2180
              Until_Condition: None
               Until_Log_File: 
                Until_Log_Pos: 0
           Master_SSL_Allowed: No
           Master_SSL_CA_File: 
           Master_SSL_CA_Path: 
              Master_SSL_Cert: 
            Master_SSL_Cipher: 
               Master_SSL_Key: 
        Seconds_Behind_Master: 0
Master_SSL_Verify_Server_Cert: No
                Last_IO_Errno: 0
                Last_IO_Error: 
               Last_SQL_Errno: 0
               Last_SQL_Error: 
  Replicate_Ignore_Server_Ids: 
             Master_Server_Id: 1
                  Master_UUID: 60622a6c-34d5-11e7-a595-06b011a7c852
             Master_Info_File: /var/lib/mysql/master.info
                    SQL_Delay: 0
          SQL_Remaining_Delay: NULL
      Slave_SQL_Running_State: Slave has read all relay log; waiting for more updates
           Master_Retry_Count: 86400
                  Master_Bind: 
      Last_IO_Error_Timestamp: 
     Last_SQL_Error_Timestamp: 
               Master_SSL_Crl: 
           Master_SSL_Crlpath: 
           Retrieved_Gtid_Set: 
            Executed_Gtid_Set: 
                Auto_Position: 0
         Replicate_Rewrite_DB: 
                 Channel_Name: 
           Master_TLS_Version: 
</code></pre>
