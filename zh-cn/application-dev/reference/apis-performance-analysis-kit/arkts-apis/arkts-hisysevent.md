# @ohos.hiSysEvent

本模块提供了系统事件打点能力，包括系统事件的埋点、落盘系统事件的订阅及已落盘的系统事件的查询能力。

**起始版本：** 9

**系统能力：** SystemCapability.HiviewDFX.HiSysEvent

**系统接口：** 此接口为系统接口。

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[addWatcher](arkts-performanceanalysis-hisysevent-addwatcher-f-sys.md#addWatcher-1) | 订阅系统事件，接收[Watcher](../../apis-core-file-kit/arkts-apis/arkts-corefile-watcher-i.md#Watcher)类型的对象作为事件参数。<br/> |
| <!--DelRow-->[exportSysEvents](arkts-performanceanalysis-hisysevent-exportsysevents-f-sys.md#exportSysEvents-1) | 批量导出系统事件，以文件格式写入应用沙箱固定目录(/data/storage/el2/base/cache/hiview/event/)。<br/> |
| <!--DelRow-->[query](arkts-performanceanalysis-hisysevent-query-f-sys.md#query-1) | 查询系统事件。<br/> |
| <!--DelRow-->[removeWatcher](arkts-performanceanalysis-hisysevent-removewatcher-f-sys.md#removeWatcher-1) | 取消订阅系统事件，接收[Watcher](../../apis-core-file-kit/arkts-apis/arkts-corefile-watcher-i.md#Watcher)类型的对象作为事件参数。<br/> |
| <!--DelRow-->[subscribe](arkts-performanceanalysis-hisysevent-subscribe-f-sys.md#subscribe-1) | 订阅实时系统事件(事件需满足低频率或偶发性的约束条件)，事件发生时立即以文件格式写入应用沙箱固定目录(/data/storage/el2/base/cache/hiview/event/)。<br/> |
| <!--DelRow-->[unsubscribe](arkts-performanceanalysis-hisysevent-unsubscribe-f-sys.md#unsubscribe-1) | 取消订阅系统事件。<br/> |
| <!--DelRow-->[write](arkts-performanceanalysis-hisysevent-write-f-sys.md#write-1) | 系统事件打点方法，接收[SysEventInfo](SysEventInfo)类型的对象作为事件参数，使用promise方式作为异步回调。<br/> |
| <!--DelRow-->[write](arkts-performanceanalysis-hisysevent-write-f-sys.md#write-2) | 系统事件打点方法，接收[SysEventInfo](SysEventInfo)类型的对象作为事件参数，使用callback方式作为异步回调。<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[Querier](arkts-performanceanalysis-hisysevent-querier-i-sys.md) | 系统事件查询者对象接口。<br/> |
| <!--DelRow-->[QueryArg](arkts-performanceanalysis-hisysevent-queryarg-i-sys.md) | 系统事件查询参数对象接口。<br/> |
| <!--DelRow-->[QueryRule](arkts-performanceanalysis-hisysevent-queryrule-i-sys.md) | 系统事件查询规则对象接口。<br/> |
| <!--DelRow-->[SysEventInfo](arkts-performanceanalysis-hisysevent-syseventinfo-i-sys.md) | 系统事件信息对象接口。<br/> |
| <!--DelRow-->[WatchRule](arkts-performanceanalysis-hisysevent-watchrule-i-sys.md) | 系统事件订阅规则对象接口。<br/> |
| <!--DelRow-->[Watcher](arkts-performanceanalysis-hisysevent-watcher-i-sys.md) | 系统事件订阅者对象接口。<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[EventType](arkts-performanceanalysis-hisysevent-eventtype-e-sys.md) | 系统事件类型枚举。<br/> |
| <!--DelRow-->[RuleType](arkts-performanceanalysis-hisysevent-ruletype-e-sys.md) | 匹配规则类型枚举。<br/> |

