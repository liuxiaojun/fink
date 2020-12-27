SourceFunction 自定义数据源

## 自定义source和sink


## New Source API 
* Bounded File Dource
    * 每个Split就是一个文件或者文件一部分
    * SplitEnumerator列举出指定文件夹下的全部文件，并逐步分配给Reader；
    * 一旦所有的Splits全部分配完毕，此时SplitEnumerator会给Reader发送NoMoreSplits消息；
    * SourceReader接收到Splits后，会根据InputFormat读取数据；
    * 当SourceReader接收到NoMoreSplits消息时，会完成并停止；

* Unbounded Streaming File Source
	* SplitEnumerator不会发送NoMoreSplits消息；
	* 二是周期性的读取指定URI、Path的地址，并获取新的文件，进而转化为Splits发送给Reader；

* Unbounded Streaming Kafka Source
    * 每个Split对应一个Kafka Topic Partition
    * SplitEnumberator 连接Kafka Broker获取当前Topic下的Partition；
    * SourceReader获取到SplitEnumberator发送的Split（Partition），创建与Kafka Topic Partition的连接，读取数据；
    * 由于数据误解，因此分配的Splits会一直存在，不断读取数据；
    * SplitEnumberator会周期性的监听Kafka Brokers，自动发现新的Partition

* Bounded Kafka Source
    * 和上面的操作一样，只不过每个Slits会指定终止条件，也就是当前Partition的最终Offset；
    * 当数据消费到指定Offset后， Split完成消费；
    * 当分配的所有Splits完成后，停止Reader线程；
