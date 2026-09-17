# AddressSanitizerPolicy

Defines the address sanitizer event configuration policy.

**Since:** 24

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

## Modules to Import

```TypeScript
import { hiAppEvent } from '@kit.PerformanceAnalysisKit';
```

## pageSwitchLogEnable

```TypeScript
pageSwitchLogEnable?: boolean
```

Whether to enable the page switching log for ADDRESS_SANITIZER event.

**true**: yes.

**false**: no.

The default value is **false**.

Note: The enabling behavior of an application takes effect only in its current lifecycle. In the same lifecycle, the enabling status of the last successful call is used. After the application restarts, you need to set the enabling status again.

**Type:** boolean

**Since:** 24

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.HiviewDFX.HiAppEvent
