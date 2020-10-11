* Fink 窗口的骨架结构中有两个必须的两个操作

* 使用窗口分配器（WindowAssigner）将数据流中的元素分配到对应的窗口
* 当满足窗口触发条件后，对窗口内的数据使用窗口处理函数（Window Function）进行处理，常用的Window Function
有reduce、aggregate、process


## Fink支持的窗口类型

* time window
	* Tumbling Windows 滚动窗口
	* Sliding Windows 滑动窗口
	* Session Windows 会话窗口
	* Globall Windows 全局窗口
* count window
	* 滚动count
	* 滑动count


## Siding Window
* 滑动窗口以一个slide不断向前滑动，窗口的长度固定
	* Window Size ： 窗口大小
	* Window Slide： 滑动间隔
* 数据可以被重复计算，取决于Size和Slide Time
	* Slide Time < Window Size 数据多个窗口中统计
	* Slide Time > Window Size 数据可能不再任何一个Window中

## Tumbiing Window 滚动窗口
* 滚动窗口下窗口之间不重叠，且窗口长度是固定的
* 特殊的滑动窗口
	Window Size = Window Slide

## Session Window
* 根据Session gap切分不同的窗口
* 当一个窗口在大于Session gap的时间内没有接收到新数据时，窗口关闭。
* Window Size可变
