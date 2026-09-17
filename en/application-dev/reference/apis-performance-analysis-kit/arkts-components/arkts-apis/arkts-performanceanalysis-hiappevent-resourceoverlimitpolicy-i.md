# ResourceOverlimitPolicy

Defines the resource leak event configuration policy.

**Since:** 24

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

## Modules to Import

```TypeScript
import { hiAppEvent } from '@kit.PerformanceAnalysisKit';
```

## jsHeapLogtype

```TypeScript
jsHeapLogtype?: string
```

The policy for RESOURCE_OVERLIMIT event **event**: No heap snapshot is transferred when an OOM error occurs.

**event_rawheap**: The system generates and transfers a heap snapshot when an OOM error occurs.

**NOTE:** 

- Only the preceding two values are supported. If other values are passed in, the method fails to be called and  
takes no effect.  
- If the parameter value is **event_rawheap**, the heap snapshot file may fail to be generated. This is because  
the application may exit in advance due to a freeze event triggered by a performance problem.

-The enabling behavior of an application takes effect only in its current lifecycle. In the same lifecycle, the enabling status of the last successful call is used. After the application restarts, you need to set the enabling status again.

**Type:** string

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

## pageSwitchLogEnable

```TypeScript
pageSwitchLogEnable?: boolean
```

Whether to enable the page switching log for RESOURCE_OVERLIMIT event.

**true**: yes.

**false**: no.

The default value is **false**.

Note: The enabling behavior of an application takes effect only in its current lifecycle. In the same lifecycle, the enabling status of the last successful call is used. After the application restarts, you need to set the enabling status again.

**Type:** boolean

**Since:** 24

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

## useRefinedLogFileName

```TypeScript
useRefinedLogFileName?: boolean
```

This parameter is used to control whether to output refined external log file names. The default value is false.

**Type:** boolean

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.HiviewDFX.HiAppEvent
