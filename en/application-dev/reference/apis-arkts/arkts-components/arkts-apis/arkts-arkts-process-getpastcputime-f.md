# getPastCpuTime

## Modules to Import

```TypeScript
import { process } from '@kit.ArkTS';
```

## getPastCpuTime

```TypeScript
function getPastCpuTime(): number
```

Obtains the CPU time (in milliseconds) from the time the process starts to the current time.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| number | CPU time obtained, in milliseconds. |

**Examples**

```TypeScript
let result = process.getPastCpuTime();
```
