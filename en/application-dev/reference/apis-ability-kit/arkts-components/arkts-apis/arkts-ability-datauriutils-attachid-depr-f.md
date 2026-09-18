# attachId

## Modules to Import

```TypeScript
```

## attachId

```TypeScript
function attachId(uri: string, id: number): string
```

Attaches an ID to the end of a given URI.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [attachId](arkts-ability-datauriutils-attachid-f.md)

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | Target URI object. |
| id | number | Yes | ID to be attached. |

**Return value:**

| Type | Description |
| --- | --- |
| string | URI object with the ID attached. |

**Examples**

```TypeScript
import dataUriUtils from '@ohos.ability.dataUriUtils';

let id = 1122;
let uri = dataUriUtils.attachId(
    'com.example.dataUriUtils',
	id,
);
```
