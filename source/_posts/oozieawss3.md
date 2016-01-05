#oozieawss3

	layout: post
	title: oozie 访问aws s3
	date: 2016-1-06 20:40:36
	categories: oozie
	tags: 
		ooize  
		aws 
		s3
		ec2
		
 
---


>ec2自建CDH5.1后，发现访问s3不太友好，于是搜刮EMR上oozie s3的一些lib  jar 过来，完美解决，因为不开源只能先把jar搞过来，能跑就可以了,
>会遇到很多问题，比如oozie check input s3目录，文件命名存在，却check不到，等等一系列.
记录解决办法如下两步.

---
		/usr/lib/oozie/libext
		/usr/lib/oozie/libserver
		/usr/lib/oozie/libtools
---


> 修改oozie-site.xml

---
     <property>
        <name>oozie.service.HadoopAccessorService.supported.filesystems</name>
        <value>hdfs,viewfs,s3,s3n</value>
    </property>
---    
