作用
* 标记Event-Time的前进过程
* 跟随DataStream Event-Time变动，并自身携带Event-Time
* 用于表明所有的较早时间可能到达完毕
* 本身也属于特殊事件


说明
* Watermark = Max EventTime - Latethreshold
* Latethreshold 越高处理延时越高
* 启发式更新
* 解决一定范围内的乱序事件
* 窗口出发条件： Current Watermark > Window EventTime
* Watermark 告诉窗口不会有更晚的数据来
* idel Watermark仅会发生在顺序事件中
