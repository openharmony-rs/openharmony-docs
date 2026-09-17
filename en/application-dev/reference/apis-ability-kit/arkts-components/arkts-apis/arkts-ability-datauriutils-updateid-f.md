# updateId

## Modules to Import

```TypeScript
import { dataUriUtils } from '@kit.AbilityKit';
```

## updateId

```TypeScript
function updateId(uri: string, id: number): string
```

Updates the ID in a given URI.

**Since:** 9

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

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
import { dataUriUtils } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let id = 1122;
  let uri = dataUriUtils.updateId(
    'com.example.dataUriUtils/1221',
    id
  );
  console.info(`update id with the uri is: ${uri}`);
} catch (err) {
  console.error(`update id err, code: ${JSON.stringify((err as BusinessError).code)}, msg: ${JSON.stringify((err as BusinessError).message)}`);
}
```
