#oozieshellactiondiscp

	layout: post
	title: oozie discp s3 shell action Permission denied
	date: 2016-1-13 19:40:36
	categories: oozie
	tags:
		ooize

---


>CDH oozie discp s3，使用用户A，启动oozie job，但是mr运行的时候默认使用yarn用户来启动mr，导致报错


---
          Diagnostics: Permission denied: user=ads_up, access=EXECUTE, inode="/user/yarn/.staging":yarn:hdfs:drwx------
---


##【解决方案】

*  Disctcp Action

``` xml
        <action name="distcp-node">
        <distcp xmlns="uri:oozie:distcp-action:0.1">
         <job-tracker>${jobTracker}</job-tracker>
           <name-node>${nameNode}</name-node>
           <prepare>
             <delete path="${nameNode}/user/${wf:user()}/${examplesRoot}/output-data/${outputDir}"/>
           </prepare>
           <configuration>
              <property>
                <name>mapred.job.queue.name</name>
                <value>${queueName}</value>
              </property>
           </configuration>
        <arg>${nameNode}/user/${wf:user()}/${examplesRoot}/input-data/text/data.txt</arg>
        <arg>${nameNode}/user/${wf:user()}/${examplesRoot}/output-data/${outputDir}/data.txt</arg>
        </distcp>
        <ok to="end"/>
        <error to="fail"/>
        </action>
```

* Shell Action

``` xml
        <action name="distcp_shell">
          <shell xmlns="uri:oozie:shell-action:0.2">
              <job-tracker>${jobTracker}</job-tracker>
              <name-node>${nameNode}</name-node>
              <prepare>
                  <delete path='${file_path}'/>
              </prepare>
              <configuration>
                  <property>
                      <name>mapred.job.queue.name</name>
                      <value>${queueName}</value>
                  </property>

              </configuration>
              <exec>${distcp_script}</exec>
              <file>${distcp_script_path}#${distcp_script}</file>
              <capture-output/>
          </shell>
          <ok to="end"/>
          <error to="send_email"/>
        </action>
```




* shell script


```bash
#!/bin/sh
          ACCESSKEYID=xxxx
          SECRETACCESSKEY=xxxx

          export HADOOP_USER_NAME=A
          hadoop distcp -D fs.s3n.awsAccessKeyId=$ACCESSKEYID \
          -D fs.s3n.awsSecretAccessKey=$SECRETACCESSKEY \
          -f file_list_path/part-00000 \
          hdfs://cdh/current_user/file_data_path/
```





##注意：


export HADOOP_USER_NAME=A
