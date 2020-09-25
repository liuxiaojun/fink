例如如何去兼顾数据一致性

大规模数据处理

以及误解乱序数据处理等

* 数据从上一个Operation节点直接Push到下一个Operation节点
* 各节点可以分布在不同的Task线程中运行，数据在Operation之间传递
* 具有Shuffe过程，单数数据不像MapReduce模型，Reduce从Map端拉取数据
* 实现框架有Apache Storm和 Apache Fink以及 Apace beam
