# getSmsSegmentsInfo (System API)

## Modules to Import

```TypeScript
import { sms } from '@kit.TelephonyKit';
```

## getSmsSegmentsInfo

```TypeScript
function getSmsSegmentsInfo(slotId: number, message: string, force7bit: boolean, callback: AsyncCallback<SmsSegmentsInfo>): void
```

Obtains SMS message segment information. This API uses an asynchronous callback to return the result.

**Since:** 8

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| slotId | number | Yes | SIM card slot ID.<br>- **0**: card slot 1 <br>- **1**: card slot 2 |
| message | string | Yes | SMS message. |
| force7bit | boolean | Yes | Whether to use 7-bit encoding. The default value is **false**.<br>- **true**: yes <br>- **false**: no |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[SmsSegmentsInfo](arkts-telephony-sms-smssegmentsinfo-i-sys.md)&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [8300001](../errorcode-telephony.md#8300001-input-parameter-value-out-of-range) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-service-connection-error) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-system-internal-error) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-internal-error) | Unknown error code. |

**Examples**

```TypeScript
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

let slotId: number = 0;
sms.getSmsSegmentsInfo(slotId, "message", false, (err: BusinessError, data: sms.SmsSegmentsInfo) => {
      console.info(`callback: err->${JSON.stringify(err)}, data->${JSON.stringify(data)}`);
});
```

```TypeScript
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

let slotId: number = 0;
let promise = sms.getSmsSegmentsInfo(slotId, "message", false);
promise.then((data: sms.SmsSegmentsInfo) => {
    console.info(`getSmsSegmentsInfo success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`getSmsSegmentsInfo failed, promise: err->${JSON.stringify(err)}`);
});
```


## getSmsSegmentsInfo

```TypeScript
function getSmsSegmentsInfo(slotId: number, message: string, force7bit: boolean): Promise<SmsSegmentsInfo>
```

Obtains SMS message segment information. This API uses a promise to return the result.

**Since:** 8

**System capability:** SystemCapability.Telephony.SmsMms

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| slotId | number | Yes | SIM card slot ID.<br>- **0**: card slot 1 <br>- **1**: card slot 2 |
| message | string | Yes | SMS message. |
| force7bit | boolean | Yes | Whether to use 7-bit encoding. The default value is **false**.<br>- **true**: yes <br>- **false**: no |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[SmsSegmentsInfo](arkts-telephony-sms-smssegmentsinfo-i-sys.md)&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
| [8300001](../errorcode-telephony.md#8300001-input-parameter-value-out-of-range) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-service-connection-error) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-system-internal-error) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-internal-error) | Unknown error code. |

**Examples**

See [getSmsSegmentsInfo](#getsmssegmentsinfo)
