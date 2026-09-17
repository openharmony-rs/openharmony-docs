# deleteId

## Modules to Import

```TypeScript
```

## deleteId

```TypeScript
function deleteId(uri: string): string
```

Deletes the ID from the end of a given URI.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [deleteId](arkts-ability-datauriutils-deleteid-f.md)

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | URI object from which the ID is to be deleted. |

**Return value:**

| Type | Description |
| --- | --- |
| string | URI object with the ID deleted. |

**Examples**

```TypeScript
import dataUriUtils from '@ohos.ability.dataUriUtils';

let uri = dataUriUtils.deleteId('com.example.dataUriUtils/1221');
```
