#hadoopQA_does_not_have_any_open_files
	layout: post
	title: ERROR does not have any open files
	date: 2015-12-26 13:53:36
	categories: hadoopqa
	tags: 
		 hadoop
		 hdfs
		 yarn

---

---
[ERROR]

---
	 [MainThread] WARN  org.apache.hadoop.security.UserGroupInformation  - PriviledgedActionException as:ads_db (auth:SIMPLE) cause:org.apache.hadoop.ipc.RemoteException(org.apache.hadoop.hdfs.server.namenode.LeaseExpiredException): No lease on /user/ads_db/oozie-oozi/0009835-151204024716154-oozie-oozi-W/orion_report_new--pig/output/_temporary/1/_temporary/attempt_1448953762828_116807_m_000000_0/part-00000 (inode 18580914): File does not exist. Holder DFSClient_attempt_1448953762828_116807_m_000000_0_-190684571_1 does not have any open files.
		        at org.apache.hadoop.hdfs.server.namenode.FSNamesystem.checkLease(FSNamesystem.java:3605)
		        at org.apache.hadoop.hdfs.server.namenode.FSNamesystem.completeFileInternal(FSNamesystem.java:3693)
		        at org.apache.hadoop.hdfs.server.namenode.FSNamesystem.completeFile(FSNamesystem.java:3663)
		        at org.apache.hadoop.hdfs.server.namenode.NameNodeRpcServer.complete(NameNodeRpcServer.java:730)
		        at org.apache.hadoop.hdfs.server.namenode.AuthorizationProviderProxyClientProtocol.complete(AuthorizationProviderProxyClientProtocol.java:243)
		        at org.apache.hadoop.hdfs.protocolPB.ClientNamenodeProtocolServerSideTranslatorPB.complete(ClientNamenodeProtocolServerSideTranslatorPB.java:527)
		        at org.apache.hadoop.hdfs.protocol.proto.ClientNamenodeProtocolProtos$ClientNamenodeProtocol$2.callBlockingMethod(ClientNamenodeProtocolProtos.java)
		        at org.apache.hadoop.ipc.ProtobufRpcEngine$Server$ProtoBufRpcInvoker.call(ProtobufRpcEngine.java:619)
		        at org.apache.hadoop.ipc.RPC$Server.call(RPC.java:1060)
		        at org.apache.hadoop.ipc.Server$Handler$1.run(Server.java:2044)
		        at org.apache.hadoop.ipc.Server$Handler$1.run(Server.java:2040)
		        at java.security.AccessController.doPrivileged(Native Method)
		        at javax.security.auth.Subject.doAs(Subject.java:415)
		        at org.apache.hadoop.security.UserGroupInformation.doAs(UserGroupInformation.java:1671)
		     at org.apache.hadoop.ipc.Server$Handler.run(Server.java:2038)

---



[解决方案]

>Hadoop HDFS Datanode 有一个同时处理文件的上限默认为4096，x2 原则，修改为8192
``` text
	dfs_datanode_max_xcievers: 4096 为 dfs_datanode_max_xcievers: 8192
```