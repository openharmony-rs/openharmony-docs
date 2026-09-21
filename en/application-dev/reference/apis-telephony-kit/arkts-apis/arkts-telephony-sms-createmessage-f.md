# createMessage

## Modules to Import

```TypeScript
import { sms } from '@kit.TelephonyKit';
```

## createMessage

```TypeScript
function createMessage(pdu: Array<number>, specification: string, callback: AsyncCallback<ShortMessage>): void
```

Creates an SMS instance based on the protocol data unit (PDU) and specified SMS protocol. This API uses an asynchronous callback to return the result.

**Since:** 6

**System capability:** SystemCapability.Telephony.SmsMms

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| pdu | Array&lt;number&gt; | Yes | Protocol data unit, which is obtained from the received SMS message. |
| specification | string | Yes | SMS protocol type.<br>- **3gpp**: GSM/UMTS/LTE SMS <br>- **3gpp2**: CDMA SMS |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[ShortMessage](arkts-telephony-sms-shortmessage-i.md)&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [8300001](../errorcode-telephony.md#8300001-input-parameter-value-out-of-range) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-service-connection-error) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-system-internal-error) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-internal-error) | Unknown error code. |

**Examples**

```TypeScript
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

const specification: string = '3gpp';
// Display PDUs in array format. The type is number.
const pdu: Array<number> = [0x01, 0x00, 0x05, 0x81, 0x01, 0x80, 0xF6, 0x00, 0x00, 0x05, 0xE8, 0x32, 0x9B, 0xFD, 0x06];
sms.createMessage(pdu, specification, (err: BusinessError, data: sms.ShortMessage) => {
    console.info(`callback: err->${JSON.stringify(err)}, data->${JSON.stringify(data)}`);
});
```


<a id="createmessage-1"></a>

## createMessage

```TypeScript
function createMessage(pdu: Array<number>, specification: string): Promise<ShortMessage>
```

Creates an SMS instance based on the protocol data unit (PDU) and specified SMS protocol. This API uses a promise to return the result.

**Since:** 6

**System capability:** SystemCapability.Telephony.SmsMms

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| pdu | Array&lt;number&gt; | Yes | Protocol data unit, which is obtained from the received SMS message. |
| specification | string | Yes | SMS protocol type.<br>- **3gpp**: GSM/UMTS/LTE SMS <br>- **3gpp2**: CDMA SMS |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ShortMessage](arkts-telephony-sms-shortmessage-i.md)&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [8300001](../errorcode-telephony.md#8300001-input-parameter-value-out-of-range) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-service-connection-error) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-system-internal-error) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-internal-error) | Unknown error code. |

**Examples**

```TypeScript
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

const specification: string = '3gpp';
// Display PDUs in array format. The type is number.
const pdu: Array<number> = [0x01, 0x00, 0x05, 0x81, 0x01, 0x80, 0xF6, 0x00, 0x00, 0x05, 0xE8, 0x32, 0x9B, 0xFD, 0x06];
sms.createMessage(pdu, specification).then((data: sms.ShortMessage) => {
    console.info(`createMessage success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`createMessage failed, promise: err->${JSON.stringify(err)}`);
});
```
