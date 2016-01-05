#hadoopQA_IS_SECURITY_ENABLED
	layout: post
	title: ERROR java.lang.NoSuchFieldError IS SECURITY ENABLED
	date: 2015-12-29 19:53:36
	categories: hadoopqa
	tags: 
		 hadoop
		 hdfs
		 yarn



----

>  java  lang  NoSuchFieldError  IS  SECURITY  ENABLED

---
	
	2015-12-29 07:34:44,195 INFO [main] org.apache.hadoop.mapreduce.v2.app.client.MRClientService: Instantiated MRClientService at dn39.hadoop.busdev.usw2.cmcm.com/10.2.2.210:15491
	2015-12-29 07:34:44,254 INFO [main] org.mortbay.log: Logging to org.slf4j.impl.Log4jLoggerAdapter(org.mortbay.log) via org.mortbay.log.Slf4jLog
	2015-12-29 07:34:44,256 INFO [main] org.apache.hadoop.http.HttpRequestLog: Http request log for http.requests.mapreduce is not defined
	2015-12-29 07:34:44,265 INFO [main] org.apache.hadoop.http.HttpServer2: Added global filter 'safety' (class=org.apache.hadoop.http.HttpServer2$QuotingInputFilter)
	2015-12-29 07:34:44,268 INFO [main] org.apache.hadoop.http.HttpServer2: Added filter AM_PROXY_FILTER (class=org.apache.hadoop.yarn.server.webproxy.amfilter.AmIpFilter) to context mapreduce
	2015-12-29 07:34:44,269 INFO [main] org.apache.hadoop.http.HttpServer2: Added filter AM_PROXY_FILTER (class=org.apache.hadoop.yarn.server.webproxy.amfilter.AmIpFilter) to context static
	2015-12-29 07:34:44,272 INFO [main] org.apache.hadoop.http.HttpServer2: adding path spec: /mapreduce/*
	2015-12-29 07:34:44,272 INFO [main] org.apache.hadoop.http.HttpServer2: adding path spec: /ws/*
	2015-12-29 07:34:44,282 INFO [main] org.apache.hadoop.http.HttpServer2: Jetty bound to port 3294
	2015-12-29 07:34:44,282 INFO [main] org.mortbay.log: jetty-6.1.26.cloudera.2
	2015-12-29 07:34:44,298 INFO [main] org.mortbay.log: Extract jar:file:/usr/lib/hadoop-yarn/hadoop-yarn-common-2.6.0-cdh5.4.8.jar!/webapps/mapreduce to /tmp/Jetty_0_0_0_0_3294_mapreduce____wbl4h1/webapp
	2015-12-29 07:34:44,541 WARN [main] org.mortbay.log: failed jsp: java.lang.NoSuchFieldError: IS_SECURITY_ENABLED
	2015-12-29 07:34:44,545 WARN [main] org.mortbay.log: failed org.mortbay.jetty.webapp.WebAppContext@75392d33{/,jar:file:/usr/lib/hadoop-yarn/hadoop-yarn-common-2.6.0-cdh5.4.8.jar!/webapps/mapreduce}: java.lang.NoSuchFieldError: IS_SECURITY_ENABLED
	2015-12-29 07:34:44,545 WARN [main] org.mortbay.log: failed ContextHandlerCollection@7cc6ab64: java.lang.NoSuchFieldError: IS_SECURITY_ENABLED
	2015-12-29 07:34:44,546 ERROR [main] org.mortbay.log: Error starting handlers
	java.lang.NoSuchFieldError: IS_SECURITY_ENABLED
		at org.apache.jasper.compiler.JspRuntimeContext.<init>(JspRuntimeContext.java:197)
		at org.apache.jasper.servlet.JspServlet.init(JspServlet.java:150)
		at org.mortbay.jetty.servlet.ServletHolder.initServlet(ServletHolder.java:440)
		at org.mortbay.jetty.servlet.ServletHolder.doStart(ServletHolder.java:263)
		at org.mortbay.component.AbstractLifeCycle.start(AbstractLifeCycle.java:50)
		at org.mortbay.jetty.servlet.ServletHandler.initialize(ServletHandler.java:736)
		at org.mortbay.jetty.servlet.Context.startContext(Context.java:140)
		at org.mortbay.jetty.webapp.WebAppContext.startContext(WebAppContext.java:1282)
		at org.mortbay.jetty.handler.ContextHandler.doStart(ContextHandler.java:518)
		at org.mortbay.jetty.webapp.WebAppContext.doStart(WebAppContext.java:499)
		at org.mortbay.component.AbstractLifeCycle.start(AbstractLifeCycle.java:50)
		at org.mortbay.jetty.handler.HandlerCollection.doStart(HandlerCollection.java:152)
		at org.mortbay.jetty.handler.ContextHandlerCollection.doStart(ContextHandlerCollection.java:156)
		at org.mortbay.component.AbstractLifeCycle.start(AbstractLifeCycle.java:50)
		at org.mortbay.jetty.handler.HandlerWrapper.doStart(HandlerWrapper.java:130)
		at org.mortbay.jetty.Server.doStart(Server.java:224)
		at org.mortbay.component.AbstractLifeCycle.start(AbstractLifeCycle.java:50)
		at org.apache.hadoop.http.HttpServer2.start(HttpServer2.java:829)
		at org.apache.hadoop.yarn.webapp.WebApps$Builder.start(WebApps.java:273)
		at org.apache.hadoop.mapreduce.v2.app.client.MRClientService.serviceStart(MRClientService.java:142)
		at org.apache.hadoop.service.AbstractService.start(AbstractService.java:193)
		at org.apache.hadoop.mapreduce.v2.app.MRAppMaster.serviceStart(MRAppMaster.java:1084)
		at org.apache.hadoop.service.AbstractService.start(AbstractService.java:193)
		at org.apache.hadoop.mapreduce.v2.app.MRAppMaster$4.run(MRAppMaster.java:1500)
		at java.security.AccessController.doPrivileged(Native Method)
		at javax.security.auth.Subject.doAs(Subject.java:415)
		at org.apache.hadoop.security.UserGroupInformation.doAs(UserGroupInformation.java:1671)
		at org.apache.hadoop.mapreduce.v2.app.MRAppMaster.initAndStartAppMaster(MRAppMaster.java:1496)
		at org.apache.hadoop.mapreduce.v2.app.MRAppMaster.main(MRAppMaster.java:1429)
	2015-12-29 07:34:44,550 INFO [main] org.mortbay.log: Started HttpServer2$SelectChannelConnectorWithSafeStartup@0.0.0.0:3294
	2015-12-29 07:34:44,550 ERROR [main] org.apache.hadoop.mapreduce.v2.app.client.MRClientService: Webapps failed to start. Ignoring for now:
	org.apache.hadoop.yarn.webapp.WebAppException: Error starting http server
		at org.apache.hadoop.yarn.webapp.WebApps$Builder.start(WebApps.java:278)
		at org.apache.hadoop.mapreduce.v2.app.client.MRClientService.serviceStart(MRClientService.java:142)
		at org.apache.hadoop.service.AbstractService.start(AbstractService.java:193)
		at org.apache.hadoop.mapreduce.v2.app.MRAppMaster.serviceStart(MRAppMaster.java:1084)
		at org.apache.hadoop.service.AbstractService.start(AbstractService.java:193)
		at org.apache.hadoop.mapreduce.v2.app.MRAppMaster$4.run(MRAppMaster.java:1500)
		at java.security.AccessController.doPrivileged(Native Method)
		at javax.security.auth.Subject.doAs(Subject.java:415)
		at org.apache.hadoop.security.UserGroupInformation.doAs(UserGroupInformation.java:1671)
		at org.apache.hadoop.mapreduce.v2.app.MRAppMaster.initAndStartAppMaster(MRAppMaster.java:1496)
		at org.apache.hadoop.mapreduce.v2.app.MRAppMaster.main(MRAppMaster.java:1429)
	Caused by: java.io.IOException: Problem in starting http server. Server handlers failed
		at org.apache.hadoop.http.HttpServer2.start(HttpServer2.java:841)
		at org.apache.hadoop.yarn.webapp.WebApps$Builder.start(WebApps.java:273)
		... 10 more
	2015-12-29 07:34:44,554 INFO [main] org.apache.hadoop.ipc.CallQueueManager: Using callQueue class java.util.concurrent.LinkedBlockingQueue
	2015-12-29 07:34:44,554 INFO [Socket Reader #1 for port 47677] org.apache.hadoop.ipc.Server: Starting Socket Reader #1 for port 47677
	2015-12-29 07:34:44,558 INFO [IPC Server Responder] org.apache.hadoop.ipc.Server: IPC Server Responder: starting
	2015-12-29 07:34:44,558 INFO [IPC Server listener on 47677] org.apache.hadoop.ipc.Server: IPC Server listener on 47677: starting
	2015-12-29 07:34:44,599 INFO [main] org.apache.hadoop.mapreduce.v2.app.rm.RMContainerRequestor: nodeBlacklistingEnabled:true
	2015-12-29 07:34:44,599 INFO [main] org.apache.hadoop.mapreduce.v2.app.rm.RMContainerRequestor: maxTaskFailuresPerNode is 3
	2015-12-29 07:34:44,599 INFO [main] org.apache.hadoop.mapreduce.v2.app.rm.RMContainerRequestor: blacklistDisablePercent is 33
	2015-12-29 07:34:44,675 ERROR [main] org.apache.hadoop.mapreduce.v2.app.rm.RMContainerAllocator: Exception while registering
	java.lang.NullPointerException
		at org.apache.hadoop.mapreduce.v2.app.client.MRClientService.getHttpPort(MRClientService.java:174)
		at org.apache.hadoop.mapreduce.v2.app.rm.RMCommunicator.register(RMCommunicator.java:157)
		at org.apache.hadoop.mapreduce.v2.app.rm.RMCommunicator.serviceStart(RMCommunicator.java:122)
		at org.apache.hadoop.mapreduce.v2.app.rm.RMContainerAllocator.serviceStart(RMContainerAllocator.java:239)
		at org.apache.hadoop.service.AbstractService.start(AbstractService.java:193)
		at org.apache.hadoop.mapreduce.v2.app.MRAppMaster$ContainerAllocatorRouter.serviceStart(MRAppMaster.java:819)
		at org.apache.hadoop.service.AbstractService.start(AbstractService.java:193)
		at org.apache.hadoop.service.CompositeService.serviceStart(CompositeService.java:120)
		at org.apache.hadoop.mapreduce.v2.app.MRAppMaster.serviceStart(MRAppMaster.java:1087)
		at org.apache.hadoop.service.AbstractService.start(AbstractService.java:193)
		at org.apache.hadoop.mapreduce.v2.app.MRAppMaster$4.run(MRAppMaster.java:1500)
		at java.security.AccessController.doPrivileged(Native Method)
		at javax.security.auth.Subject.doAs(Subject.java:415)
		at org.apache.hadoop.security.UserGroupInformation.doAs(UserGroupInformation.java:1671)
		at org.apache.hadoop.mapreduce.v2.app.MRAppMaster.initAndStartAppMaster(MRAppMaster.java:1496)
		at org.apache.hadoop.mapreduce.v2.app.MRAppMaster.main(MRAppMaster.java:1429)
	2015-12-29 07:34:44,675 INFO [main] org.apache.hadoop.service.AbstractService: Service RMCommunicator failed in state STARTED; cause: org.apache.hadoop.yarn.exceptions.YarnRuntimeException: java.lang.NullPointerException
	org.apache.hadoop.yarn.exceptions.YarnRuntimeException: java.lang.NullPointerException
		at org.apache.hadoop.mapreduce.v2.app.rm.RMCommunicator.register(RMCommunicator.java:178)
		at org.apache.hadoop.mapreduce.v2.app.rm.RMCommunicator.serviceStart(RMCommunicator.java:122)
		at org.apache.hadoop.mapreduce.v2.app.rm.RMContainerAllocator.serviceStart(RMContainerAllocator.java:239)
		at org.apache.hadoop.service.AbstractService.start(AbstractService.java:193)
		at org.apache.hadoop.mapreduce.v2.app.MRAppMaster$ContainerAllocatorRouter.serviceStart(MRAppMaster.java:819)
		at org.apache.hadoop.service.AbstractService.start(AbstractService.java:193)
		at org.apache.hadoop.service.CompositeService.serviceStart(CompositeService.java:120)
		at org.apache.hadoop.mapreduce.v2.app.MRAppMaster.serviceStart(MRAppMaster.java:1087)
		at org.apache.hadoop.service.AbstractService.start(AbstractService.java:193)
		at org.apache.hadoop.mapreduce.v2.app.MRAppMaster$4.run(MRAppMaster.java:1500)
		at java.security.AccessController.doPrivileged(Native Method)
		at javax.security.auth.Subject.doAs(Subject.java:415)
		at org.apache.hadoop.security.UserGroupInformation.doAs(UserGroupInformation.java:1671)
		at org.apache.hadoop.mapreduce.v2.app.MRAppMaster.initAndStartAppMaster(MRAppMaster.java:1496)
		at org.apache.hadoop.mapreduce.v2.app.MRAppMaster.main(MRAppMaster.java:1429)
	Caused by: java.lang.NullPointerException
		at org.apache.hadoop.mapreduce.v2.app.client.MRClientService.getHttpPort(MRClientService.java:174)
		at org.apache.hadoop.mapreduce.v2.app.rm.RMCommunicator.register(RMCommunicator.java:157)
		... 14 more
	2015-12-29 07:34:44,676 INFO [main] org.apache.hadoop.mapreduce.v2.app.rm.RMContainerAllocator: Final Stats: PendingReds:0 ScheduledMaps:0 ScheduledReds:0 AssignedMaps:0 AssignedReds:0 CompletedMaps:0 CompletedReds:0 ContAlloc:0 ContRel:0 HostLocal:0 RackLocal:0
	2015-12-29 07:34:44,676 INFO [main] org.apache.hadoop.service.AbstractService: Service org.apache.hadoop.mapreduce.v2.app.MRAppMaster$ContainerAllocatorRouter failed in state STARTED; cause: org.apache.hadoop.yarn.exceptions.YarnRuntimeException: java.lang.NullPointerException
	org.apache.hadoop.yarn.exceptions.YarnRuntimeException: java.lang.NullPointerException
		at org.apache.hadoop.mapreduce.v2.app.rm.RMCommunicator.register(RMCommunicator.java:178)
		at org.apache.hadoop.mapreduce.v2.app.rm.RMCommunicator.serviceStart(RMCommunicator.java:122)
		at org.apache.hadoop.mapreduce.v2.app.rm.RMContainerAllocator.serviceStart(RMContainerAllocator.java:239)
		at org.apache.hadoop.service.AbstractService.start(AbstractService.java:193)
		at org.apache.hadoop.mapreduce.v2.app.MRAppMaster$ContainerAllocatorRouter.serviceStart(MRAppMaster.java:819)
		at org.apache.hadoop.service.AbstractService.start(AbstractService.java:193)
		at org.apache.hadoop.service.CompositeService.serviceStart(CompositeService.java:120)
		at org.apache.hadoop.mapreduce.v2.app.MRAppMaster.serviceStart(MRAppMaster.java:1087)
		at org.apache.hadoop.service.AbstractService.start(AbstractService.java:193)
		at org.apache.hadoop.mapreduce.v2.app.MRAppMaster$4.run(MRAppMaster.java:1500)
		at java.security.AccessController.doPrivileged(Native Method)
		at javax.security.auth.Subject.doAs(Subject.java:415)
		at org.apache.hadoop.security.UserGroupInformation.doAs(UserGroupInformation.java:1671)
		at org.apache.hadoop.mapreduce.v2.app.MRAppMaster.initAndStartAppMaster(MRAppMaster.java:1496)
		at org.apache.hadoop.mapreduce.v2.app.MRAppMaster.main(MRAppMaster.java:1429)
	Caused by: java.lang.NullPointerException
		at org.apache.hadoop.mapreduce.v2.app.client.MRClientService.getHttpPort(MRClientService.java:174)
		at org.apache.hadoop.mapreduce.v2.app.rm.RMCommunicator.register(RMCommunicator.java:157)
		... 14 more
	2015-12-29 07:34:44,676 INFO [main] org.apache.hadoop.service.AbstractService: Service org.apache.hadoop.mapreduce.v2.app.MRAppMaster failed in state STARTED; cause: org.apache.hadoop.yarn.exceptions.YarnRuntimeException: java.lang.NullPointerException
	org.apache.hadoop.yarn.exceptions.YarnRuntimeException: java.lang.NullPointerException
		at org.apache.hadoop.mapreduce.v2.app.rm.RMCommunicator.register(RMCommunicator.java:178)
		at org.apache.hadoop.mapreduce.v2.app.rm.RMCommunicator.serviceStart(RMCommunicator.java:122)
		at org.apache.hadoop.mapreduce.v2.app.rm.RMContainerAllocator.serviceStart(RMContainerAllocator.java:239)
		at org.apache.hadoop.service.AbstractService.start(AbstractService.java:193)
		at org.apache.hadoop.mapreduce.v2.app.MRAppMaster$ContainerAllocatorRouter.serviceStart(MRAppMaster.java:819)
		at org.apache.hadoop.service.AbstractService.start(AbstractService.java:193)
		at org.apache.hadoop.service.CompositeService.serviceStart(CompositeService.java:120)
		at org.apache.hadoop.mapreduce.v2.app.MRAppMaster.serviceStart(MRAppMaster.java:1087)
		at org.apache.hadoop.service.AbstractService.start(AbstractService.java:193)
		at org.apache.hadoop.mapreduce.v2.app.MRAppMaster$4.run(MRAppMaster.java:1500)
		at java.security.AccessController.doPrivileged(Native Method)
		at javax.security.auth.Subject.doAs(Subject.java:415)
		at org.apache.hadoop.security.UserGroupInformation.doAs(UserGroupInformation.java:1671)
		at org.apache.hadoop.mapreduce.v2.app.MRAppMaster.initAndStartAppMaster(MRAppMaster.java:1496)
		at org.apache.hadoop.mapreduce.v2.app.MRAppMaster.main(MRAppMaster.java:1429)
	Caused by: java.lang.NullPointerException
		at org.apache.hadoop.mapreduce.v2.app.client.MRClientService.getHttpPort(MRClientService.java:174)
		at org.apache.hadoop.mapreduce.v2.app.rm.RMCommunicator.register(RMCommunicator.java:157)
		... 14 more

---

【解决方案】

>workflow.xml的pig action注释掉如下属性：

---
	<!—<property>
	<name>mapreduce.user.classpath.first</name>
	<value>true</value>
	</property>
	<property>
	<name>oozie.launcher.mapreduce.user.classpath.first</name>
	<value>true</value>
	</property>—>
	
---
