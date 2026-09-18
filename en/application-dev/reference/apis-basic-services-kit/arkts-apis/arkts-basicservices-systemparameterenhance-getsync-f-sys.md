# getSync (System API)

## Modules to Import

```TypeScript
import { systemParameterEnhance } from '@kit.BasicServicesKit';
```

## getSync

```TypeScript
function getSync(key: string, def?: string): string
```

Obtains a value of the specified key. This API uses a promise to return the result.

**Since:** 9

**System capability:** SystemCapability.Startup.SystemInfo

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes | Key to be queried. The value can contain a maximum of 128 bytes. Only letters, digits, periods (.), hyphens (-), at signs (@), colons (:), and underscores (_) are allowed. |
| def | string | No | Default value of the system parameter.<br> It works only when the system parameter does not exist.<br> The value can be **undefined** or any custom value. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Value of the system parameter.<br> If the specified key exists, the set value is returned. <br> If the specified key does not exist and **def** is set to a valid value, the set value is returned. If the specified key does not exist and **def** is set to an invalid value (such as **undefined**) or is not set, an exception is thrown. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.incorrect parameter types; 3.parameter verification failed. |
| [14700101](../errorcode-system-parameterV9.md#14700101-failure-to-query-the-system-parameter) | System parameter not found. |
| [14700103](../errorcode-device-info.md#14700103-operation-denied-due-to-permission) | The operation on the system permission is denied. |
| [14700104](../errorcode-system-parameterV9.md#14700104-internal-system-error-including-out-of-memory-and-deadlock) | System internal error such as out memory or deadlock. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let info: string = systemParameterEnhance.getSync('const.ohos.apiversion');
  console.info('getSync result: ' + info);
} catch (e) {
  console.error(`getSync failed. Code: ${(e as BusinessError).code}, message: ${(e as BusinessError).message}`);
}
```
