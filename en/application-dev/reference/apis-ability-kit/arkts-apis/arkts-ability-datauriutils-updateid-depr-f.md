# updateId

## Modules to Import

```TypeScript
```

## updateId

```TypeScript
function updateId(uri: string, id: number): string
```

Updates the ID in a given URI.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [updateId](arkts-ability-datauriutils-updateid-f.md)

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | Target URI object. |
| id | number | Yes | New ID. |

**Return value:**

| Type | Description |
| --- | --- |
| string | URI object with the new ID. |

**Examples**

```TypeScript
import dataUriUtils from '@ohos.ability.dataUriUtils';

let id = 1122;
let uri = dataUriUtils.updateId(
    'com.example.dataUriUtils/1221',
	id
);
```
