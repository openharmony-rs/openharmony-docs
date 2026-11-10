# UrgencyLevel

```TypeScript
enum UrgencyLevel
```

Enumerates the urgency level of hint GC.

**Since:** 26.1.0

<!--Device-util-enum UrgencyLevel--><!--Device-util-enum UrgencyLevel-End-->

**System capability:** SystemCapability.Utils.Lang

## HIGH

```TypeScript
HIGH = 2
```

HIGH level, the gc triggering threshold is low. It is suitable for scenarios the ArkTS memory pressure of the application is extremely high, developers expect the system to trigger GC as soon as possible to reclaim memory.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-UrgencyLevel-HIGH = 2--><!--Device-UrgencyLevel-HIGH = 2-End-->

**System capability:** SystemCapability.Utils.Lang

## LOW

```TypeScript
LOW = 0
```

LOW level, GC threshold is relatively high, but GC is still more likely to be triggered than normal memory thresholds. It is suitable for scenarios where the developer expects to proactively trigger GC to reclaim some dead objects, but the ArkTS memory pressure of the application is under control.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-UrgencyLevel-LOW = 0--><!--Device-UrgencyLevel-LOW = 0-End-->

**System capability:** SystemCapability.Utils.Lang

## MEDIUM

```TypeScript
MEDIUM = 1
```

MEDIUM level, The GC triggering threshold is between LOW and HIGH.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-UrgencyLevel-MEDIUM = 1--><!--Device-UrgencyLevel-MEDIUM = 1-End-->

**System capability:** SystemCapability.Utils.Lang
