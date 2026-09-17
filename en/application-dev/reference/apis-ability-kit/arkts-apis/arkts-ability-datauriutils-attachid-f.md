# attachId

## Modules to Import

```TypeScript
import { dataUriUtils } from '@kit.AbilityKit';
```

## attachId

```TypeScript
function attachId(uri: string, id: number): string
```

Attaches an ID to the end of a given URI.

**Since:** 9

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

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
import { dataUriUtils } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let id = 1122;
try {
  let uri = dataUriUtils.attachId(
    'com.example.dataUriUtils',
    id,
  );
  console.info(`attachId the uri is: ${uri}`);
} catch (err) {
  console.error(`attachId err, code: ${JSON.stringify((err as BusinessError).code)}, msg: ${JSON.stringify((err as BusinessError).message)}`);
}
```
