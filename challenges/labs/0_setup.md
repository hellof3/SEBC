## 1. Node Information
### Cloud
<pre><code>AWS China</code></pre>
### IP and DNS
<pre><code>
	172.31.0.138    ec2-54-223-247-81.cn-north-1.compute.amazonaws.com.cn
	172.31.14.154   ec2-54-222-221-106.cn-north-1.compute.amazonaws.com.cn
	172.31.11.202   ec2-54-222-140-140.cn-north-1.compute.amazonaws.com.cn
	172.31.0.194    ec2-52-80-36-91.cn-north-1.compute.amazonaws.com.cn
	172.31.12.17    ec2-52-80-13-78.cn-north-1.compute.amazonaws.com.cn
Linux:
</pre><code>
### uname -a
<pre><code>
Linux ip-172-31-0-138.cn-north-1.compute.internal 2.6.32-573.18.1.el6.x86_64 #1 SMP Tue Feb 9 22:46:17 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
</code></pre>
### fileSystem
<code><pre>
df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda1      7.8G  938M  6.5G  13% /
tmpfs           7.8G     0  7.8G   0% /dev/shm
/dev/xvda2      9.8G   23M  9.2G   1% /opt
/dev/xvdb1       20G   44M   19G   1% /disk1
</code></pre>
### repolist
<pre><code>
yum repolist enabled
repo id                        repo name                                  status
base                           CentOS-6 - Base                            6,706
extras                         CentOS-6 - Extras                             64
updates                        CentOS-6 - Updates                           270
repolist: 7,040
</code></pre>

## 2. Add Users And Groups
### add 
<pre><code>
useradd zhou -u 2800
useradd chen -u 2900
groupadd shanghai
groupadd beijing
usermod  -a -G shanghai chen
usermod  -a -G beijing zhou"
</code></pre>
### display
<pre><code>
passwd:
zhou:x:2800:2800::/home/zhou:/bin/bash
chen:x:2900:2900::/home/chen:/bin/bash

group:
shanghai:x:2901:chen
beijing:x:2902:zhou
</code></pre>