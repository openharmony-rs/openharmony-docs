# deleteProfile (System API)

## Modules to Import

```TypeScript
import { eSIM } from '@kit.TelephonyKit';
```

## deleteProfile

```TypeScript
function deleteProfile(slotId: number, iccid: string): Promise<ResultCode>
```

Delete configuration file. Use Promise asynchronous callback.

**Since:** 18

**Required permissions:** ohos.permission.SET_TELEPHONY_ESIM_STATE

<!--Device-eSIM-function deleteProfile(slotId: int, iccid: string): Promise<ResultCode>--><!--Device-eSIM-function deleteProfile(slotId: int, iccid: string): Promise<ResultCode>-End-->

**System capability:** SystemCapability.Telephony.CoreService.Esim

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| slotId | number | Yes | Card slot ID. <br>The value should be an integer. <br>- **0**: card slot 1. <br>- **1**: card slot 2 |
| iccid | string | Yes | Profile ID. <br>The minimum length is 19 and the maximum length is 20. <br>ID of the configuration file. Generally, the ICCID is a number of 19 to 20 digits. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ResultCode](arkts-telephony-esim-resultcode-e-sys.md)&gt; | Promise used to return the operation result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:         1. Mandatory parameters are left unspecified.         2. Incorrect parameter types.         3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [3120001](../errorcode-telephony.md#3120001-service-connection-error) | Service connection failed. |
| [3120002](../errorcode-telephony.md#3120002-system-internal-error) | System internal error. |

<!--Del-->
**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { eSIM } from '@kit.TelephonyKit';

eSIM.deleteProfile(1, 'testId').then(() => {
    console.info(`deleteProfile invoking succeeded.`);
}).catch((err: BusinessError<void>) => {
    console.error(`deleteProfile, ErrorState: err->${JSON.stringify(err)}`);
});
```

<!--DelEnd-->
