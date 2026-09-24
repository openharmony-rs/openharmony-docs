# alterPin2 (System API)

## Modules to Import

```TypeScript
import { sim } from '@kit.TelephonyKit';
```

## alterPin2

```TypeScript
function alterPin2(slotId: number, newPin2: string, oldPin2: string, callback: AsyncCallback<LockStatusResponse>): void
```

Change Pin2 password.

**Since:** 8

**Required permissions:** ohos.permission.SET_TELEPHONY_STATE

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| slotId | number | Yes | Indicates the card slot index number, ranging from 0 to the maximum card slot index number supported by the device. |
| newPin2 | string | Yes | Indicates a new password. |
| oldPin2 | string | Yes | Indicates old password. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[LockStatusResponse](arkts-telephony-sim-lockstatusresponse-i-sys.md)&gt; | Yes | Indicates the callback for getting the response to obtain the SIM card lock status of the specified card slot. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [8300001](../errorcode-telephony.md#8300001-input-parameter-value-out-of-range) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-service-connection-error) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-system-internal-error) | System internal error. |
| [8300004](../errorcode-telephony.md#8300004-sim-card-not-detected) | No SIM card found. |
| [8300999](../errorcode-telephony.md#8300999-internal-error) | Unknown error. |
| [8301002](../errorcode-telephony.md#8301002-failed-to-read-or-update-sim-card-data) | The SIM card failed to read or update data. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

sim.alterPin2(0, "1234", "0000", (err: BusinessError, data: sim.LockStatusResponse) => {
    console.info(`callback: err->${JSON.stringify(err)}, data->${JSON.stringify(data)}`);
});
```


<a id="alterpin2-1"></a>

## alterPin2

```TypeScript
function alterPin2(slotId: number, newPin2: string, oldPin2: string): Promise<LockStatusResponse>
```

Change Pin2 password.

**Since:** 8

**Required permissions:** ohos.permission.SET_TELEPHONY_STATE

**System capability:** SystemCapability.Telephony.CoreService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| slotId | number | Yes | Indicates the card slot index number, ranging from 0 to the maximum card slot index number supported by the device. |
| newPin2 | string | Yes | Indicates a new password. |
| oldPin2 | string | Yes | Indicates old password. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[LockStatusResponse](arkts-telephony-sim-lockstatusresponse-i-sys.md)&gt; | Returns the response to obtain the SIM card lock status of the specified card slot. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [8300001](../errorcode-telephony.md#8300001-input-parameter-value-out-of-range) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-service-connection-error) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-system-internal-error) | System internal error. |
| [8300004](../errorcode-telephony.md#8300004-sim-card-not-detected) | No SIM card found. |
| [8300999](../errorcode-telephony.md#8300999-internal-error) | Unknown error. |
| [8301002](../errorcode-telephony.md#8301002-failed-to-read-or-update-sim-card-data) | The SIM card failed to read or update data. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

sim.alterPin2(0, "1234", "0000").then((data: sim.LockStatusResponse) => {
    console.info(`alterPin2 success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`alterPin2 failed, promise: err->${JSON.stringify(err)}`);
});
```
