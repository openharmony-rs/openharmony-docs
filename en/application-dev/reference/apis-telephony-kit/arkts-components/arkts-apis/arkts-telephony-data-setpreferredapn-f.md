# setPreferredApn

## Modules to Import

```TypeScript
import { data } from '@kit.TelephonyKit';
```

## setPreferredApn

```TypeScript
function setPreferredApn(apnId: number): Promise<boolean>
```

Sets the APN corresponding to the specified **apnId** as the preferred APN. This API returns the result asynchronously.

> **NOTE:** 
> 
> If the input APN ID is invalid, the default preferred APN configured by the carrier is used.

**Since:** 16

**Required permissions:** ohos.permission.MANAGE_APN_SETTING

**System capability:** SystemCapability.Telephony.CellularData

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| apnId | number | Yes | APN ID, which can be obtained by calling [queryApnIds](arkts-telephony-data-queryapnids-f.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. If no SIM card is installed, the value **false** is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |

**Examples**

```TypeScript
import { data } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

let apnId: number = 0; // apnId is a valid value returned by queryApnIds. If an invalid APN ID is passed to setPreferredApn, the default preferred APN configured by the carrier is used.
data.setPreferredApn(apnId).then((result: boolean) => {
    console.info(`setPreferredApn result: ${result}`);
}).catch((err: BusinessError) => {
    console.error(`setPreferredApn failed. code: ${err.code}, message: ${err.message}`);
});
```
