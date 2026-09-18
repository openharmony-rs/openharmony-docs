# unHoldCall (System API)

## Modules to Import

```TypeScript
import { call } from '@kit.TelephonyKit';
```

## unHoldCall

```TypeScript
function unHoldCall(callId: number, callback: AsyncCallback<void>): void
```

Unholds a call based on the specified call ID. This API uses an asynchronous callback to return the result.

**Since:** 7

**Required permissions:** ohos.permission.ANSWER_CALL

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callId | number | Yes | Call ID. |
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

call.unHoldCall(1, (err: BusinessError) => {
    if (err) {
        console.error(`unHoldCall fail, err->${JSON.stringify(err)}`);
    } else {
        console.info(`unHoldCall success.`);
    }
});
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

call.unHoldCall(1).then(() => {
    console.info(`unHoldCall success.`);
}).catch((err: BusinessError) => {
    console.error(`unHoldCall fail, promise: err->${JSON.stringify(err)}`);
});
```


## unHoldCall

```TypeScript
function unHoldCall(callId: number): Promise<void>
```

Unholds a call based on the specified call ID. This API uses a promise to return the result.

**Since:** 7

**Required permissions:** ohos.permission.ANSWER_CALL

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callId | number | Yes | Call ID. |

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

See [unHoldCall](#unholdcall)
