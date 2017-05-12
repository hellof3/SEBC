## 1. List Dir
<pre><code>
hdfs dfs -ls /user
Found 4 items
drwxr-xr-x   - hdfs   supergroup          0 2017-05-12 04:23 /user/chen
drwxrwxrwx   - mapred hadoop              0 2017-05-12 04:23 /user/history
drwxrwxr-t   - hive   hive                0 2017-05-12 04:24 /user/hive
drwxr-xr-x   - chen   chen                0 2017-05-12 04:23 /user/zhou
</code></pre>

## CURL hosts
<pre><code>
curl -u admin:admin "http://172.31.14.154:7180/api/v14/hosts"
{
  "items" : [ {
    "hostId" : "ef12ed50-cc8f-4184-a215-4c616456f1c6",
    "ipAddress" : "172.31.12.17",
    "hostname" : "ec2-52-80-13-78.cn-north-1.compute.amazonaws.com.cn",
    "rackId" : "/default",
    "hostUrl" : "http://ec2-54-222-221-106.cn-north-1.compute.amazonaws.com.cn:7180/cmf/hostRedirect/ef12ed50-cc8f-4184-a215-4c616456f1c6",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 16722812928
  }, {
    "hostId" : "35ca44c2-127d-4887-8aa8-5f8f73fd78dd",
    "ipAddress" : "172.31.0.194",
    "hostname" : "ec2-52-80-36-91.cn-north-1.compute.amazonaws.com.cn",
    "rackId" : "/default",
    "hostUrl" : "http://ec2-54-222-221-106.cn-north-1.compute.amazonaws.com.cn:7180/cmf/hostRedirect/35ca44c2-127d-4887-8aa8-5f8f73fd78dd",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 16722812928
  }, {
    "hostId" : "6f7b999f-7421-4ef3-b88b-a14c09a4592a",
    "ipAddress" : "172.31.11.202",
    "hostname" : "ec2-54-222-140-140.cn-north-1.compute.amazonaws.com.cn",
    "rackId" : "/default",
    "hostUrl" : "http://ec2-54-222-221-106.cn-north-1.compute.amazonaws.com.cn:7180/cmf/hostRedirect/6f7b999f-7421-4ef3-b88b-a14c09a4592a",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 16722812928
  }, {
    "hostId" : "ca6af072-2d4c-448a-8516-2dea449029ee",
    "ipAddress" : "172.31.14.154",
    "hostname" : "ec2-54-222-221-106.cn-north-1.compute.amazonaws.com.cn",
    "rackId" : "/default",
    "hostUrl" : "http://ec2-54-222-221-106.cn-north-1.compute.amazonaws.com.cn:7180/cmf/hostRedirect/ca6af072-2d4c-448a-8516-2dea449029ee",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 16722812928
  }, {
    "hostId" : "13bde53a-7f4c-4f51-ae01-34d0824c9aa9",
    "ipAddress" : "172.31.0.138",
    "hostname" : "ec2-54-223-247-81.cn-north-1.compute.amazonaws.com.cn",
    "rackId" : "/default",
    "hostUrl" : "http://ec2-54-222-221-106.cn-north-1.compute.amazonaws.com.cn:7180/cmf/hostRedirect/13bde53a-7f4c-4f51-ae01-34d0824c9aa9",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 16722489344
  } ]
}
</code></pre>

