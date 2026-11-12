# Querier（系统接口）

```TypeScript
interface Querier
```

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

查询结果统计的回调方法(reason: int, total: int) =&gt; void。当查询完成时触发（只调用一次），回调函数接收查询结果统计信息：reason表示查询完成的原因（如查询成功、查询超时等），total表示查询到的总事件数。

**起始版本：** 9

<!--Device-Querier-onComplete: (reason: int, total: int) => void--><!--Device-Querier-onComplete: (reason: int, total: int) => void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiSysEvent

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| reason | number | 是 |  |
| total | number | 是 |  |

## onQuery

```TypeScript
onQuery: (infos: SysEventInfo[]) => void
```

返回查询到的系统事件的回调方法(infos: [SysEventInfo](arkts-performanceanalysis-hisysevent-syseventinfo-i-sys.md)[]) =&gt; void。当查询到系统事件时触发（可能调用多次），回调函数接收查询到的[SysEventInfo](arkts-performanceanalysis-hisysevent-syseventinfo-i-sys.md)数组，用于处理查询结果。

**起始版本：** 9

<!--Device-Querier-onQuery: (infos: SysEventInfo[]) => void--><!--Device-Querier-onQuery: (infos: SysEventInfo[]) => void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiSysEvent

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| infos | [SysEventInfo](arkts-performanceanalysis-hisysevent-syseventinfo-i-sys.md)[] | 是 |  |
