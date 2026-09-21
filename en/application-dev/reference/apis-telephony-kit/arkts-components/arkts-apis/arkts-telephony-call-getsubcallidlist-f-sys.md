# getSubCallIdList (System API)

## Modules to Import

```TypeScript
import { call } from '@kit.TelephonyKit';
```

## getSubCallIdList

```TypeScript
function getSubCallIdList(callId: number, callback: AsyncCallback<Array<string>>): void
```

Obtains the list of subcall IDs. This API uses an asynchronous callback to return the result.

**Since:** 7

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callId | number | Yes | Call ID. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;string&gt;&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameters types; |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [8300001](../errorcode-telephony.md#8300001-input-parameter-value-out-of-range) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-service-connection-error) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-system-internal-error) | System internal error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

call.getSubCallIdList(1, (err: BusinessError, data: Array<string>) => {
    if (err) {
        console.error(`getSubCallIdList fail, err->${JSON.stringify(err)}`);
    } else {
        console.info(`getSubCallIdList success, data->${JSON.stringify(data)}`);
    }
});
```


<a id="getsubcallidlist-1"></a>

## getSubCallIdList

```TypeScript
function getSubCallIdList(callId: number): Promise<Array<string>>
```

Obtains the list of subcall IDs. This API uses a promise to return the result.

**Since:** 7

**System capability:** SystemCapability.Telephony.CallManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callId | number | Yes | Call ID. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameters types; |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [8300001](../errorcode-telephony.md#8300001-input-parameter-value-out-of-range) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-service-connection-error) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-system-internal-error) | System internal error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

call.getSubCallIdList(1).then((data: Array<string>) => {
    console.info(`getSubCallIdList success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`getSubCallIdList fail, promise: err->${JSON.stringify(err)}`);
});
```
