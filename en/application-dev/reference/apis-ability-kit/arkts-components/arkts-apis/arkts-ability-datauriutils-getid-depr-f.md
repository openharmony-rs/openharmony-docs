# getId

## Modules to Import

```TypeScript
```

## getId

```TypeScript
function getId(uri: string): number
```

Obtains the ID attached to the end of a given URI.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getId](arkts-ability-datauriutils-getid-f.md)

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | Target URI object. |

**Return value:**

| Type | Description |
| --- | --- |
| number | ID obtained. |

**Examples**

```TypeScript
import dataUriUtils from '@ohos.ability.dataUriUtils';

let id = dataUriUtils.getId('com.example.dataUriUtils/1221');
```
