##1. Conifg Hosts
<code>
cat /etc/hosts
172.31.3.76     ip-172-31-3-76.cn-north-1.compute.internal hadoop1
172.31.13.65    ip-172-31-13-65.cn-north-1.compute.internal hadoop2
172.31.4.106    ip-172-31-4-106.cn-north-1.compute.internal hadoop3
172.31.10.116   ip-172-31-10-116.cn-north-1.compute.internal hadoop4
172.31.12.27    ip-172-31-12-27.cn-north-1.compute.interna hadoop5
</code>

##2. Close Iptables
<code>
for i in {1..5};do ssh hadoop$i "service iptables stop";done
</code>

##3. Check And Config Swappiness
### check
<code>
cat /proc/sys/vm/swappiness
60
</code>

<code>
### config
for i in {1..5};do ssh hadoop$i "echo vm.swappiness=1 >> /etc/sysctl.conf; \
  sysctl -p";done
</code>

##4. Disable Transparent Hugepage
<code>
for i in {1..5};do ssh hadoop$i "echo never > /sys/kernel/mm/redhat_transparent_hugepage/defrag";done
</code>

##5. Mount Attributes
<code>
mount -l
/dev/xvda1 on / type ext4 (rw)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw,rootcontext="system_u:object_r:tmpfs_t:s0")
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
</code>

##6. Allocated Space
<code>
df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda1      7.8G  4.1G  3.4G  55% /
tmpfs           7.8G     0  7.8G   0% /dev/shm
</code>

##7. Network Interface
<code>
ifconfig
eth0      Link encap:Ethernet  HWaddr 06:B0:11:A7:C8:52  
          inet addr:172.31.3.76  Bcast:172.31.15.255  Mask:255.255.240.0
          inet6 addr: fe80::4b0:11ff:fea7:c852/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:9001  Metric:1
          RX packets:1828457 errors:0 dropped:0 overruns:0 frame:0
          TX packets:804130 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2656134286 (2.4 GiB)  TX bytes:66799877 (63.7 MiB)
          Interrupt:145 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:882 errors:0 dropped:0 overruns:0 frame:0
          TX packets:882 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:140912 (137.6 KiB)  TX bytes:140912 (137.6 KiB)
</code>

##8. DNS Check
<code>
getent hosts
127.0.0.1       localhost localhost.localdomain localhost4 localhost4.localdomain4
127.0.0.1       localhost localhost.localdomain localhost6 localhost6.localdomain6
172.31.3.76     ip-172-31-3-76.cn-north-1.compute.internal hadoop1
172.31.13.65    ip-172-31-13-65.cn-north-1.compute.internal hadoop2
172.31.4.106    ip-172-31-4-106.cn-north-1.compute.internal hadoop3
172.31.10.116   ip-172-31-10-116.cn-north-1.compute.internal hadoop4
172.31.12.27    ip-172-31-12-27.cn-north-1.compute.interna hadoop5
</code>

<code>
getent hosts
127.0.0.1       localhost localhost.localdomain localhost4 localhost4.localdomain4
127.0.0.1       localhost localhost.localdomain localhost6 localhost6.localdomain6
172.31.3.76     ip-172-31-3-76.cn-north-1.compute.internal hadoop1
172.31.13.65    ip-172-31-13-65.cn-north-1.compute.internal hadoop2
172.31.4.106    ip-172-31-4-106.cn-north-1.compute.internal hadoop3
172.31.10.116   ip-172-31-10-116.cn-north-1.compute.internal hadoop4
172.31.12.27    ip-172-31-12-27.cn-north-1.compute.interna hadoop5
</code>

##9. Install and check ntpd,nscd
### install 
<code>
for i in {1..5}
do
  ssh hadoop$i "
	yum install -y ntp nscd; \
	service ntpd start; \
	service nscd start; \
	chkconfig ntpd on; \
	chkconfig nscd on;"
done
</code>
### check
<code>
service ntpd status
ntpd (pid  7039) is running...
service nscd status
nscd (pid 7057) is running...
</code>
