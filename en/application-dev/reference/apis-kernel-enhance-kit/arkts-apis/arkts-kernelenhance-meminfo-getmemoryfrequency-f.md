# getMemoryFrequency

## Modules to Import

```TypeScript
import { meminfo } from '@kit.KernelEnhanceKit';
```

## getMemoryFrequency

```TypeScript
function getMemoryFrequency(): number
```

Obtain the memory frequency.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-meminfo-function getMemoryFrequency(): int--><!--Device-meminfo-function getMemoryFrequency(): int-End-->

**System capability:** SystemCapability.Kernel.Memory

**Return value:**

| Type | Description |
| --- | --- |
| number | Memory frequency, in MHz. If it does not exist, 0 is returned. |
