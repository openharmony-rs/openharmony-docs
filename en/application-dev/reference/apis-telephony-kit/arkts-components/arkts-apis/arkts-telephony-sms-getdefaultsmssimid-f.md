# getDefaultSmsSimId

## Modules to Import

```TypeScript
import { sms } from '@kit.TelephonyKit';
```

## getDefaultSmsSimId

```TypeScript
function getDefaultSmsSimId(callback: AsyncCallback<number>): void
```

Obtains the default ID of the SIM card used to send SMS messages. This API uses an asynchronous callback to return the result.

**Since:** 10

**System capability:** SystemCapability.Telephony.SmsMms

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback used to return the result.<br>The return value is bound to the SIM card and increases from 1. <br>The return value is **-1** if no SIM card is detected. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [8300001](../errorcode-telephony.md#8300001-input-parameter-value-out-of-range) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-service-connection-error) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-system-internal-error) | System internal error. |
| [8300004](../errorcode-telephony.md#8300004-sim-card-not-detected) | Do not have sim card. |
| [8300999](../errorcode-telephony.md#8300999-internal-error) | Unknown error code. |
| [8301001](../errorcode-telephony.md#8301001-sim-card-not-activated) | SIM card is not activated. |

**Examples**

```TypeScript
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

sms.getDefaultSmsSimId((err: BusinessError, data: number) => {
    console.info(`callback: err->${JSON.stringify(err)}, data->${JSON.stringify(data)}`);
});
```

```TypeScript
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

let promise = sms.getDefaultSmsSimId();
promise.then((data: number) => {
    console.info(`getDefaultSmsSimId success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`getDefaultSmsSimId failed, promise: err->${JSON.stringify(err)}`);
});
```


## getDefaultSmsSimId

```TypeScript
function getDefaultSmsSimId(): Promise<number>
```

Obtains the default ID of the SIM card used to send SMS messages. This API uses a promise to return the result.

**Since:** 10

**System capability:** SystemCapability.Telephony.SmsMms

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the result.<br>The return value is bound to the SIM card and increases from 1. <br>The return value is **-1** if no SIM card is detected. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [8300001](../errorcode-telephony.md#8300001-input-parameter-value-out-of-range) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-service-connection-error) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-system-internal-error) | System internal error. |
| [8300004](../errorcode-telephony.md#8300004-sim-card-not-detected) | Do not have sim card. |
| [8300999](../errorcode-telephony.md#8300999-internal-error) | Unknown error code. |
| [8301001](../errorcode-telephony.md#8301001-sim-card-not-activated) | SIM card is not activated. |

**Examples**

See [getDefaultSmsSimId](#getdefaultsmssimid)
