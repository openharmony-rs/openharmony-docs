# setCallTransfer (System API)

## Modules to Import

```TypeScript
import { call } from '@kit.TelephonyKit';
```

## setCallTransfer

```TypeScript
function setCallTransfer(slotId: number, info: CallTransferInfo, callback: AsyncCallback<void>): void
```

Sets call transfer information. This API uses an asynchronous callback to return the result.

**Since:** 8

**Required permissions:** ohos.permission.SET_TELEPHONY_STATE

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| slotId | number | Yes | Card slot ID.<br>- **0**: card slot 1. <br>- **1**: card slot 2. |
| info | [CallTransferInfo](arkts-telephony-call-calltransferinfo-i-sys.md) | Yes | Call transfer information. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameters types; |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [8300001](../errorcode-telephony.md#8300001-input-parameter-value-out-of-range) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-service-connection-error) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-system-internal-error) | System internal error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let callTransferInfo: call.CallTransferInfo = {
    transferNum: "111",
    type: call.CallTransferType.TRANSFER_TYPE_BUSY,
    settingType: call.CallTransferSettingType.CALL_TRANSFER_ENABLE
}
call.setCallTransfer(0, callTransferInfo, (err: BusinessError) => {
    if (err) {
        console.error(`setCallTransfer fail, err->${JSON.stringify(err)}`);
    } else {
        console.info(`setCallTransfer success.`);
    }
});
```


<a id="setcalltransfer-1"></a>

## setCallTransfer

```TypeScript
function setCallTransfer(slotId: number, info: CallTransferInfo): Promise<void>
```

Sets call transfer information. This API uses a promise to return the result.

**Since:** 8

**Required permissions:** ohos.permission.SET_TELEPHONY_STATE

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| slotId | number | Yes | Card slot ID.<br>- **0**: card slot 1. <br>- **1**: card slot 2. |
| info | [CallTransferInfo](arkts-telephony-call-calltransferinfo-i-sys.md) | Yes | Call transfer information. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameters types; |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [8300001](../errorcode-telephony.md#8300001-input-parameter-value-out-of-range) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-service-connection-error) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-system-internal-error) | System internal error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let callTransferInfo: call.CallTransferInfo = {
    transferNum: "111",
    type: call.CallTransferType.TRANSFER_TYPE_BUSY,
    settingType: call.CallTransferSettingType.CALL_TRANSFER_ENABLE
}
call.setCallTransfer(0, callTransferInfo).then(() => {
    console.info(`setCallTransfer success.`);
}).catch((err: BusinessError) => {
    console.error(`setCallTransfer fail, promise: err->${JSON.stringify(err)}`);
});
```
