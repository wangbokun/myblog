#hadoopQA_lzo
	layout: post
	title: ERROR lzo.GPLNativeCodeLoader Could not load native gpl library
	date: 2015-12-24 13:53:36
	categories: hadoopqa
	tags: 
		 hadoop
		 hdfs
		 yarn

---
ERROR lzo.GPLNativeCodeLoader: Could not load native gpl library
 
---
	-bash-4.1$ hadoop jar hadoop-examples.jar   wordcount  in  out
	Java HotSpot(TM) 64-Bit Server VM warning: ignoring option MaxPermSize=2048m; support was removed in 8.0
	15/12/26 15:25:06 INFO client.ConfiguredRMFailoverProxyProvider: Failing over to rm2.hadoop.cnn1.busdev.cmcm.com
	15/12/26 15:25:07 INFO input.FileInputFormat: Total input paths to process : 1
	15/12/26 15:25:07 ERROR lzo.GPLNativeCodeLoader: Could not load native gpl library
	java.lang.UnsatisfiedLinkError: no gplcompression in java.library.path
	    at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1865)
	    at java.lang.Runtime.loadLibrary0(Runtime.java:870)
	    at java.lang.System.loadLibrary(System.java:1122)
	    at com.hadoop.compression.lzo.GPLNativeCodeLoader.<clinit>(GPLNativeCodeLoader.java:32)
	    at com.hadoop.compression.lzo.LzoCodec.<clinit>(LzoCodec.java:71)
	    at java.lang.Class.forName0(Native Method)
	    at java.lang.Class.forName(Class.java:348)
	    at org.apache.hadoop.conf.Configuration.getClassByNameOrNull(Configuration.java:2138)
	    at org.apache.hadoop.conf.Configuration.getClassByName(Configuration.java:2103)
	    at org.apache.hadoop.io.compress.CompressionCodecFactory.getCodecClasses(CompressionCodecFactory.java:128)
	    at org.apache.hadoop.io.compress.CompressionCodecFactory.<init>(CompressionCodecFactory.java:175)
	    at org.apache.hadoop.mapreduce.lib.input.TextInputFormat.isSplitable(TextInputFormat.java:58)
	    at org.apache.hadoop.mapreduce.lib.input.FileInputFormat.getSplits(FileInputFormat.java:399)
	    at org.apache.hadoop.mapreduce.JobSubmitter.writeNewSplits(JobSubmitter.java:304)
	    at org.apache.hadoop.mapreduce.JobSubmitter.writeSplits(JobSubmitter.java:321)
	    at org.apache.hadoop.mapreduce.JobSubmitter.submitJobInternal(JobSubmitter.java:199)
	    at org.apache.hadoop.mapreduce.Job$10.run(Job.java:1307)
	    at org.apache.hadoop.mapreduce.Job$10.run(Job.java:1304)
	    at java.security.AccessController.doPrivileged(Native Method)
	    at javax.security.auth.Subject.doAs(Subject.java:422)
	    at org.apache.hadoop.security.UserGroupInformation.doAs(UserGroupInformation.java:1671)
	    at org.apache.hadoop.mapreduce.Job.submit(Job.java:1304)
	    at org.apache.hadoop.mapreduce.Job.waitForCompletion(Job.java:1325)
	    at org.apache.hadoop.examples.WordCount.main(WordCount.java:87)
	    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
	    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	    at java.lang.reflect.Method.invoke(Method.java:497)
	    at org.apache.hadoop.util.ProgramDriver$ProgramDescription.invoke(ProgramDriver.java:71)
	    at org.apache.hadoop.util.ProgramDriver.run(ProgramDriver.java:144)
	    at org.apache.hadoop.examples.ExampleDriver.main(ExampleDriver.java:74)
	    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
	    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	    at java.lang.reflect.Method.invoke(Method.java:497)
	    at org.apache.hadoop.util.RunJar.run(RunJar.java:221)
	    at org.apache.hadoop.util.RunJar.main(RunJar.java:136)
	15/12/26 15:25:07 ERROR lzo.LzoCodec: Cannot load native-lzo without native-hadoop

--



解决方案：

```bash
yum --enablerepo=cloudera-cdh5  install -y hadoop-lzo.x86_64 hadoop-lzo-native.x86_64
cp  -a /usr/lib/hadoop/lib/native/Linux-amd64-64/libgplcompression.so  /usr/lib/jvm/jre-1.7.0-openjdk.x86_64/lib/amd64/
cp  -a  /usr/lib/hadoop/lib/native/libhadoop.so  /usr/lib/jvm/jre-1.7.0-openjdk.x86_64/lib/amd64/
cp  -a  /usr/lib/hadoop/lib/native/libsnappy.so  /usr/lib/jvm/jre-1.7.0-openjdk.x86_64/lib/amd64/
cp  -a /usr/lib/hadoop/lib/native/Linux-amd64-64/libgplcompression.so.0.0.0  /usr/lib/jvm/jre-1.7.0-openjdk.x86_64/lib/amd64/
cp  -a  /usr/lib/hadoop/lib/native/libhadoop.so.1.0.0  /usr/lib/jvm/jre-1.7.0-openjdk.x86_64/lib/amd64/
cp  -a  /usr/lib/hadoop/lib/native/libsnappy.so.1.1.3  /usr/lib/jvm/jre-1.7.0-openjdk.x86_64/lib/amd64/
cp  -a  /usr/lib/hadoop/lib/native/Linux-amd64-64/libgplcompression.so.0.0.0  //usr/lib/hadoop/lib/native/libgplcompression.so
```
