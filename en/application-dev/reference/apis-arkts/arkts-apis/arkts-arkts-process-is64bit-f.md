# is64Bit

## Modules to Import

```TypeScript
import { process } from '@kit.ArkTS';
```

## is64Bit

```TypeScript
function is64Bit(): boolean
```

Checks whether this process is running in a 64-bit environment.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** is returned if the process is running in a 64-bit environment; otherwise, **false** is returned. |

**Examples**

```TypeScript
let result = process.is64Bit();
```
