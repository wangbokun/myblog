#hadoopYarnConfig


	layout: post
	title: yarn mem config
	date: 2016-1-04 19:40:36
	categories: hadoop
	tags: 
		yarn
		hadoop
		mem
		
		
---

> yarn-site.xml  && mapred-site.xml  内存配置标准



Configuration File | Configuration Setting | Value Calculation
:----------- | :-----------: | -----------:
yarn-site.xml         | yarn.nodemanager.resource.memory-mb        | containers * RAM-per-container
yarn-site.xml         | yarn.scheduler.minimum-allocation-mb        | RAM-per-container
yarn-site.xml         | yarn.scheduler.maximum-allocation-mb        | containers * RAM-per-container
yarn-site.xml         | yarn.app.mapreduce.am.resource.mb        | 2 * RAM-per-container
yarn-site.xml         | yarn.app.mapreduce.am.command-opts        | 0.8 * 2 * RAM-per-container
yarn-site.xml         | yarn.app.mapreduce.am.resource.mb        | 2 * RAM-per-container
mapred-site.xml       | mapreduce.map.memory.mb        | RAM-per-container
mapred-site.xml       | mapreduce.reduce.memory.mb        | 2 * RAM-per-container
mapred-site.xml       | mapreduce.map.java.opts        | 0.8 * RAM-per-container
mapred-site.xml       | mapreduce.reduce.java.opts        | 0.8 * 2 * RAM-per-container


---

* RAM-per-container is minimum-allocation-mb ，一般设置为1024m.
* 其余按公式以此类推
