# getMainThreadStackTrace

## Modules to Import

```TypeScript
import { util } from '@kit.ArkTS';
```

## getMainThreadStackTrace

```TypeScript
function getMainThreadStackTrace(): string
```

Obtains the stack trace information of the main thread. A maximum of 64 call frames can be returned. This API may affect the performance of the main thread. You are advised to use this API only when necessary, such as in log recording, error analysis, or debugging scenarios.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| string | Stack trace information of the main thread. If the main thread is not executing JavaScript code, an empty string is returned. |

**Examples**

```TypeScript
let stack = util.getMainThreadStackTrace();
console.info(stack);
// Obtain the stack trace information of the main thread.
```
