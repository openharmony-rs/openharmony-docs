# hasCallSync

## Modules to Import

```TypeScript
import { call } from '@kit.TelephonyKit';
```

## hasCallSync

```TypeScript
function hasCallSync(): boolean
```

Checks whether a call is in progress.

**Since:** 10

**System capability:** SystemCapability.Telephony.CallManager

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Promise used to return the result. The value **true** indicates that a call is in progress, and the value **false** indicates the opposite. |

**Examples**

```TypeScript
let hasCall: boolean = call.hasCallSync();
console.info(`hasCallSync success, has call is ` + hasCall);
```