## CRUL Services
<pre><code>
curl -u admin:admin "http://172.31.14.154:7180/api/v6/clusters/hellof3/services"
{
  "items" : [ {
    "name" : "hive",
    "type" : "HIVE",
    "clusterRef" : {
      "clusterName" : "cluster"
    },
    "serviceUrl" : "http://ec2-54-222-221-106.cn-north-1.compute.amazonaws.com.cn:7180/cmf/serviceRedirect/hive",
    "serviceState" : "STARTED",
    "healthSummary" : "BAD",
    "healthChecks" : [ {
      "name" : "HIVE_HIVEMETASTORES_HEALTHY",
      "summary" : "BAD"
    }, {
      "name" : "HIVE_HIVESERVER2S_HEALTHY",
      "summary" : "BAD"
    } ],
    "configStalenessStatus" : "FRESH",
    "clientConfigStalenessStatus" : "FRESH",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "displayName" : "Hive"
  }, {
    "name" : "zookeeper",
    "type" : "ZOOKEEPER",
    "clusterRef" : {
      "clusterName" : "cluster"
    },
    "serviceUrl" : "http://ec2-54-222-221-106.cn-north-1.compute.amazonaws.com.cn:7180/cmf/serviceRedirect/zookeeper",
    "serviceState" : "STARTED",
    "healthSummary" : "BAD",
    "healthChecks" : [ {
      "name" : "ZOOKEEPER_CANARY_HEALTH",
      "summary" : "GOOD"
    }, {
      "name" : "ZOOKEEPER_SERVERS_HEALTHY",
      "summary" : "BAD"
    } ],
    "configStalenessStatus" : "FRESH",
    "clientConfigStalenessStatus" : "FRESH",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "displayName" : "ZooKeeper"
  }, {
    "name" : "hue",
    "type" : "HUE",
    "clusterRef" : {
      "clusterName" : "cluster"
    },
    "serviceUrl" : "http://ec2-54-222-221-106.cn-north-1.compute.amazonaws.com.cn:7180/cmf/serviceRedirect/hue",
    "serviceState" : "STARTED",
    "healthSummary" : "BAD",
    "healthChecks" : [ {
      "name" : "HUE_HUE_SERVERS_HEALTHY",
      "summary" : "BAD"
    } ],
    "configStalenessStatus" : "FRESH",
    "clientConfigStalenessStatus" : "FRESH",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "displayName" : "Hue"
  }, {
    "name" : "oozie",
    "type" : "OOZIE",
    "clusterRef" : {
      "clusterName" : "cluster"
    },
    "serviceUrl" : "http://ec2-54-222-221-106.cn-north-1.compute.amazonaws.com.cn:7180/cmf/serviceRedirect/oozie",
    "serviceState" : "STARTED",
    "healthSummary" : "BAD",
    "healthChecks" : [ {
      "name" : "OOZIE_OOZIE_SERVERS_HEALTHY",
      "summary" : "BAD"
    } ],
    "configStalenessStatus" : "FRESH",
    "clientConfigStalenessStatus" : "FRESH",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "displayName" : "Oozie"
  }, {
    "name" : "impala",
    "type" : "IMPALA",
    "clusterRef" : {
      "clusterName" : "cluster"
    },
    "serviceUrl" : "http://ec2-54-222-221-106.cn-north-1.compute.amazonaws.com.cn:7180/cmf/serviceRedirect/impala",
    "serviceState" : "STARTED",
    "healthSummary" : "BAD",
    "healthChecks" : [ {
      "name" : "IMPALA_ASSIGNMENT_LOCALITY",
      "summary" : "DISABLED"
    }, {
      "name" : "IMPALA_CATALOGSERVER_HEALTH",
      "summary" : "BAD"
    }, {
      "name" : "IMPALA_IMPALADS_HEALTHY",
      "summary" : "BAD"
    }, {
      "name" : "IMPALA_STATESTORE_HEALTH",
      "summary" : "BAD"
    } ],
    "configStalenessStatus" : "FRESH",
    "clientConfigStalenessStatus" : "FRESH",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "displayName" : "Impala"
  }, {
    "name" : "yarn",
    "type" : "YARN",
    "clusterRef" : {
      "clusterName" : "cluster"
    },
    "serviceUrl" : "http://ec2-54-222-221-106.cn-north-1.compute.amazonaws.com.cn:7180/cmf/serviceRedirect/yarn",
    "serviceState" : "STARTED",
    "healthSummary" : "BAD",
    "healthChecks" : [ {
      "name" : "YARN_JOBHISTORY_HEALTH",
      "summary" : "BAD"
    }, {
      "name" : "YARN_NODE_MANAGERS_HEALTHY",
      "summary" : "BAD"
    }, {
      "name" : "YARN_RESOURCEMANAGERS_HEALTH",
      "summary" : "BAD"
    }, {
      "name" : "YARN_USAGE_AGGREGATION_HEALTH",
      "summary" : "DISABLED"
    } ],
    "configStalenessStatus" : "FRESH",
    "clientConfigStalenessStatus" : "FRESH",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "displayName" : "YARN (MR2 Included)"
  }, {
    "name" : "hdfs",
    "type" : "HDFS",
    "clusterRef" : {
      "clusterName" : "cluster"
    },
    "serviceUrl" : "http://ec2-54-222-221-106.cn-north-1.compute.amazonaws.com.cn:7180/cmf/serviceRedirect/hdfs",
    "serviceState" : "STARTED",
    "healthSummary" : "BAD",
    "healthChecks" : [ {
      "name" : "HDFS_BLOCKS_WITH_CORRUPT_REPLICAS",
      "summary" : "GOOD"
    }, {
      "name" : "HDFS_CANARY_HEALTH",
      "summary" : "GOOD"
    }, {
      "name" : "HDFS_DATA_NODES_HEALTHY",
      "summary" : "BAD"
    }, {
      "name" : "HDFS_FREE_SPACE_REMAINING",
      "summary" : "GOOD"
    }, {
      "name" : "HDFS_HA_NAMENODE_HEALTH",
      "summary" : "BAD"
    }, {
      "name" : "HDFS_MISSING_BLOCKS",
      "summary" : "GOOD"
    }, {
      "name" : "HDFS_UNDER_REPLICATED_BLOCKS",
      "summary" : "GOOD"
    } ],
    "configStalenessStatus" : "FRESH",
    "clientConfigStalenessStatus" : "FRESH",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "displayName" : "HDFS"
  } ]
}[
</code></pre>