Flink Runtime 整体架构

整体架构包含了三个部分
* JobManager （Master）
* TaskManager （Worker）
* Client

Client端是用户编写code在客户端进行相应的优化和编译，产生dataflow的graph，也就是streamgraph，编译出来Jobgraph对象，然后再通过客户端通过actor system进行rpc的远程访问，akka之间会进行远程通信，然后把对应的作业，提交到集群上面。
在集群里面运行起来之后，jobmanager是负责对整个提交过来的JobGraph的管理，这里面会有相应的调度性的工作，和checkpoint的一些协调性质的工作，jobmanager就是对整个job的管理，
jobmanager就会跟taskmanager进行通信，也是通过actor system ， 这样的一种远程通信方式去做，这里面会发现提交过来的作业会进行solt的申请，solt就是每一个taskmanager里面的计算资源，
jobmanager通过scaledule 去调出来的task，对应分发到taskmanager的solt去执行起来，这时候会阐释task solt的线程，
这个线程会把jobmanager的每一个作业，拆分成耕细粒度的作业，去执行起来，最终完成整个job的运行。


## Dispatcher
* 集群Job的调度分发
* 根据JobGraph启动JobManager

## ResourceManager
* 集群层面资源管理
* 适配不同的资源管理
* 核心组件： SoltManager

## Session模式
* Runtime集群组件共享
* 资源复用
* Runtime中有多个Jobmanager

## Per-job模式
* Runtime集群组件仅为单个Job服务
* 资源相对独立
* 不支持提交JobGraph



