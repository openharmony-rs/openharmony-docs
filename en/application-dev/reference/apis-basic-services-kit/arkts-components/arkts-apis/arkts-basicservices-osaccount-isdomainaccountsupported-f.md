# isDomainAccountSupported

## Modules to Import

```TypeScript
import { osAccount } from '@kit.BasicServicesKit';
```

## isDomainAccountSupported

```TypeScript
function isDomainAccountSupported(): Promise<boolean>
```

Checks whether this domain account is supported. This API uses a promise to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Account.OsAccount

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** means this domain account is supported; the value **false** means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  osAccount.isDomainAccountSupported().then((isSupported: boolean) => {
    console.info('isDomainAccountSupported successfully, isSupported: ' + isSupported);
  }).catch((err: BusinessError) => {
    console.error(`isDomainAccountSupported failed, code is ${err.code}, message is: ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`isDomainAccountSupported exception: code is ${err.code}, message is ${err.message}`);
}
```
