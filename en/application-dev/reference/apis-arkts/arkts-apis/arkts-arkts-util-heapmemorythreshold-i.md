# HeapMemoryThreshold

```TypeScript
interface HeapMemoryThreshold
```

Describes the heap memory threshold at which the registered callback is triggered after a GC.

@interface HeapMemoryThreshold

**Since:** 24

<!--Device-util-interface HeapMemoryThreshold--><!--Device-util-interface HeapMemoryThreshold-End-->

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { util } from '@kit.ArkTS';
```

## localHeapThreshold

```TypeScript
localHeapThreshold?: number
```

This number is on a scale of 70 to 95, representing the percentage threshold of the local heap memory at which the callback is triggered after a GC. Values outside this range are automatically clamped to the valid range. If not set, the callback will not be triggered by local heap memory pressure.

**Type:** number

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-HeapMemoryThreshold-localHeapThreshold?: number--><!--Device-HeapMemoryThreshold-localHeapThreshold?: number-End-->

**System capability:** SystemCapability.Utils.Lang

## processHeapThreshold

```TypeScript
processHeapThreshold?: number
```

This number is on a scale of 70 to 95, representing the percentage threshold of the process's total heap memory at which the callback is triggered after a GC. Values outside this range are automatically clamped to the valid range. If not set, the callback will not be triggered by process heap memory pressure.

**Type:** number

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-HeapMemoryThreshold-processHeapThreshold?: number--><!--Device-HeapMemoryThreshold-processHeapThreshold?: number-End-->

**System capability:** SystemCapability.Utils.Lang

## sharedHeapThreshold

```TypeScript
sharedHeapThreshold?: number
```

This number is on a scale of 70 to 95, representing the percentage threshold of the shared heap memory at which the callback is triggered after a GC. Values outside this range are automatically clamped to the valid range. If not set, the callback will not be triggered by shared heap memory pressure.

**Type:** number

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-HeapMemoryThreshold-sharedHeapThreshold?: number--><!--Device-HeapMemoryThreshold-sharedHeapThreshold?: number-End-->

**System capability:** SystemCapability.Utils.Lang
