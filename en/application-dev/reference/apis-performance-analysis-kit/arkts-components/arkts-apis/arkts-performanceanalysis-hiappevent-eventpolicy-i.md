# EventPolicy

```TypeScript
interface EventPolicy
```

Defines the system event configuration policy, which is set by calling [configEventPolicy](arkts-performanceanalysis-hiappevent-configeventpolicy-f.md).

**Since:** 22

<!--Device-hiAppEvent-interface EventPolicy--><!--Device-hiAppEvent-interface EventPolicy-End-->

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

## Modules to Import

```TypeScript
import { hiAppEvent } from '@kit.PerformanceAnalysisKit';
```

## addressSanitizerPolicy

```TypeScript
addressSanitizerPolicy?: AddressSanitizerPolicy
```

ADDRESS_SANITIZER event configuration policy.

**Type:** [AddressSanitizerPolicy](arkts-performanceanalysis-hiappevent-addresssanitizerpolicy-i.md)

**Since:** 24

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 24.

<!--Device-EventPolicy-addressSanitizerPolicy?: AddressSanitizerPolicy--><!--Device-EventPolicy-addressSanitizerPolicy?: AddressSanitizerPolicy-End-->

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

## appCrashPolicy

```TypeScript
appCrashPolicy?: AppCrashPolicy
```

APP_CRASH event configuration policy.

**Type:** [AppCrashPolicy](arkts-performanceanalysis-hiappevent-appcrashpolicy-i.md)

**Since:** 24

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 24.

<!--Device-EventPolicy-appCrashPolicy?: AppCrashPolicy--><!--Device-EventPolicy-appCrashPolicy?: AppCrashPolicy-End-->

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

## appFreezePolicy

```TypeScript
appFreezePolicy?: AppFreezePolicy
```

APP_FREEZE event configuration policy.

**Type:** [AppFreezePolicy](arkts-performanceanalysis-hiappevent-appfreezepolicy-i.md)

**Since:** 24

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 24.

<!--Device-EventPolicy-appFreezePolicy?: AppFreezePolicy--><!--Device-EventPolicy-appFreezePolicy?: AppFreezePolicy-End-->

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

## cpuUsageHighPolicy

```TypeScript
cpuUsageHighPolicy?: CpuUsageHighPolicy
```

Configuration policy for CPU_USAGE_HIGH event.

**Type:** [CpuUsageHighPolicy](arkts-performanceanalysis-hiappevent-cpuusagehighpolicy-i.md)

**Since:** 22

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 22.

<!--Device-EventPolicy-cpuUsageHighPolicy?: CpuUsageHighPolicy--><!--Device-EventPolicy-cpuUsageHighPolicy?: CpuUsageHighPolicy-End-->

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

## mainThreadJankPolicy

```TypeScript
mainThreadJankPolicy?: MainThreadJankPolicy
```

Configuration policy for MAIN_THREAD_JANK event.

**Type:** [MainThreadJankPolicy](arkts-performanceanalysis-hiappevent-mainthreadjankpolicy-i.md)

**Since:** 22

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 22.

<!--Device-EventPolicy-mainThreadJankPolicy?: MainThreadJankPolicy--><!--Device-EventPolicy-mainThreadJankPolicy?: MainThreadJankPolicy-End-->

**System capability:** SystemCapability.HiviewDFX.HiAppEvent

## resourceOverlimitPolicy

```TypeScript
resourceOverlimitPolicy?: ResourceOverlimitPolicy
```

RESOURCE_OVERLIMIT event configuration policy.

**Type:** [ResourceOverlimitPolicy](arkts-performanceanalysis-hiappevent-resourceoverlimitpolicy-i.md)

**Since:** 24

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 24.

<!--Device-EventPolicy-resourceOverlimitPolicy?: ResourceOverlimitPolicy--><!--Device-EventPolicy-resourceOverlimitPolicy?: ResourceOverlimitPolicy-End-->

**System capability:** SystemCapability.HiviewDFX.HiAppEvent
