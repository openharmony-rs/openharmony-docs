# Watcher（系统接口）

```TypeScript
interface Watcher
```

系统事件订阅者对象接口。

**起始版本：** 9

<!--Device-hiSysEvent-interface Watcher--><!--Device-hiSysEvent-interface Watcher-End-->

**系统能力：** SystemCapability.HiviewDFX.HiSysEvent

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { hiSysEvent } from '@kit.PerformanceAnalysisKit';
```

## onEvent

```TypeScript
onEvent: (info: SysEventInfo) => void
```

订阅事件的回调方法(info: [SysEventInfo](arkts-performanceanalysis-hisysevent-syseventinfo-i-sys.md)) =&gt; void。当订阅的事件发生时此回调方法会被触发，回调函数接收订阅到的[SysEventInfo](arkts-performanceanalysis-hisysevent-syseventinfo-i-sys.md)，用于处理订阅到的事件数据。

**起始版本：** 9

<!--Device-Watcher-onEvent: (info: SysEventInfo) => void--><!--Device-Watcher-onEvent: (info: SysEventInfo) => void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiSysEvent

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | [SysEventInfo](arkts-performanceanalysis-hisysevent-syseventinfo-i-sys.md) | 是 |  |

## onServiceDied

```TypeScript
onServiceDied: () => void
```

系统事件服务关闭的回调方法() =&gt; void。当系统事件服务异常关闭或停止时触发，用于处理服务异常情况（如记录日志、重新订阅事件等）。

**起始版本：** 9

<!--Device-Watcher-onServiceDied: () => void--><!--Device-Watcher-onServiceDied: () => void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiSysEvent

**系统接口：** 此接口为系统接口。

## rules

```TypeScript
rules: WatchRule[]
```

订阅对象数组，每个订阅者对象包含多个订阅规则。

**类型：** [WatchRule](arkts-performanceanalysis-hisysevent-watchrule-i-sys.md)[]

**起始版本：** 9

<!--Device-Watcher-rules: WatchRule[]--><!--Device-Watcher-rules: WatchRule[]-End-->

**系统能力：** SystemCapability.HiviewDFX.HiSysEvent

**系统接口：** 此接口为系统接口。
