#oozieEmail

	layout: post
	title: oozie email
	date: 2015-11-02 19:40:36
	categories: oozie
	tags: 
		ooize  smtp
		mail
 
---


- 添加配置文件到/etc/oozie/conf/oozie-site.xml ，如下：

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
---


> oozie smtp 需要配置以下内容oozie-site.xml

---

	<property>
        <name>oozie.email.smtp.host</name>
        <value>xxxx.com</value>
    </property>
    <property>
        <name>oozie.email.smtp.port</name>
        <value>25</value>
    </property>
    <property>
        <name>oozie.email.from.address</name>
        <value>hadoop_devops@xxx.com</value>
    </property>
   

    <property>
        <name>oozie.email.smtp.auth</name>
        <value>true</value>
    </property>

    <property>
        <name>oozie.email.smtp.username</name>
        <value>xxxx</value>
    </property>

    <property>
        <name>oozie.email.smtp.password</name>
        <value>xxxx</value>
    </property>
---



>还存在一个问题，关于oozie TLS 尚未解决,后续更新....