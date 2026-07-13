# @ohos.hiSysEvent

本模块提供了系统事件打点能力，包括系统事件的埋点、落盘系统事件的订阅及已落盘的系统事件的查询能力。

**起始版本：** 9

**系统能力：** SystemCapability.HiviewDFX.HiSysEvent

**系统接口：** 此接口为系统接口。

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [addWatcher](arkts-performanceanalysis-addwatcher-f-sys.md#addwatcher-1) | 订阅系统事件，接收[Watcher](../../apis-core-file-kit/arkts-apis/arkts-corefile-watcher-i.md)类型的对象作为事件参数。 |
| [exportSysEvents](arkts-performanceanalysis-exportsysevents-f-sys.md#exportsysevents-1) | 批量导出系统事件，以文件格式写入应用沙箱固定目录(/data/storage/el2/base/cache/hiview/event/)。 |
| [query](arkts-performanceanalysis-query-f-sys.md#query-1) | 查询系统事件。 |
| [removeWatcher](arkts-performanceanalysis-removewatcher-f-sys.md#removewatcher-1) | 取消订阅系统事件，接收[Watcher](../../apis-core-file-kit/arkts-apis/arkts-corefile-watcher-i.md)类型的对象作为事件参数。 |
| [subscribe](arkts-performanceanalysis-subscribe-f-sys.md#subscribe-1) | 订阅实时系统事件(事件需满足低频率或偶发性的约束条件)，事件发生时立即以文件格式写入应用沙箱固定目录(/data/storage/el2/base/cache/hiview/event/)。 |
| [unsubscribe](arkts-performanceanalysis-unsubscribe-f-sys.md#unsubscribe-1) | 取消订阅系统事件。 |
| [write](arkts-performanceanalysis-write-f-sys.md#write-1) | 系统事件打点方法，接收[SysEventInfo](SysEventInfo)类型的对象作为事件参数，使用promise方式作为异步回调。 |
| [write](arkts-performanceanalysis-write-f-sys.md#write-2) | 系统事件打点方法，接收[SysEventInfo](SysEventInfo)类型的对象作为事件参数，使用callback方式作为异步回调。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [Querier](arkts-performanceanalysis-querier-i-sys.md) | 系统事件查询者对象接口。 |
| [QueryArg](arkts-performanceanalysis-queryarg-i-sys.md) | 系统事件查询参数对象接口。 |
| [QueryRule](arkts-performanceanalysis-queryrule-i-sys.md) | 系统事件查询规则对象接口。 |
| [SysEventInfo](arkts-performanceanalysis-syseventinfo-i-sys.md) | 系统事件信息对象接口。 |
| [WatchRule](arkts-performanceanalysis-watchrule-i-sys.md) | 系统事件订阅规则对象接口。 |
| [Watcher](arkts-performanceanalysis-watcher-i-sys.md) | 系统事件订阅者对象接口。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [EventType](arkts-performanceanalysis-eventtype-e-sys.md) | 系统事件类型枚举。 |
| [RuleType](arkts-performanceanalysis-ruletype-e-sys.md) | 匹配规则类型枚举。 |
<!--DelEnd-->

