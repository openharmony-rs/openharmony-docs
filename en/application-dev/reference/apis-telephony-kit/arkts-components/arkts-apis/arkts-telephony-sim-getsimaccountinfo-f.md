# getSimAccountInfo

## Modules to Import

```TypeScript
import { sim } from '@kit.TelephonyKit';
```

## getSimAccountInfo

```TypeScript
function getSimAccountInfo(slotId: number, callback: AsyncCallback<IccAccountInfo>): void
```

Obtains SIM card account information. This API uses an asynchronous callback to return the result.

**Required permission**: ohos.permission.GET_TELEPHONY_STATE

> **NOTE:** 
> 
> The **GET_TELEPHONY_STATE** permission is required to obtain the ICCID and phone number. Such information is
> sensitive and not open to third-party applications. When this API is called, the returned ICCID and phone number
> are empty.

**Since:** 10

**Required permissions:** ohos.permission.GET_TELEPHONY_STATE

**System capability:** SystemCapability.Telephony.CoreService

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| slotId | number | Yes | Card slot ID.<br>- **0**: card slot 1. <br>- **1**: card slot 2 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[IccAccountInfo](arkts-telephony-sim-iccaccountinfo-i.md)&gt; | Yes | Callback used to return the result, which is the account information of the SIM card in the specified slot. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied.<br>**Applicable version:** 10 - 22 |
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

sim.getSimAccountInfo(0, (err:BusinessError , data: sim.IccAccountInfo) => {
    console.info(`callback: err->${JSON.stringify(err)}, data->${JSON.stringify(data)}`);
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

sim.getSimAccountInfo(0).then((data: sim.IccAccountInfo) => {
    console.info(`getSimAccountInfo success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`getSimAccountInfo failed, promise: err->${JSON.stringify(err)}`);
});
```


## getSimAccountInfo

```TypeScript
function getSimAccountInfo(slotId: number): Promise<IccAccountInfo>
```

Obtains SIM card account information. This API uses a promise to return the result.

**Required permission**: ohos.permission.GET_TELEPHONY_STATE

> **NOTE:** 
> 
> The **GET_TELEPHONY_STATE** permission is required to obtain the ICCID and phone number. Such information is
> sensitive and not open to third-party applications. When this API is called, the returned ICCID and phone number
> are empty.

**Since:** 10

**Required permissions:** ohos.permission.GET_TELEPHONY_STATE

**System capability:** SystemCapability.Telephony.CoreService

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| slotId | number | Yes | Card slot ID.<br>- **0**: card slot 1. <br>- **1**: card slot 2 |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[IccAccountInfo](arkts-telephony-sim-iccaccountinfo-i.md)&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied.<br>**Applicable version:** 10 - 22 |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [8300001](../errorcode-telephony.md#8300001-input-parameter-value-out-of-range) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-service-connection-error) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-system-internal-error) | System internal error. |
| [8300004](../errorcode-telephony.md#8300004-sim-card-not-detected) | No SIM card found. |
| [8300999](../errorcode-telephony.md#8300999-internal-error) | Unknown error. |
| [8301002](../errorcode-telephony.md#8301002-failed-to-read-or-update-sim-card-data) | The SIM card failed to read or update data. |

**Examples**

See [getSimAccountInfo](#getsimaccountinfo)
