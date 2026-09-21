# joinConference (System API)

## Modules to Import

```TypeScript
import { call } from '@kit.TelephonyKit';
```

## joinConference

```TypeScript
function joinConference(mainCallId: number, callNumberList: Array<string>, callback: AsyncCallback<void>): void
```

Joins a conference call. This API uses an asynchronous callback to return the result.

**Since:** 8

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mainCallId | number | Yes | Main call ID. |
| callNumberList | Array&lt;string&gt; | Yes | List of call numbers. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

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

let callNumberList: Array<string> = [
    "138XXXXXXXX"
];
call.joinConference(1, callNumberList, (err: BusinessError) => {
    if (err) {
        console.error(`joinConference fail, err->${JSON.stringify(err)}`);
    } else {
        console.info(`joinConference success.`);
    }
});
```


<a id="joinconference-1"></a>

## joinConference

```TypeScript
function joinConference(mainCallId: number, callNumberList: Array<string>): Promise<void>
```

Joins a conference call. This API uses a promise to return the result.

**Since:** 8

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mainCallId | number | Yes | Main call ID. |
| callNumberList | Array&lt;string&gt; | Yes | List of call numbers. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

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

let callNumberList: Array<string> = [
    "138XXXXXXXX"
];
call.joinConference(1, callNumberList).then(() => {
    console.info(`joinConference success.`);
}).catch((err: BusinessError) => {
    console.error(`joinConference fail, promise: err->${JSON.stringify(err)}`);
});
```
