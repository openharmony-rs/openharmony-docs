# AppFreezePolicy

```TypeScript
interface AppFreezePolicy
```

Defines the application freeze event configuration policy.

**Since:** 24

<!--Device-hiAppEvent-interface AppFreezePolicy--><!--Device-hiAppEvent-interface AppFreezePolicy-End-->

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

## Modules to Import

```TypeScript
import { hiAppEvent } from '@kit.PerformanceAnalysisKit';
```

## pageSwitchLogEnable

```TypeScript
pageSwitchLogEnable?: boolean
```

Whether to enable the page switching log for APP_FREEZE event.

**true**: yes.

**false**: no.

The default value is **false**.

Note: The enabling behavior of an application takes effect only in its current lifecycle. In the same lifecycle, the enabling status of the last successful call is used. After the application restarts, you need to set the enabling status again.

**Type:** boolean

**Since:** 24

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 24.

<!--Device-AppFreezePolicy-pageSwitchLogEnable?: boolean--><!--Device-AppFreezePolicy-pageSwitchLogEnable?: boolean-End-->

**System capability:** SystemCapability.HiviewDFX.HiAppEvent
