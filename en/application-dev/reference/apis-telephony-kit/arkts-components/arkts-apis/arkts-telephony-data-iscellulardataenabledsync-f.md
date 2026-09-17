# isCellularDataEnabledSync

## Modules to Import

```TypeScript
import { data } from '@kit.TelephonyKit';
```

## isCellularDataEnabledSync

```TypeScript
function isCellularDataEnabledSync(): boolean
```

Checks whether the cellular data service is enabled. This API returns the result synchronously.

**Required permission**: ohos.permission.GET_NETWORK_INFO

**Since:** 12

**Required permissions:** ohos.permission.GET_NETWORK_INFO

**System capability:** SystemCapability.Telephony.CellularData

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the cellular data service is enabled.<br>**true**: The cellular data service is enabled. <br>**false**: The cellular data service is disabled. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [8300002](../errorcode-telephony.md#8300002-service-connection-error) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-system-internal-error) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-internal-error) | Unknown error code. |

**Examples**

```TypeScript
import { data } from '@kit.TelephonyKit';

try {
    let isEnabled: boolean = data.isCellularDataEnabledSync();
    console.info(`isCellularDataEnabledSync success : ${isEnabled}`);
} catch (err) {
    console.error(`isCellularDataEnabledSync fail. code: ${err.code}, message: ${err.message}`);  
}
```
