# AppCrashPolicy

Defines the application crash event configuration policy.

**Since:** 24

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

## Modules to Import

```TypeScript
import { hiAppEvent } from '@kit.PerformanceAnalysisKit';
```

## collectMinidump

```TypeScript
collectMinidump?: boolean
```

Policy for the APP_CRASH event the value true means to the minidump capture capability is enabled. the value false means to the minidump capture function is disabled. <br>Default value:false.

**Type:** boolean

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

## extendPcLrPrinting

```TypeScript
extendPcLrPrinting?: boolean
```

The policy for APP_CRASH event. Whether to print the memory values before and after the PC and LR registers in crash logs. The value **true** means to print the memory values of 248 bytes before and 256 bytes after the PC and LR on 64- bit system, or 124 bytes before and 128 bytes after on 32-bit systems.

The value **false** means to print the memory values of 16 bytes before and 232 bytes after the PC and LR on 64- bit system, or 8 bytes before and 116 bytes after on 32-bit systems.

The default value is **false**.

**Type:** boolean

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

## logFileCutoffSzBytes

```TypeScript
logFileCutoffSzBytes?: number
```

The policy for APP_CRASH event. Truncation size for crash logs. The value ranges from 0 to 5242880, in bytes. The default value is 0, indicating that crash logs are not truncated.

**Type:** number

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

## pageSwitchLogEnable

```TypeScript
pageSwitchLogEnable?: boolean
```

Whether to enable the page switching log for APP_CRASH event.

**true**: yes.

**false**: no.

The default value is **false**.

Note: The enabling behavior of an application takes effect only in its current lifecycle. In the same lifecycle, the enabling status of the last successful call is used. After the application restarts, you need to set the enabling status again.

**Type:** boolean

**Since:** 24

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

## simplifyVmaPrinting

```TypeScript
simplifyVmaPrinting?: boolean
```

The policy for APP_CRASH event. Whether to print the mapping information of all virtual memory areas (VMAs) in the crash log, that is, the **Maps** field in the crash log.

The value **true** means to print only the VMA mapping information of the addresses in the crash log to reduce the log size.

The value **false** means to print all VMA mapping information.

The default value is **false**.

**Type:** boolean

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.HiviewDFX.HiAppEvent
