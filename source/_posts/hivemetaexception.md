#hiveMetaException


	layout: post
	title: hive MetaException
	date: 2016-1-04 19:40:36
	categories: hive
	tags: 
		MetaException
		hive

---
>[ERROR message]



  	MetaException(message:Got exception: .
  	org.apache.hadoop.hive.metastore.api.MetaException.
  	Hive Schema version 0.13.0 does not match metastore's.
    schema version 1.1.0 Metastore is not upgraded or . 
    corrupt)


>[解决方案1]

	mysql> select * from VERSION;
	+--------+----------------+----------------------------------+.
	
	| VER_ID | SCHEMA_VERSION | VERSION_COMMENT |
	+--------+----------------+----------------------------------+
	| 1 | 1.1.0 | Set by MetaStore root@10.3.9.246 |
	+--------+----------------+----------------------------------+
	1 row in set (0.01 sec)

	mysql> TRUNCATE TABLE VERSION;
	Query OK, 0 rows affected (0.05 sec)

	mysql> INSERT INTO VERSION (VER_ID, SCHEMA_VERSION, VERSION_COMMENT) VALUES (1, '0.13.0', 'Hive release version 0.13.0');
	Query OK, 1 row affected (0.02 sec)

	mysql> select * from VERSION;
	+--------+----------------+-----------------------------+
	| VER_ID | SCHEMA_VERSION | VERSION_COMMENT |
	+--------+----------------+-----------------------------+
	| 1 | 0.13.0 | Hive release version 0.13.0 |
	+--------+----------------+-----------------------------+
	1 row in set (0.01 sec)
	



>[解决方案2]


	# ./schematool -dbType derby -initSchemaTo 0.1.3.0
	Metastore connection URL: jdbc:mysql://emr-busdevbigdata.c2lyaqdpfktq.us-west-1.rds.amazonaws.com/hive
	Metastore Connection Driver : com.mysql.jdbc.Driver
	Metastore connection User: hive
	Starting metastore schema initialization to 0.1.3.0
	org.apache.hadoop.hive.metastore.HiveMetaException: 	Unknown version specified for initialization: 0.1.3.0
	*** schemaTool failed ***
	
	
	
	
>根本原因，

hive-site.xml 第一次已启动修改为ture，  以后改为false


	<property>
		<name>hive.metastore.schema.verification</name>
		<value>false</value>
	</property>