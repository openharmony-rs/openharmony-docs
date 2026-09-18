# updateImsCallMode (System API)

## Modules to Import

```TypeScript
import { call } from '@kit.TelephonyKit';
```

## updateImsCallMode

```TypeScript
function updateImsCallMode(callId: number, mode: ImsCallMode, callback: AsyncCallback<void>): void
```

Updates the IMS call mode. This API uses an asynchronous callback to return the result.

**Since:** 8

**Required permissions:** ohos.permission.SET_TELEPHONY_STATE

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callId | number | Yes | Call ID. |
| mode | [ImsCallMode](arkts-telephony-call-imscallmode-e-sys.md) | Yes | IMS call mode. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameters types; |
| [8300001](../errorcode-telephony.md#8300001-input-parameter-value-out-of-range) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-service-connection-error) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-system-internal-error) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-internal-error) | Unknown error code. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

call.updateImsCallMode(1, 1, (err: BusinessError) => {
    if (err) {
        console.error(`updateImsCallMode fail, err->${JSON.stringify(err)}`);
    } else {
        console.info(`updateImsCallMode success.`);
    }
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

call.updateImsCallMode(1, 1).then(() => {
    console.info(`updateImsCallMode success.`);
}).catch((err: BusinessError) => {
    console.error(`updateImsCallMode fail, promise: err->${JSON.stringify(err)}`);
});
```


## updateImsCallMode

```TypeScript
function updateImsCallMode(callId: number, mode: ImsCallMode): Promise<void>
```

Updates the IMS call mode. This API uses a promise to return the result.

**Since:** 8

**Required permissions:** ohos.permission.SET_TELEPHONY_STATE

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callId | number | Yes | Call ID. |
| mode | [ImsCallMode](arkts-telephony-call-imscallmode-e-sys.md) | Yes | IMS call mode. |

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
| [8300001](../errorcode-telephony.md#8300001-input-parameter-value-out-of-range) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-service-connection-error) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-system-internal-error) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-internal-error) | Unknown error code. |

**Examples**

See [updateImsCallMode](#updateimscallmode)
