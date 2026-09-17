# queryAllApns

## Modules to Import

```TypeScript
import { data } from '@kit.TelephonyKit';
```

## queryAllApns

```TypeScript
function queryAllApns(): Promise<Array<ApnInfo>>
```

Obtains the access point name (APN) of the default SIM card used for mobile data. This API returns the result asynchronously.

**Since:** 16

**Required permissions:** ohos.permission.MANAGE_APN_SETTING

**System capability:** SystemCapability.Telephony.CellularData

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[ApnInfo](arkts-telephony-data-apninfo-i.md)&gt;&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |

**Examples**

```TypeScript
import { data } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

data.queryAllApns().then((apnInfos: Array<data.ApnInfo>) => {
    console.info(`queryAllApns success, promise: apnInfos->${JSON.stringify(apnInfos)}`);
}).catch((err: BusinessError) => {
    console.error(`queryAllApns failed. code: ${err.code}, message: ${err.message}`);
});
```
