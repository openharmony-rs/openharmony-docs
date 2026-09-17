# sendCallUiEvent (System API)

## Modules to Import

```TypeScript
import { call } from '@kit.TelephonyKit';
```

## sendCallUiEvent

```TypeScript
function sendCallUiEvent(callId: number, eventName: string): Promise<void>
```

Sends a call UI event. This API uses a promise to return the result.

**Since:** 12

**Required permissions:** ohos.permission.SET_TELEPHONY_STATE

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callId | number | Yes | Call ID. |
| eventName | string | Yes | Event name. |

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

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let callId: number = 0;
call.sendCallUiEvent(callId, 'eventName').then(() => {
    console.info(`sendCallUiEvent success.`);
}).catch((err: BusinessError) => {
    console.error(`sendCallUiEvent fail, promise: err->${JSON.stringify(err)}`);
});
```
