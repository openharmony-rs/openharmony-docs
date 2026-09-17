# Watcher (System API)

Defines a watcher for event subscription.

**Since:** 9

**System capability:** SystemCapability.HiviewDFX.HiSysEvent

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { hiSysEvent } from '@kit.PerformanceAnalysisKit';
```

## onEvent

```TypeScript
onEvent: (info: SysEventInfo) => void
```

Callback for event subscription: (info: [SysEventInfo](arkts-performanceanalysis-hisysevent-syseventinfo-i-sys.md)) =&gt; void

**Since:** 9

**System capability:** SystemCapability.HiviewDFX.HiSysEvent

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| info | [SysEventInfo](arkts-performanceanalysis-hisysevent-syseventinfo-i-sys.md) | Yes |  |

## onServiceDied

```TypeScript
onServiceDied: () => void
```

Callback for disabling of event subscription: () =&gt; void

**Since:** 9

**System capability:** SystemCapability.HiviewDFX.HiSysEvent

**System API:** This is a system API.

## rules

```TypeScript
rules: WatchRule[]
```

Array of matching event subscription rules.

**Type:** [WatchRule](arkts-performanceanalysis-hisysevent-watchrule-i-sys.md)[]

**Since:** 9

**System capability:** SystemCapability.HiviewDFX.HiSysEvent

**System API:** This is a system API.
