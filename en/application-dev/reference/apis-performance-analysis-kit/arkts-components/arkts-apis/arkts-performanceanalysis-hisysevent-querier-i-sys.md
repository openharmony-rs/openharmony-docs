# Querier (System API)

Defines an event query instance.

**Since:** 9

**System capability:** SystemCapability.HiviewDFX.HiSysEvent

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { hiSysEvent } from '@kit.PerformanceAnalysisKit';
```

## onComplete

```TypeScript
onComplete: (reason: number, total: number) => void
```

Callback used to return the query result statistics: (reason: int, total: int) =&gt; void

**Since:** 9

**System capability:** SystemCapability.HiviewDFX.HiSysEvent

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| reason | number | Yes |  |
| total | number | Yes |  |

## onQuery

```TypeScript
onQuery: (infos: SysEventInfo[]) => void
```

Callback used to return the queried system events: (infos: [SysEventInfo](arkts-performanceanalysis-hisysevent-syseventinfo-i-sys.md)[]) =&gt; void.

**Since:** 9

**System capability:** SystemCapability.HiviewDFX.HiSysEvent

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| infos | [SysEventInfo](arkts-performanceanalysis-hisysevent-syseventinfo-i-sys.md)[] | Yes |  |
