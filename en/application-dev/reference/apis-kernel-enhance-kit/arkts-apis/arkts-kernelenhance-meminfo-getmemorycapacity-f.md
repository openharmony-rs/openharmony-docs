# getMemoryCapacity

## Modules to Import

```TypeScript
import { meminfo } from '@kit.KernelEnhanceKit';
```

## getMemoryCapacity

```TypeScript
function getMemoryCapacity(): number
```

Obtain the total memory capacity of the system.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-meminfo-function getMemoryCapacity(): int--><!--Device-meminfo-function getMemoryCapacity(): int-End-->

**System capability:** SystemCapability.Kernel.Memory

**Return value:**

| Type | Description |
| --- | --- |
| number | Total memory capacity, in MB. If it does not exist, 0 is returned. |
