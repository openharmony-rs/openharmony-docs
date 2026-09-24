# getCallWaitingStatus (System API)

## Modules to Import

```TypeScript
import { call } from '@kit.TelephonyKit';
```

## getCallWaitingStatus

```TypeScript
function getCallWaitingStatus(slotId: number, callback: AsyncCallback<CallWaitingStatus>): void
```

Obtains the call waiting status. This API uses an asynchronous callback to return the result.

**Since:** 7

**Required permissions:** ohos.permission.GET_TELEPHONY_STATE

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| slotId | number | Yes | Card slot ID.<br>- **0**: card slot 1. <br>- **1**: card slot 2. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[CallWaitingStatus](arkts-telephony-call-callwaitingstatus-e-sys.md)&gt; | Yes | Callback used to return the result.<br>The value can be: <br>- **0**: Call waiting is disabled. <br>- **1**: Call waiting is enabled. |

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

call.getCallWaitingStatus(0, (err: BusinessError, data: call.CallWaitingStatus) => {
    if (err) {
        console.error(`getCallWaitingStatus fail, err->${JSON.stringify(err)}`);
    } else {
        console.info(`getCallWaitingStatus success, data->${JSON.stringify(data)}`);
    }
});
```


<a id="getcallwaitingstatus-1"></a>

## getCallWaitingStatus

```TypeScript
function getCallWaitingStatus(slotId: number): Promise<CallWaitingStatus>
```

Obtains the call waiting status. This API uses a promise to return the result.

**Since:** 7

**Required permissions:** ohos.permission.GET_TELEPHONY_STATE

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| slotId | number | Yes | Card slot ID.<br>- **0**: card slot 1. <br>- **1**: card slot 2. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[CallWaitingStatus](arkts-telephony-call-callwaitingstatus-e-sys.md)&gt; | Promise used to return the result.<br>- **0**: Call waiting is disabled. <br>- **1**: Call waiting is enabled. |

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

call.getCallWaitingStatus(0).then((data: call.CallWaitingStatus) => {
    console.info(`getCallWaitingStatus success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`getCallWaitingStatus fail, promise: err->${JSON.stringify(err)}`);
});
```
