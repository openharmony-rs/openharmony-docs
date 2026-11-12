# @ohos.hiSysEvent(系统事件打点)

本模块提供了系统事件打点能力，包括系统事件的埋点、落盘系统事件的订阅及已落盘的系统事件的查询能力。可用于系统故障诊断、性能监控、用户行为分析等场景，帮助开发者快速定位和解决问题，提升系统可观测性和运维效率。

**起始版本：** 9

<!--Device-unnamed-declare namespace hiSysEvent--><!--Device-unnamed-declare namespace hiSysEvent-End-->

**系统能力：** SystemCapability.HiviewDFX.HiSysEvent

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { hiSysEvent } from '@kit.PerformanceAnalysisKit';
```

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [addWatcher](arkts-performanceanalysis-hisysevent-addwatcher-f-sys.md#addwatcher-1) | 订阅系统事件，接收[Watcher](arkts-performanceanalysis-hisysevent-watcher-i-sys.md)类型的对象作为事件参数。适用于需要实时监控系统事件的场景。 |
| [exportSysEvents](arkts-performanceanalysis-hisysevent-exportsysevents-f-sys.md#exportsysevents-1) | 批量导出系统事件，以文件格式写入应用沙箱固定目录(/data/storage/el2/base/cache/hiview/event/)。调用成功后，返回接口调用时间戳，可用于定位导出的事件文件。 |
| [query](arkts-performanceanalysis-hisysevent-query-f-sys.md#query-1) | 查询系统事件。支持按时间范围、事件领域、事件名称等多种查询条件进行匹配查询。 |
| [removeWatcher](arkts-performanceanalysis-hisysevent-removewatcher-f-sys.md#removewatcher-1) | 取消订阅系统事件，接收[Watcher](arkts-performanceanalysis-hisysevent-watcher-i-sys.md)类型的对象作为事件参数。适用于当不再需要监控某些事件时取消订阅的场景。取消订阅成功后，将不再接收该订阅者的事件。 |
| [subscribe](arkts-performanceanalysis-hisysevent-subscribe-f-sys.md#subscribe-1) | 订阅实时系统事件(事件需满足低频率或偶发性的约束条件)，事件发生时立即以文件格式写入应用沙箱固定目录(/data/storage/el2/base/cache/hiview/event/)。用于实时监控关键系统事件并进行告警，如性能异常告警、安全事件监控等场景。适用于低频率或偶发性的关键事件，不建议高频事件使用。 |
| [unsubscribe](arkts-performanceanalysis-hisysevent-unsubscribe-f-sys.md#unsubscribe-1) | 取消订阅所有的实时系统事件。取消订阅成功后，将不再接收实时事件。适用于当不再需要订阅实时事件时调用的场景，能够释放订阅资源，减少资源占用。 |
| [write](arkts-performanceanalysis-hisysevent-write-f-sys.md#write-1) | 系统事件打点接口，接收[SysEventInfo](arkts-performanceanalysis-hisysevent-syseventinfo-i-sys.md)类型的对象作为事件参数，使用Promise异步回调。适用于需要链式调用处理异步结果的场景，能够使代码更加简洁优雅。 |
| [write](arkts-performanceanalysis-hisysevent-write-f-sys.md#write-2) | 系统事件打点接口，接收[SysEventInfo](arkts-performanceanalysis-hisysevent-syseventinfo-i-sys.md)类型的对象作为事件参数，使用callback方式作为异步回调。适用于需要异步记录系统事件以避免阻塞主线程的场景，能够提升应用响应性能。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [Querier](arkts-performanceanalysis-hisysevent-querier-i-sys.md) | 系统事件查询者对象接口。 |
| [QueryArg](arkts-performanceanalysis-hisysevent-queryarg-i-sys.md) | 系统事件查询参数对象接口。 |
| [QueryRule](arkts-performanceanalysis-hisysevent-queryrule-i-sys.md) | 系统事件查询规则对象接口。 |
| [SysEventInfo](arkts-performanceanalysis-hisysevent-syseventinfo-i-sys.md) | 系统事件信息对象接口。 |
| [Watcher](arkts-performanceanalysis-hisysevent-watcher-i-sys.md) | 系统事件订阅者对象接口。 |
| [WatchRule](arkts-performanceanalysis-hisysevent-watchrule-i-sys.md) | 系统事件订阅规则对象接口。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [EventType](arkts-performanceanalysis-hisysevent-eventtype-e-sys.md) | 系统事件类型枚举。 |
| [RuleType](arkts-performanceanalysis-hisysevent-ruletype-e-sys.md) | 匹配规则类型枚举。 |
<!--DelEnd-->
