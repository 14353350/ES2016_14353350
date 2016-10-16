#DOL实例分析&编程


###一.修改example2，让3个square模块变成2个

####example2.xml通过迭代，定义了3个square模块, 改为2即可

1. 进入/dol/examples/example2
2. 使用gedit打开example2.xml
3. 修改N=3为N=2，如图 
	![example2.xml](http://s4.sinaimg.cn/middle/006buDuJzy75zvIPqVld3&690)

####运行结果

![](http://s16.sinaimg.cn/middle/006buDuJzy75zvIUXMP1f&690)

####example2.dot

![](http://a3.qpic.cn/psb?/V10Juzzw1GQHCb/Db33VPd3Vkb*oYt3nqlmLIK*tsKAAyfiTFLQq5UpJsA!/b/dI8AAAAAAAAA&bo=UgJpAAAAAAAFABo!&rf=viewer_4)

###二.修改example1，使其输出3次方数

####信号处理函数square.c将输入信号i平方后写出到输出端，使i立方即可

1. 进入/dol/examples/example2/src
2. 使用gedit打开square.c
3. 修改 i = i \* i 为 i = i \* i \* i ，如图
4. 上次有运行过，修改需要将之前build的文件夹 /dol/bulid/bin/main下的example1 删掉
	![example2.xml](http://s9.sinaimg.cn/middle/006buDuJzy75zvIPbpSf8&690)

####运行结果

![](http://s3.sinaimg.cn/middle/006buDuJzy75zvIObzI62&690)

####example1.dot

![](http://a3.qpic.cn/psb?/V10Juzzw1GQHCb/OrCJfHuPDj66ESLOgX1o*1p5aeNG3CYDA5IID2zG*PE!/b/dAoBAAAAAAAA&bo=9gGCAAAAAAAFB1E!&rf=viewer_4)

##实验感想

1. example中各文件的含义：
 + src文件夹：各进程（生产者，消费者，处理模块等）的功能定义
	 
		xxx.c和xxx.h：模块 xxx\_init是初始化函数，xxx\_fire 是信号产生函数
		
		使用DOL\_read和DOL\_write读写端口
 + example.xml：系统架构即模块连接方式定义
		+ process	进程
			+ port	端口
				+ type  input or output
				+ name  不同进程（通道）中的name独立
			+ source	源文件
		+ sw_channel	链接两个端口的通道  type 类型 size 缓冲区大小 name 名字
			+ port
		+ connection
			+ origin	name 指定进程或通道
				+ port	name 指定连接的端口
			+ target
				+ port








