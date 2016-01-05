#hadoopYarnCapacityScheduler


	layout: post
	title: yarn 调度器 Capacity Scheduler
	date: 2016-1-04 19:40:36
	categories: hadoop
	tags: 
		yarn
		hadoop
		capacity
		scheduler
		
		
---
>hadoop三种调度器简单说明

* FIFO 系统默认调度器.按照作业提交时间先后顺序依次执行.
* Capacity Scheduler 资源调度器,为租户分配不同QUEUE来提交作业，每个QUEUE可以限制总统量.
* Fair Scheduler 公平调度器，正如其名，对于每个作业一视同仁，谁先抢到资源谁先用.


> 本章重点说明下 Capacity Scheduler

* 先说明下几个配置含义

       
       <property>
        <name>yarn.scheduler.capacity.maximum-applications</name>
        <value>10000</value>
        <description>
           集群最大并行作业数
        </description>
       <property>



	   <property>
        <name>yarn.scheduler.capacity.maximum-am-resource-percent</name>
        <value>0.1</value>
        <description>
      	集群中可用于运行application master的资源比例上限，用于限制并发运行的应用
      	 即：yarn.scheduler.capacity.maximum-applications*yarn.scheduler.capacity.maximum-am-resource-percent = 最大并行任务数
    	</description>
   	   </property>
   	   
----
>application master
 
* 这个地方提到了application master 先简单介绍一下.如图所示：
  ![Mou icon](http://wangbokun.com/img/rsourcemanager_liucheng.png)
  
  一个作业提交倒ResourceManager后，RM会先找一台nodemanager启动一个Container，这个Container中会运行一个application master(和RM建立链接，汇报作业运行状态，直到作业完成会被销毁)，然后application master会分配作业到nodemanager上，再去run map task && reduce task
 ***
 这个简单提下，后续专门写这块逻辑
 
 
 * 继续看配置
 
 
 
        <property>
         <name>yarn.scheduler.capacity.node-locality-delay</name>
         <value>30</value>
         <description>
     		 本地延迟分配次数，默认为40，设置-1，意思是关闭。
    	 </description>
   		</property>
   
   
        <property>
         <name>yarn.scheduler.capacity.root.queues</name> 
         <value>default,queue1,queue2,queue3</value>
         <description>
     		 设置queue个数、名称
    	 </description>
        </property>



	