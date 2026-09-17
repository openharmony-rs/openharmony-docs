# QueryArg (System API)

Defines arguments for an event query.

**Since:** 9

**System capability:** SystemCapability.HiviewDFX.HiSysEvent

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { hiSysEvent } from '@kit.PerformanceAnalysisKit';
```

## beginTime

```TypeScript
beginTime: number
```

Start time of the system event to be queried. The value is a 13-digit timestamp, indicating the number of milliseconds elapsed since 00:00:00:00 on January 1, 1970.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.HiviewDFX.HiSysEvent

**System API:** This is a system API.

## endTime

```TypeScript
endTime: number
```

End time of the system event to be queried. The value is a 13-digit timestamp, indicating the number of milliseconds elapsed since 00:00:00:00 on January 1, 1970.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.HiviewDFX.HiSysEvent

**System API:** This is a system API.

## fromSeq

```TypeScript
fromSeq?: number
```

Start SN of the events to be queried. The default value is **-1**

**Type:** number

**Since:** 10

**System capability:** SystemCapability.HiviewDFX.HiSysEvent

**System API:** This is a system API.

## maxEvents

```TypeScript
maxEvents: number
```

Maximum number of events that can be queried.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.HiviewDFX.HiSysEvent

**System API:** This is a system API.

## toSeq

```TypeScript
toSeq?: number
```

End SN of the system events to be queried. The default value is **-1**.

**Type:** number

**Since:** 10

**System capability:** SystemCapability.HiviewDFX.HiSysEvent

**System API:** This is a system API.
