#oozie_sharelib_upgrade

	layout: post
	title: oozie  sharelib  upgrade
	date: 2015-11-30 19:40:36
	categories: oozie
	tags:
	 ooize
	 sharelib

---

>  ozie  hdfs url 中添加新的pig jar不能被识别,需要upgrade sharelib，记录操作如下：

``` bash
hadoop fs -put  pig_1_4  /user/oozie/share/lib/lib_20151202054214/pig_14
```
----

然后list 不出来pig_14

----

```  bash
	sudo -u oozie oozie  admin -shareliblist -oozie http://localhost:11000/oozie
```



``` text
	[Available ShareLib]
	oozie
	hive
	distcp
	hcatalog
	sqoop
	mapreduce-streaming
	spark
	hive2
	pig
```



---
> 需要执行update share lib  命令如下


``` bash
oozie admin -sharelibupdate  -oozie http://localhost:11000/oozie
```

>然后执行list就可以看到相应的jar 目录 pig_14


``` bash
	oozie  admin -shareliblist -oozie http://localhost:11000/oozie
```

``` text
	[Available ShareLib]
	oozie
	hive
	distcp
	hcatalog
	sqoop
	mapreduce-streaming
	spark
	pig_14
	hive2
	pig

```
