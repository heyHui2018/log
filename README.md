logging(Forked from ngaut/log)
=======
新增SetCallDepth方法,用于修改寻找调用函数对应的调用深度,以便对日志输出进行封装及自定义。

example：[https://github.com/heyHui2018/best-practise]

* 声明：
```
type LogP struct {
	TraceId string
}
log.SetCallDepth(5)
```
* 封装
```
func (l *LogP) logP(format string, v ...interface{}) {
	log.Infof(l.TraceId+" "+format, v)
}
```
* 调用：
```
l := new(LogP)
	l.TraceId = time.Now().Format("20060102150405") + utils.GetRandomString()
	l.logP("Register 完成,耗时 = %v", 123)
```
* 说明：
* [x] 实现自定义
* [x] 准确输出调用层级