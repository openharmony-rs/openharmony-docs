# getActiveApnName

## Modules to Import

```TypeScript
import { data } from '@kit.TelephonyKit';
```

## getActiveApnName

```TypeScript
function getActiveApnName(): Promise<string>
```

Obtains the access point name (APN) of the default SIM card used for mobile data. This API returns the result asynchronously.

**Required permission**: ohos.permission.GET_NETWORK_INFO

**Since:** 20

**Required permissions:** ohos.permission.GET_NETWORK_INFO

**System capability:** SystemCapability.Telephony.CellularData

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the result. If mobile data is not activated, an empty string is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |

**Examples**

```TypeScript
import { data } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

data.getActiveApnName().then((apn: string) => {
    console.info(`getActiveApnName success, apn: ${apn}`);
}).catch((err: BusinessError) => {
    console.error(`getActiveApnName failed. code: ${err.code}, message: ${err.message}`);
});
```
