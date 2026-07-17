# Querier（系统接口）

系统事件查询者对象接口。

**起始版本：** 9

<!--Device-hiSysEvent-interface Querier--><!--Device-hiSysEvent-interface Querier-End-->

**系统能力：** SystemCapability.HiviewDFX.HiSysEvent

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { hiSysEvent } from '@kit.PerformanceAnalysisKit';
```

## onComplete

```TypeScript
onComplete: (reason: number, total: number) => void
```

查询结果统计的回调方法(reason: int, total: int) => void。

**类型：** (reason: number, total: number) => void

**起始版本：** 9

<!--Device-Querier-onComplete: (reason: int, total: int) => void--><!--Device-Querier-onComplete: (reason: int, total: int) => void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiSysEvent

**系统接口：** 此接口为系统接口。

## onQuery

```TypeScript
onQuery: (infos: SysEventInfo[]) => void
```

返回查询到的系统事件的回调方法(infos: [SysEventInfo](arkts-performanceanalysis-hisysevent-syseventinfo-i-sys.md)[]) => void。

**类型：** (infos: SysEventInfo[]) => void

**起始版本：** 9

<!--Device-Querier-onQuery: (infos: SysEventInfo[]) => void--><!--Device-Querier-onQuery: (infos: SysEventInfo[]) => void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiSysEvent

**系统接口：** 此接口为系统接口。

