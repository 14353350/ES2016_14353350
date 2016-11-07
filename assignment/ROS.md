#Ubuntu16.04 ROS安装

###1. 设置安装源

<pre><code>$	sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list' </code></pre>

###2. 设置keys

<pre><code>$	sudo apt-key adv --keyserver hkp://ha.pool.sks-keyservers.net:80 --recv-key 0xB01FA116 </code></pre>

![](http://a1.qpic.cn/psb?/V10Juzzw1GQHCb/3*JsSyVHzShBJw5XC.bPujYq0t1p6aHwK6Z4vm*kKeE!/b/dHEBAAAAAAAA&bo=1gK7AAAAAAAFB0s!&rf=viewer_4)

###3. 安装

<pre><code>$	sudo apt-get update	
$	sudo apt-get install ros-kinetic-desktop-full </code></pre>

###4. 初始化

<pre><code>$	sudo rosdep init </code></pre>

![](http://a2.qpic.cn/psb?/V10Juzzw1GQHCb/Kq2CVhmp2YE8uU.kR0PM2XLJ3MkgqOe261PuBahtKGU!/b/dAkBAAAAAAAA&bo=GwJfAAAAAAAFAGU!&rf=viewer_4)

<pre><code>$	rosdep update </code></pre>

![](http://a3.qpic.cn/psb?/V10Juzzw1GQHCb/AcBVuBs.MOg9AXGB8vDwiQr.t4c8H4axIRGrTU8K4bA!/b/dI8AAAAAAAAA&bo=3gIVAQAAAAAFAOs!&rf=viewer_4)

###5. 环境配置

<pre><code>$	echo "source /opt/ros/kinetic/setup.bash" >> ~/.bashrc 
$	source ~/.bashrc </code></pre>

###6. 安装rosinstall

<pre><code>$	sudo apt-get install python-rosinstall </code></pre>

###7. 测试

<pre><code>$	roscore </code></pre>

![](http://a3.qpic.cn/psb?/V10Juzzw1GQHCb/QfWzkypCh0ENHqyPT1nxJkLCpfHVVUEz18AfI4kKWhA!/b/dHwBAAAAAAAA&bo=bAPYAQAAAAAFAJU!&rf=viewer_4)

新建Terminal,输入下述命令.开启一个小海龟界面

<pre><code>$	rosrun turtlesim turtlesim_node </code></pre>

![](http://a3.qpic.cn/psb?/V10Juzzw1GQHCb/wSNTo0M25Fz2is0yy8uONtcx64JsborGFL4VdGBFnMM!/b/dI8AAAAAAAAA&bo=8wEMAgAAAAAFAN8!&rf=viewer_4)

再打开一个Terminal,输入下述命令

<pre><code>$	rosrun turtlesim turtle_teleop_key </code></pre>

键盘按方向键,可控制小乌龟移动

![](http://a2.qpic.cn/psb?/V10Juzzw1GQHCb/jlm.FhLrXlJE9iYMQY36Bu1bwSm.QKvnG3UfJS.eJyw!/b/dNwAAAAAAAAA&bo=9AENAgAAAAAFANk!&rf=viewer_4)

再打开一个Terminal,输入下述命令,可以看到当前ROS nodes以及Topic等图形展示

<pre><code>$	rosrun rqt_graph rqt_graph </code></pre>

![](http://a1.qpic.cn/psb?/V10Juzzw1GQHCb/HBKFtrznZqcP6CcQWvJu8SghuaoHq87elkDzHxiNoJ4!/b/dOQAAAAAAAAA&bo=dAPRAQAAAAAFAIQ!&rf=viewer_4)

由上图可见,左右两边矩形为ROS node,中间连线上是Topic名称
