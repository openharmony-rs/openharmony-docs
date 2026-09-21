# isImsSwitchEnabled (System API)

## Modules to Import

```TypeScript
import { call } from '@kit.TelephonyKit';
```

## isImsSwitchEnabled

```TypeScript
function isImsSwitchEnabled(slotId: number, callback: AsyncCallback<boolean>): void
```

Checks whether the IMS service is enabled. This API uses an asynchronous callback to return the result.

**Since:** 8

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| slotId | number | Yes | Card slot ID.<br>- **0**: card slot 1. <br>- **1**: card slot 2. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. The value **true** indicates that the IMS service is enabled, and the value **false** indicates the opposite. The value **true** indicates that the IMS service is enabled, and the value **false** indicates the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameters types; |
| [8300001](../errorcode-telephony.md#8300001-input-parameter-value-out-of-range) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-service-connection-error) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-system-internal-error) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-internal-error) | Unknown error code. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

call.isImsSwitchEnabled(0, (err: BusinessError, data: boolean) => {
    if (err) {
        console.error(`isImsSwitchEnabled fail, err->${JSON.stringify(err)}`);
    } else {
        console.info(`isImsSwitchEnabled success, data->${JSON.stringify(data)}`);
    }
});
```


<a id="isimsswitchenabled-1"></a>

## isImsSwitchEnabled

```TypeScript
function isImsSwitchEnabled(slotId: number): Promise<boolean>
```

Checks whether the IMS service is enabled. This API uses a promise to return the result.

**Since:** 8

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| slotId | number | Yes | Card slot ID.<br>- **0**: card slot 1. <br>- **1**: card slot 2. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** indicates that the IMS service is enabled, and the value **false** indicates the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameters types; |
| [8300001](../errorcode-telephony.md#8300001-input-parameter-value-out-of-range) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-service-connection-error) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-system-internal-error) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-internal-error) | Unknown error code. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

call.isImsSwitchEnabled(0).then((data: boolean) => {
    console.info(`isImsSwitchEnabled success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`isImsSwitchEnabled fail, promise: err->${JSON.stringify(err)}`);
});
```
