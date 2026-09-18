# getUidForName

## Modules to Import

```TypeScript
import { process } from '@kit.ArkTS';
```

## getUidForName

```TypeScript
function getUidForName(v: string): number
```

Obtains the UID of a user from the user database of the system based on the specified user name.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getUidForName](arkts-arkts-process-processmanager-c.md#getuidforname)

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| v | string | Yes | User name. |

**Return value:**

| Type | Description |
| --- | --- |
| number | UID of the user. |

**Examples**

```TypeScript
let pres = process.getUidForName("tool");
```
