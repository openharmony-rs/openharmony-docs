# MainThreadJankPolicy

```TypeScript
interface MainThreadJankPolicy
```

Defines the configuration policy for the main thread jank event.

**Since:** 22

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

## Modules to Import

```TypeScript
import { hiAppEvent } from '@kit.PerformanceAnalysisKit';
```

## autoStopSampling

```TypeScript
autoStopSampling?: boolean
```

Whether to automatically stop sampling the main thread stack when the main thread jank event ends.

The value **true** means to stop sampling when the main thread jank event ends or the number of samplings reaches the specified value.

The value **false** means to stop sampling when the number of samplings reaches the specified value.

The default value is **false**.

**Type:** boolean

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

## ignoreStartupTime

```TypeScript
ignoreStartupTime?: number
```

Mainthread jank event detection time ignored during application startup, in seconds. The default value is **10**, and the minimum value is **3**.

**Type:** number

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

## logType

```TypeScript
logType?: number
```

Type of logs to collect. Default value: **0**

**logType = 0**: The default values of other parameters are used. When the main thread experiences two consecutive timeouts between 150 ms and 450 ms, a call stack capture is triggered. When the timeout exceeds 450 ms, a trace capture is triggered.

**logType=1**: Only the call stack is captured, and the threshold for triggering the detection is customized.

**logType=2**: Only traces are captured.

**NOTE:** 

- When **logType** is set to **0**, you only need to set **autoStopSampling**. Default values are used for other  
parameters.  
- When **logType** is set to **2**, other parameters do not take effect and do not need to be set.

**Type:** number

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

## reportTimesPerApp

```TypeScript
reportTimesPerApp?: number
```

Number of sampling reporting times for the main thread jank event of the processes with the same PID of an application. This parameter can be set only once for the processes with the same PID.

The default value is **1**, Unit: times.

The number of times that the sampling is reported per minute ranges from 1 to 3.

**Type:** number

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

## sampleCount

```TypeScript
sampleCount?: number
```

Number of samplings for the main thread jank event. Unit: times. The default value is **10**. The minimum

value is 1. The maximum value is calculated using the following formula:

**sampleCount** = (2500/**sampleInterval** - 4).

**NOTE:** 

- The value **2500** (ms) indicates the maximum time allowed for a main thread jank event to be reported after  
being detected. Therefore, the value of **sampleCount** cannot be greater than the maximum value calculated based on the formula.  
- The value **4** indicates the number of check intervals, that is, the first check interval, the twice second  
check intervals, and the interval for collecting and reporting stack information.  
- You need to set the parameters as required.

**Type:** number

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

## sampleInterval

```TypeScript
sampleInterval?: number
```

Interval for the main thread jank event detection and sampling, in milliseconds. The default value is **150**. The value range is [50, 500].

**Type:** number

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.HiviewDFX.HiAppEvent
