# sendMessage

## Modules to Import

```TypeScript
import { sms } from '@kit.TelephonyKit';
```

## sendMessage

```TypeScript
function sendMessage(options: SendMessageOptions): void
```

Sends an SMS message.

> **NOTE:** 
> 
> This API is supported since API version 6 and deprecated since API version 10. You are advised to use
> [sendShortMessage](arkts-telephony-sms-sendshortmessage-f.md).

**Since:** 6

**Deprecated since:** 10

**Substitutes:** [sendShortMessage](arkts-telephony-sms-sendshortmessage-f.md)

**Required permissions:** ohos.permission.SEND_MESSAGES

**System capability:** SystemCapability.Telephony.SmsMms

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [SendMessageOptions](arkts-telephony-sms-sendmessageoptions-i.md) | Yes | Options (including the callback) for sending SMS messages. For details, see [SendMessageOptions](arkts-telephony-sms-sendmessageoptions-i.md). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [8300001](../errorcode-telephony.md#8300001-input-parameter-value-out-of-range) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-service-connection-error) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-system-internal-error) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-internal-error) | Unknown error code. |

**Examples**

```TypeScript
import { sms } from '@kit.TelephonyKit';
import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';

let sendCallback: AsyncCallback<sms.ISendShortMessageCallback> = (err: BusinessError, data: sms.ISendShortMessageCallback) => {
    console.info(`sendCallback: err->${JSON.stringify(err)}, data->${JSON.stringify(data)}`); 
};
let deliveryCallback: AsyncCallback<sms.IDeliveryShortMessageCallback> = (err: BusinessError, data: sms.IDeliveryShortMessageCallback) => {
    console.info(`deliveryCallback: err->${JSON.stringify(err)}, data->${JSON.stringify(data)}`); 
};
let options: sms.SendMessageOptions = {
    slotId: 0,
    content: 'SMS message content',
    destinationHost: '+861xxxxxxxxxx',
    serviceCenter: '+861xxxxxxxxxx',
    destinationPort: 1000,
    sendCallback: sendCallback,
    deliveryCallback: deliveryCallback
};
sms.sendMessage(options);
```
