## 1. List Mysql-Server Machine Name
<pre><code>
hostname
ip-172-31-0-138.cn-north-1.compute.internal
</code></pre>

## 2. Show Mysql Version
<pre><code>
mysql --version
mysql  Ver 14.14 Distrib 5.6.36, for Linux (x86_64) using  EditLine wrapper
</code></pre>

## 3. Create DataBase
### scm
<pre><code>
create database scm;
create user 'scm'@'localhost' identified by 'cloudera-scm';
create user 'scm'@'%' identified by 'cloudera-scm';
grant all privileges on scm.* to 'scm'@'localhost';
grant all privileges on scm.* to 'scm'@'%';
</code></pre>
### rman
<pre><code>
create database rman;
create user 'rman'@'localhost' identified by 'rman';
create user 'rman'@'%' identified by 'rman';
grant all privileges on rman.* to 'rman'@'localhost';
grant all privileges on rman.* to 'rman'@'%';
</code></pre>
### hive
<pre><code>
create database hive;
create user 'hive'@'localhost' identified by 'hive';
create user 'hive'@'%' identified by 'hive';
grant all privileges on hive.* to 'hive'@'localhost';
grant all privileges on hive.* to 'hive'@'%';
</code></pre>
### oozie
<pre><code>
create database oozie;
create user 'oozie'@'localhost' identified by 'oozie';
create user 'oozie'@'%' identified by 'oozie';
grant all privileges on oozie.* to 'oozie'@'localhost';
grant all privileges on oozie.* to 'oozie'@'%';
</code></pre>
### hue
<pre><code>
create database hue;
create user 'hue'@'localhost' identified by 'hue';
create user 'hue'@'%' identified by 'hue';
grant all privileges on hue.* to 'hue'@'localhost';
grant all privileges on hue.* to 'hue'@'%';
</code></pre>
### sentry
<pre><code>
create database sentry;
create user 'sentry'@'localhost' identified by 'sentry';
create user 'sentry'@'%' identified by 'sentry';
grant all privileges on sentry.* to 'sentry'@'localhost';
grant all privileges on sentry.* to 'sentry'@'%';
</code></pre>

## 4. Show DataBases
<pre><code>
show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| hive               |
| hue                |
| mysql              |
| oozie              |
| performance_schema |
| rman               |
| scm                |
| sentry             |
+--------------------+
</code></pre>