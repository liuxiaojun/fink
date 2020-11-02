## Window多流合并
* Window Join
* Interval Join

## Window Join
```
streamA.join(StreamB)
	.where(<KeySelector>)
	.equalTO(<KeySelector>)
	.window(<WindowAssigner>)
	.apply(<joinFunction>)
```
