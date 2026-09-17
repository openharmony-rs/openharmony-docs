# isCleartextPermittedByHostName

## Modules to Import

```TypeScript
import { networkSecurity } from '@kit.NetworkKit';
```

## isCleartextPermittedByHostName

```TypeScript
export function isCleartextPermittedByHostName(hostName: string): boolean
```

Checks whether host name–based plaintext HTTP access is allowed from the preset **network_config.json** file of the application. By default, plaintext HTTP access is allowed.

**Since:** 18

**Required permissions:** ohos.permission.INTERNET

**System capability:** SystemCapability.Communication.NetStack

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| hostName | string | Yes | Host name. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Boolean value indicating whether host name–based plaintext HTTP is allowed. The value **true** indicates that plaintext HTTP is allowed, and the value **false** indicates the opposite. The default value is **true**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |

**Examples**

```TypeScript
import { networkSecurity } from '@kit.NetworkKit';

try {
  let result: boolean = networkSecurity.isCleartextPermittedByHostName("xxx");
  console.info(`isCleartextPermitted Result: ${JSON.stringify(result)}`);
} catch (error) {
  console.error(`isCleartextPermitted Error: ${JSON.stringify(error)}`);
}
```
