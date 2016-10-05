#DOL配置

##Description
>**Distributed operation layer (DOL)** is a software development framework to program parallel applications. The DOL allows to specify applications based on the Kahn process network model of computation and features a simulation engine based on SystemC. Moreover, the DOL provides an XML-based specification format to describe the implementation of a parallel application on a multiprocessor systems, including binding and mapping.

##How To Install

####安装必要环境

<pre><code> 
$	sudo apt-get update
$	sudo apt-get install ant
$	sudo apt-get install openjdk-8-jdk
$	sudo apt-get install unzip
</code></pre>

####下载文件

<pre><code>
$	sudo wget http://www.accellera.org/images/downloads/standards/systemc/systemc-2.3.1.tgz
$	sudo wget http://www.tik.ee.ethz.ch/~shapes/downloads/dol_ethz.zip
</code></pre>

####解压文件

1. 新建dol的文件夹	<pre><code>$	mkdir dol</code></pre>
2. 将dolethz.zip解压到dol文件夹中	<pre><code>$	unzip dol_ethz.zip -d dol</code></pre>
3. 解压systemc	<pre><code>$	tar -zxvf systemc-2.3.1.tgz</code></pre>

####编译systemc

1. 解压后进入systemc-2.3.1的目录下  <pre><code>$	cd systemc-2.3.1 </code></pre>
2. 新建一个临时文件夹objdir并进入  <pre><code>$	mkdir objdir 
$	cd objdir</code></pre>
3. 运行configure(能根据系统的环境设置一下参数，用于编译)  <pre><code>$ ../configure CXX=g++ --disable-async-updates </code></pre>
   下图为运行configure之后的截图
    ![](http://s11.sinaimg.cn/middle/006buDuJzy75o3mIVXc5a&690)
4. 编译  <pre><code>$	sudo make install</code></pre>
   编译完后文件目录如下($cd .. $ls),能看到include, lib-linux64(对于32位系统，这里是lib-linux)

	![](http://s1.sinaimg.cn/middle/006buDuJzy75o3mK0gw10&690)
5. 记录当前的工作路径（会输出当前所在路径，记下来，待会有用） <pre><code>$	pwd</code></pre>
   这里表示我当前的工作路径为 /root/systemc-2.3.1
	![](http://s10.sinaimg.cn/middle/006buDuJzy75o3RNl0d49&690)
####编译dol

1. 进入刚刚的dol文件夹，修改build.xml文件。找到下面这段话，就是说上面编译的systemc位置在哪里
    <pre><code>  property name=”systemc.inc” value=”YYY/include” 	
	  property name=”systemc.lib” value=”YYY/lib-linux/libsystemc.a” </code></pre>
  把YYY改成上页pwd的结果（注意，对于 64位 系统的机器，lib-linux要改成lib-linux64） 

2. 编译 <pre><code>$	ant -f build_zip.xml all</code></pre>若成功会显示build successful
3. 运行第一个例子

	进入build/bin/main路径下
    <pre><code> $	cd build/bin/main </code></pre>
    运行
    <pre><code> $	ant -f runexample.xml -Dnumber=1 </code></pre>
    成功结果如图

	![](http://s9.sinaimg.cn/middle/006buDuJzy75o4m9hKUb8&690)
##Experimental experience
1. Make
 + 在Linux和Ubuntu环境中，make工具主要被用来进行工程编译和程序
 + Makefile文件：描述了整个工程所有文件的编译顺序、编译规则
 + make通过比较对应文件（规则的目标和依赖）的最后修改时间，来
决定哪些文件需要更新、那些文件不需要更新。
链接
2. Ant 
 + Ant是一种基于Java开放源码构建工具，通过配置一个xml文件快速开发创建和部署过程。Ant使用构建文件来完成一系列操作。
 + Ant用Java的类来扩展
 + 它是一个流程脚本引擎，用于自动化调用程序完成项目的下列任务：编译、打包、测试、调用系统命令（exec) 
 
 	[ant make g++ qmake 详解](http://blog.csdn.net/hudfang/article/details/46429747)
3. Ant的优点
 + 跨平台性。Ant是纯java语言编写的，所示具有很好的跨平台性。
 + 操作简单。Ant是由一个内置任务和可选任务组成的。Ant运行时需要一
个XML文件(构建文件)
 +  Ant通过调用target树，就可以执行各种task。每个task实现了特定接口对象。由于Ant构建文件时XML格式的文件，所以和容易维护和书写，而且结构很清晰
 + Ant可以集成到开发环境中。由于Ant的跨平台性和操作简单的特点，它很容易集成到一些开发环境中去
	
	[ant的好处](http://blog.sina.com.cn/s/blog_70f1758901018sgl.html)









