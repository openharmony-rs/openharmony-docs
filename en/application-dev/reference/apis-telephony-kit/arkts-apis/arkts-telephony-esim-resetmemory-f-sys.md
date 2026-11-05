# resetMemory (System API)

## Modules to Import

```TypeScript
import { eSIM } from '@kit.TelephonyKit';
```

## resetMemory

```TypeScript
function resetMemory(slotId: number, options?:ResetOption): Promise<ResultCode>
```

Clear all specific profiles and reset the eUICC. Different from reserveProfilesForFactoryRestore, this interface clears configuration files. To restore factory settings and retain existing configuration files, use reserveProfilesForFactoryRestore. Use Promise asynchronous callbacks.

**Since:** 18

**Required permissions:** ohos.permission.SET_TELEPHONY_ESIM_STATE

<!--Device-eSIM-function resetMemory(slotId: int, options?:ResetOption): Promise<ResultCode>--><!--Device-eSIM-function resetMemory(slotId: int, options?:ResetOption): Promise<ResultCode>-End-->

**System capability:** SystemCapability.Telephony.CoreService.Esim

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| slotId | number | Yes | Card slot ID. <br>The value should be an integer. <br>- **0**: card slot 1. <br>- **1**: card slot 2 |
| options | [ResetOption](arkts-telephony-esim-resetoption-e-sys.md) | No | Resets the status. If this parameter is not transferred, the default setting is used. You can transfer the corresponding enumerated value to specify the reset option. Multiple options can be bitwise or combined. |

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

eSIM.resetMemory(1).then(() => {
    console.info(`resetMemory invoking succeeded.`);
}).catch((err: BusinessError<void>) => {
    console.error(`resetMemory, ErrorState: err->${JSON.stringify(err)}`);
});
```

<!--DelEnd-->
