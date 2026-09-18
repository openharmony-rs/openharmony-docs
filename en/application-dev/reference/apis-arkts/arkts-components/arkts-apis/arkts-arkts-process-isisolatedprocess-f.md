# isIsolatedProcess

## Modules to Import

```TypeScript
import { process } from '@kit.ArkTS';
```

## isIsolatedProcess

```TypeScript
function isIsolatedProcess(): boolean
```

Checks whether this process is isolated.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if the process is isolated; otherwise, **false** is returned. |

**Examples**

```TypeScript
let result = process.isIsolatedProcess();
```
