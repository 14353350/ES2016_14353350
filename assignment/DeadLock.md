#死锁

####死锁就是两个或者多个进程，互相请求对方占有的资源

1. **互斥** ： 至少有一个资源必须处于非共享模式，即一次只有一个进程使用。如果另一进程申请该资源，那么申请进程就必须等到该资源被释放为止。
2. **占有并等待** ： 一个进程必须占有至少一个资源，并等待另一资源，而该资源为其他进程所占有。
3. **非抢占** ： 资源不能被抢占，即资源只能在进程完成任务后自动释放。
4. **循环等待** ： 若干进程之间形成一种头尾相接的循环等待资源关系

####样例运行结果
   ![deadlock](http://a3.qpic.cn/psb?/V10Juzzw1GQHCb/MlGkiVqNaikZMBvi1JZkoDh4Lwjqd8LJbdtJCPdoCkI!/b/dHABAAAAAAAA&bo=pgK4AQAAAAAFBzk!&rf=viewer_4)

####产生死锁原因

+ A中methodA方法调用B中last方法，B中methodB方法调用A中last方法。为产生循环等待创立了条件。
+ synchronized: 当它用来修饰一个方法或者一个代码块的时候，能够保证在同一时刻最多只有一个线程执行该段代码。 

	![](http://a3.qpic.cn/psb?/V10Juzzw1GQHCb/W6gvVtMmAwxQbVA03q7AcAtEub1zmggT43UhhZoQxYI!/b/dNoAAAAAAAAA&bo=QgN3AgAAAAADABE!&rf=viewer_4)

+ main线程等待20000执行a.methodA(a)
+ 当t.start()之后，线程t就被插入到调度队列里，当调度到他的时候，执行b.methodB(a)

	![](http://a2.qpic.cn/psb?/V10Juzzw1GQHCb/zslINIerVMARuVcPA.uxg1kcdIZ1quvjuRobCs6*Ffc!/b/dI0BAAAAAAAA&bo=kwHpAQAAAAADAF8!&rf=viewer_4)

+ 当main线程执行a.method(A)请求执行b.last(),而t线程正好执行到b.methodB(a)请求执行a.last(), 由于当一个线程访问Object中一个synchronized同步方法时，其他线程对object中所有其它synchronized同步代码块或同步方法的访问将被阻塞，main线程和t线程都被阻塞，从而产生死锁。
