# getAppSharedHeapObjectUsedSize

## Modules to Import

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

## getAppSharedHeapObjectUsedSize

```TypeScript
function getAppSharedHeapObjectUsedSize(): bigint
```

Obtains the memory usage of ArkTS shared heap objects in the virtual machine.

**Since:** 26.1.0

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-hidebug-function getAppSharedHeapObjectUsedSize(): bigint--><!--Device-hidebug-function getAppSharedHeapObjectUsedSize(): bigint-End-->

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**Return value:**

| Type | Description |
| --- | --- |
| bigint | The memory usage of shared heap ArkTS objects, in KB. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [11400104](../errorcode-hiviewdfx-hidebug-cpuusage.md#11400104-abnormal-cpu-usage) | VM instance exception. |
