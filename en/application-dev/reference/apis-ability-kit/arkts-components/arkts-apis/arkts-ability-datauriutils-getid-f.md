# getId

## Modules to Import

```TypeScript
import { dataUriUtils } from '@kit.AbilityKit';
```

## getId

```TypeScript
function getId(uri: string): number
```

Obtains the ID attached to the end of a given URI.

**Since:** 9

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | Target URI object. |

**Return value:**

| Type | Description |
| --- | --- |
| number | ID obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
import { dataUriUtils } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let id = dataUriUtils.getId('com.example.dataUriUtils/1221');
  console.info(`get id: ${id}`);
} catch (err) {
  console.error(`get id err, code: ${JSON.stringify((err as BusinessError).code)}, msg: ${JSON.stringify((err as BusinessError).message)}`);
}
```
