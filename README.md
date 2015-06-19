# SparkOnHBase
## Overview
This is a simple reusable lib for working with HBase with Spark


##Functionality
Current functionality supports the following functions

* bulkPut
* bulkDelete
* bulkIncrement
* bulkGet
* bulkCheckAndPut
* bulkCheckAndDelete
* foreachPartition (with HConnection)
* mapPartition (with HConnection)
* hbaseRDD (HBaseInputFormat)
* Java APIs
* Java Examples
* Java Unit Tests

##Near Future
* More unit test
* More Examples
* Python APIs
* Python Examples
* Python Unit Test

##Far Future

* Partitioned Bulk Put/Mutation
* Sorted Partitioned Bulk Get
* Spark implementation of HBase bulkLoad
* Spark implementation of HBase copyTable


##Build
mvn clean package [-P<version>]

By default the project will build against the dependencies for CDH 5.3.x. Available profiles are:

* cdh510
* cdh532
* cdh542

##CDH setup

### CDH 5.0.2

Testing was done on CDH 5.0.2

Just put hbase-protocol-*.jar in /opt/cloudera/parcels/CDH/lib/spark/assembly/lib/ and bounced

/opt/cloudera/parcels/CDH/lib/spark/assembly/lib

### CDH 5.3.x and above

Testing was performed on a standard cluster install.

##Examples

SparkOnHBase comes with a number of examples.  Here is the CLI commands to try them out.  These work with a table named 't1' and column family 'c'

```
create 't1', 'c'
```

Unless specified each of these works on both a secure and non-secure cluster.

###Bulk Put

```
spark-submit --class com.cloudera.spark.hbase.example.HBaseBulkPutExample --master yarn --deploy-mode client --executor-memory 512M --num-executors 4 --conf spark.executor.extraClassPath="/opt/cloudera/parcels/CDH/lib/hbase/lib/*" --driver-class-path "/opt/cloudera/parcels/CDH/lib/hbase/lib/*" SparkHBase.jar t1 c
```

###Bulk Put Timestamp

```
spark-submit --class com.cloudera.spark.hbase.example.HBaseBulkPutTimestampExample --master yarn --deploy-mode client --executor-memory 512M --num-executors 4 --conf spark.executor.extraClassPath="/opt/cloudera/parcels/CDH/lib/hbase/lib/*" --driver-class-path "/opt/cloudera/parcels/CDH/lib/hbase/lib/*" SparkHBase.jar t1 c
```

###Bulk Get

```
spark-submit --class com.cloudera.spark.hbase.example.HBaseBulkGetExample --master yarn --deploy-mode client --executor-memory 512M --num-executors 4 --conf spark.executor.extraClassPath="/opt/cloudera/parcels/CDH/lib/hbase/lib/*" --driver-class-path "/opt/cloudera/parcels/CDH/lib/hbase/lib/*" SparkHBase.jar t1 c
```

###Bulk Increment

```
spark-submit --class com.cloudera.spark.hbase.example.HBaseBulkIncrementExample --master yarn --deploy-mode client --executor-memory 512M --num-executors 4 --conf spark.executor.extraClassPath="/opt/cloudera/parcels/CDH/lib/hbase/lib/*" --driver-class-path "/opt/cloudera/parcels/CDH/lib/hbase/lib/*" SparkHBase.jar t1 c
```

###Bulk Delete

```
spark-submit --class com.cloudera.spark.hbase.example.HBaseBulkDeleteExample --master yarn --deploy-mode client --executor-memory 512M --num-executors 4 --conf spark.executor.extraClassPath="/opt/cloudera/parcels/CDH/lib/hbase/lib/*" --driver-class-path "/opt/cloudera/parcels/CDH/lib/hbase/lib/*" SparkHBase.jar t1 c
```

###Scan

```
spark-submit --class com.cloudera.spark.hbase.example.HBaseScanRDDExample --master yarn --deploy-mode client --executor-memory 512M --num-executors 4 --conf spark.executor.extraClassPath="/opt/cloudera/parcels/CDH/lib/hbase/lib/*" --driver-class-path "/opt/cloudera/parcels/CDH/lib/hbase/lib/*" SparkHBase.jar t1 c
```

###Old Scan that doesn't work on Kerberos

```
spark-submit --class com.cloudera.spark.hbase.example.HBaseDistributedScanExample --master yarn --deploy-mode client --executor-memory 512M --num-executors 4 --conf spark.executor.extraClassPath="/opt/cloudera/parcels/CDH/lib/hbase/lib/*" --driver-class-path "/opt/cloudera/parcels/CDH/lib/hbase/lib/*" SparkHBase.jar t1 c
```

sbt/sbt assembly 'test-only org.apache.spark.hbase*'


