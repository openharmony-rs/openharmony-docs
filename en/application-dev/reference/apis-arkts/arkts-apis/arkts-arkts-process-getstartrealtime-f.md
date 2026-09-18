# getStartRealtime

## Modules to Import

```TypeScript
import { process } from '@kit.ArkTS';
```

## getStartRealtime

```TypeScript
function getStartRealtime(): number
```

Obtains the duration (excluding the system sleep time), in milliseconds, from the time the system starts to the time the process starts.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| number | Duration obtained, in milliseconds. |

**Examples**

```TypeScript
let realtime = process.getStartRealtime();
```
