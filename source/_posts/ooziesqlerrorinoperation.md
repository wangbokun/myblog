#oozieSQLerrorinoperation

	layout: post
	title: oozie E0603 SQL error in operation
	date: 2016-1-05 15:40:36
	categories: oozie
	tags: 
		ooize  
		mail
 
---

【ERROR MESSAGE】



		org.apache.oozie.command.CommandException: E0603: SQL error in operation, <openjpa-2.2.2-r422266:1468616 fatal stor
	e error> org.apache.openjpa.persistence.RollbackException: The transaction has been rolled back.  See the nested ex
	ceptions for details on the errors that occurred.
	FailedObject: org.apache.oozie.CoordinatorActionBean@266c1312
        at org.apache.oozie.command.coord.CoordMaterializeTransitionXCommand.performWrites(CoordMaterializeTransiti
	onXCommand.java:158)
        at org.apache.oozie.command.MaterializeTransitionXCommand.execute(MaterializeTransitionXCommand.java:75)
        at org.apache.oozie.command.MaterializeTransitionXCommand.execute(MaterializeTransitionXCommand.java:29)
        at org.apache.oozie.command.XCommand.call(XCommand.java:286)
        at org.apache.oozie.service.CallableQueueService$CallableWrapper.run(CallableQueueService.java:175)
        at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1145)
        at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:615)
        at java.lang.Thread.run(Thread.java:745)
	Caused by: org.apache.oozie.executor.jpa.JPAExecutorException: E0603: SQL error in operation, <openjpa-2.2.2-r42226
	6:1468616 fatal store error> org.apache.openjpa.persistence.RollbackException: The transaction has been rolled back
	.  See the nested exceptions for details on the errors that occurred.
	FailedObject: org.apache.oozie.CoordinatorActionBean@266c1312
        at org.apache.oozie.service.JPAService.executeBatchInsertUpdateDelete(JPAService.java:425)
        at org.apache.oozie.executor.jpa.BatchQueryExecutor.executeBatchInsertUpdateDelete(BatchQueryExecutor.java:
	132)
        at org.apache.oozie.command.coord.CoordMaterializeTransitionXCommand.performWrites(CoordMaterializeTransiti
	onXCommand.java:133)
        ... 7 more
	Caused by: <openjpa-2.2.2-r422266:1468616 fatal store error> org.apache.openjpa.persistence.RollbackException: The transaction has been rolled back.  See the nested exceptions for details on the errors that occurred.
	FailedObject: org.apache.oozie.CoordinatorActionBean@266c1312
        at org.apache.openjpa.persistence.EntityManagerImpl.commit(EntityManagerImpl.java:594)
        at org.apache.oozie.service.JPAService.executeBatchInsertUpdateDelete(JPAService.java:421)
        ... 9 more
	Caused by: <openjpa-2.2.2-r422266:1468616 fatal store error> org.apache.openjpa.persistence.EntityExistsException: The transaction has been rolled back.  See the nested exceptions for details on the errors that occurred.
	FailedObject: org.apache.oozie.CoordinatorActionBean@266c1312
        at org.apache.openjpa.kernel.BrokerImpl.newFlushException(BrokerImpl.java:2347)
        at org.apache.openjpa.kernel.BrokerImpl.flush(BrokerImpl.java:2184)
        at org.apache.openjpa.kernel.BrokerImpl.flushSafe(BrokerImpl.java:2082)
        at org.apache.openjpa.kernel.BrokerImpl.beforeCompletion(BrokerImpl.java:2000)
        at org.apache.openjpa.kernel.LocalManagedRuntime.commit(LocalManagedRuntime.java:81)
        at org.apache.openjpa.kernel.BrokerImpl.commit(BrokerImpl.java:1524)
        at org.apache.openjpa.kernel.DelegatingBroker.commit(DelegatingBroker.java:933)
        at org.apache.openjpa.persistence.EntityManagerImpl.commit(EntityManagerImpl.java:570)
       	 ... 10 more
       	 
 		Caused by: <openjpa-2.2.2-r422266:1468616 fatal store error> .					org.apache.openjpa.persistence.EntityExistsException: 	Duplicate entry '0000940-151229085645556-oozie-oozi-C@261' for key 'PRIMARY' {prepstmnt 1380510951 INSERT INTO COORD_ACTIONS (id, action_number, action_xml, console_url, created_conf, created_time, error_code, error_message, external_id, external_status, job_id, last_modified_time, missing_dependencies, nominal_time, pending, push_missing_dependencies, rerun_time, run_conf, sla_xml, status, time_out, tracker_uri, job_type) VALUES (?, ?, ?, ?, ?, ?, ?, ?, ?, ?, ?, ?, ?, ?, ?, ?, ?, ?, ?, ?, ?, ?, ?)} [code=1062, state=23000]
	FailedObject: org.apache.oozie.CoordinatorActionBean@266c1312
        at org.apache.openjpa.jdbc.sql.DBDictionary.narrow(DBDictionary.java:4947)
        at org.apache.openjpa.jdbc.sql.DBDictionary.newStoreException(DBDictionary.java:4922)
        at org.apache.openjpa.jdbc.sql.SQLExceptions.getStore(SQLExceptions.java:136)
        at org.apache.openjpa.jdbc.sql.SQLExceptions.getStore(SQLExceptions.java:78)
        at org.apache.openjpa.jdbc.kernel.PreparedStatementManagerImpl.flushAndUpdate(PreparedStatementManagerImpl.java:144)
        at org.apache.openjpa.jdbc.kernel.BatchingPreparedStatementManagerImpl.flushAndUpdate(BatchingPreparedStatementManagerImpl.java:79)
        at org.apache.openjpa.jdbc.kernel.PreparedStatementManagerImpl.flushInternal(PreparedStatementManagerImpl.java:100)
        at org.apache.openjpa.jdbc.kernel.PreparedStatementManagerImpl.flush(PreparedStatementManagerImpl.java:88)
        at org.apache.openjpa.jdbc.kernel.ConstraintUpdateManager.flush(ConstraintUpdateManager.java:550)
        at org.apache.openjpa.jdbc.kernel.ConstraintUpdateManager.flush(ConstraintUpdateManager.java:106)
        at org.apache.openjpa.jdbc.kernel.BatchingConstraintUpdateManager.flush(BatchingConstraintUpdateManager.java:59)
        at org.apache.openjpa.jdbc.kernel.AbstractUpdateManager.flush(AbstractUpdateManager.java:105)
        at org.apache.openjpa.jdbc.kernel.AbstractUpdateManager.flush(AbstractUpdateManager.java:78)
        at org.apache.openjpa.jdbc.kernel.JDBCStoreManager.flush(JDBCStoreManager.java:732)
        at org.apache.openjpa.kernel.DelegatingStoreManager.flush(DelegatingStoreManager.java:131)
        ... 17 more


>1

```bash
	$ sudo -u oozie /usr/lib/oozie/bin/ooziedb.sh create -sqlfile /usr/lib/oozie/oozie.sql -run  or
 $ sudo /usr/lib/oozie/bin/ooziedb.sh create -sqlfile /usr/lib/oozie/oozie.sql -run	
```

---

>2

```bash
	$ sudo -u oozie /usr/lib/oozie/bin/ooziedb.sh upgrade -run
```

---
>1 or 2  验证中....

