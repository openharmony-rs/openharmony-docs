# uptime

## Modules to Import

```TypeScript
import { process } from '@kit.ArkTS';
```

## uptime

```TypeScript
function uptime(): number
```

Obtains the running time of the current system, in seconds.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-process-function uptime(): number--><!--Device-process-function uptime(): number-End-->

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| number | Running time of the system, in seconds. |

**Examples**

```TypeScript
let time = process.uptime();
```
