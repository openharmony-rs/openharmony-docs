# separateConference (System API)

## Modules to Import

```TypeScript
import { call } from '@kit.TelephonyKit';
```

## separateConference

```TypeScript
function separateConference(callId: number, callback: AsyncCallback<void>): void
```

Separates calls from a conference call. This API uses an asynchronous callback to return the result.

**Since:** 11

**Required permissions:** ohos.permission.SET_TELEPHONY_STATE

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
| 8300008 | Conference call is not active. |
| [8300999](../errorcode-telephony.md#8300999-internal-error) | Unknown error code. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

call.separateConference(1, (err: BusinessError) => {
    if (err) {
        console.error(`separateConference fail, err->${JSON.stringify(err)}`);
    } else {
        console.info(`separateConference success.`);
    }
});
```


<a id="separateconference-1"></a>

## separateConference

```TypeScript
function separateConference(callId: number): Promise<void>
```

Separates calls from a conference call. This API uses a promise to return the result.

**Since:** 11

**Required permissions:** ohos.permission.SET_TELEPHONY_STATE

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
| 8300008 | Conference call is not active. |
| [8300999](../errorcode-telephony.md#8300999-internal-error) | Unknown error code. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

call.separateConference(1).then(() => {
    console.info(`separateConference success.`);
}).catch((err: BusinessError) => {
    console.error(`separateConference fail, promise: err->${JSON.stringify(err)}`);
});
```
