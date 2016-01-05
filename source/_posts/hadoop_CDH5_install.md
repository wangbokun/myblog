#hadoop_CDH5_install
layout: post
title: CDH5 install
date: 2015-12-24 14:00:00
categories:  hadoop
tags: 
 hadoop
 hdfs
 yarn
		
---

# hadoop CDH5 install

> 一：安装前准备工作

  - hostname 
     采用rsync分发文件 /etc/hosts , change_hostsname.sh，然后批量run script.
 
### hosts文件：

```	text
10.50.x.x launcher_x.x.com
10.50.x.x zk1.x.x.com
10.50.x.x zk2.x.x.com
10.50.x.x zk3.x.x.com
10.50.x.x nn1.x.x.com
10.50.x.x nn2.x.x.com
10.50.x.x rm1.x.x.com
10.50.x.x rm2.x.x.com
10.50.x.x dn001.x.x.com
``` 

###  script :  change_hostsname.sh  
  
``` bash
#!/bin/sh
IP=`hostname  -i`
IP=`ip ad|grep inet|grep bond0|awk -F' ' '{print $2}'|awk -F'/' '{print $1}'`
HOST_NAME=`grep $IP  /etc/hosts|awk -F' '   '{print $2}'`
sed -i "2s/^.*$/HOSTNAME=$HOST_NAME/"   /etc/sysconfig/network
hostname $HOST_NAME
```   