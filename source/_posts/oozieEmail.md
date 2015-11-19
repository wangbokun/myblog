layout: post
title: oozie email
date: 2015-11-02 19:40:36
categories: oozie
tags: 
---
		<property>
		 	<name>
		 		oozie.service.ActionService.executor.ext.classes
		 	</name>
		 	<value>
		 		org.apache.oozie.action.email.EmailActionExecutor,
		 		org.apache.oozie.action.hadoop.HiveActionExecutor,
		 		org.apache.oozie.action.hadoop.ShellActionExecutor,
		 		org.apache.oozie.action.hadoop.SqoopActionExecutor
		 	</value>
		</property>

---

		<property>
			<name>
				oozie.service.SchemaService.wf.ext.schemas
			</name>
			<value>
				shell-action-0.1.xsd,email-action-0.1.xsd,hive-action-0.2.xsd,sqoop-action-0.2.xsd,ssh-action-0.1.xsd
			</value>
		</property>
