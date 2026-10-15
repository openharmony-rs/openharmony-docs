# @ohos.telephony.sms (SMS)
<!--Kit: Telephony Kit-->
<!--Subsystem: Telephony-->
<!--Owner: @shao-yikai-->
<!--Designer: @wnazgul-->
<!--Tester: @jiang_99-->
<!--Adviser: @zhang_yixin13-->

The SMS module provides basic capabilities for managing SMS messages, including:
 - Creates and sends SMS messages.
 - Obtains the default slot ID of the SIM card used to send SMS messages.
 - Checks whether the current device can send and receive messages.

> **NOTE**
>
> The initial APIs of this module are supported since API version 6. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { sms } from '@kit.TelephonyKit';
```

## sms.createMessage

createMessage\(pdu: Array&lt;number&gt;, specification: string, callback: AsyncCallback\<ShortMessage\>\): void

Creates an SMS instance based on the protocol data unit (PDU) and specified SMS protocol. This API uses an asynchronous callback to return the result.

Use scenarios: After an SMS is received, the PDU data returned by the system is parsed into an SMS instance to read the SMS body and sender address.

**System capability**: SystemCapability.Telephony.SmsMms

**Parameters**

| Name       | Type                                              | Mandatory| Description                                                        |
| ------------- | -------------------------------------------------- | ---- | ------------------------------------------------------------ |
| pdu           | Array&lt;number&gt;                                | Yes  | Protocol data unit, which is obtained from the received SMS message.                          |
| specification | string                                             | Yes  | SMS protocol type. <br>- **3gpp**: GSM/UMTS/LTE SMS<br>- **3gpp2**: CDMA SMS|
| callback      | AsyncCallback&lt;[ShortMessage](#shortmessage)&gt; | Yes  | Callback used to return the result.                                                  |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Telephony Error Codes](errorcode-telephony.md).

| ID|                  Error Message                    |
| -------- | -------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                            |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Operation failed. Cannot connect to service. |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error code.                          |

**Example**

```ts
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

const specification: string = '3gpp';
// Display PDUs in array format. The type is number.
const pdu: Array<number> = [0x01, 0x00, 0x05, 0x81, 0x01, 0x80, 0xF6, 0x00, 0x00, 0x05, 0xE8, 0x32, 0x9B, 0xFD, 0x06];
sms.createMessage(pdu, specification, (err: BusinessError, data: sms.ShortMessage) => {
    if (err) {
        console.error(`callback: err->${JSON.stringify(err)}`);
        return;
    }
    console.info(`callback: data->${JSON.stringify(data)}`);
});
```


## sms.createMessage

createMessage\(pdu: Array&lt;number&gt;, specification: string\): Promise\<ShortMessage\>

Creates an SMS instance based on the protocol data unit (PDU) and specified SMS protocol. This API uses a promise to return the result.

**System capability**: SystemCapability.Telephony.SmsMms

**Parameters**

| Name       | Type               | Mandatory| Description                                                        |
| ------------- | ------------------- | ---- | ------------------------------------------------------------ |
| pdu           | Array&lt;number&gt; | Yes  | Protocol data unit, which is obtained from the received SMS message.                          |
| specification | string              | Yes  | SMS protocol type. <br>- **3gpp**: GSM/UMTS/LTE SMS<br>- **3gpp2**: CDMA SMS|

**Return value**

| Type                                        | Description                             |
| -------------------------------------------- | --------------------------------- |
| Promise&lt;[ShortMessage](#shortmessage)&gt; | Promise used to return the result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Telephony Error Codes](errorcode-telephony.md).

| ID|                  Error Message                    |
| -------- | -------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                            |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Operation failed. Cannot connect to service. |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error code.                          |

**Example**

```ts
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

const specification: string = '3gpp';
// Display PDUs in array format. The type is number.
const pdu: Array<number> = [0x01, 0x00, 0x05, 0x81, 0x01, 0x80, 0xF6, 0x00, 0x00, 0x05, 0xE8, 0x32, 0x9B, 0xFD, 0x06];
sms.createMessage(pdu, specification).then((data: sms.ShortMessage) => {
    console.info(`createMessage success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`createMessage failed, promise: errCode:${err.code},errMsg:${err.message}`);
});
```

## sms.sendMessage<sup>(deprecated)</sup>

sendMessage\(options: SendMessageOptions\): void

Sends an SMS message.

> **NOTE**
>
> This API is supported since API version 6 and deprecated since API version 10. You are advised to use [sendShortMessage](#smssendshortmessage10).

**Required permissions**: ohos.permission.SEND_MESSAGES (available only for system applications)

**System capability**: SystemCapability.Telephony.SmsMms

**Parameters**

| Name | Type                                     | Mandatory| Description                                                        |
| ------- | ----------------------------------------- | ---- | ------------------------------------------------------------ |
| options | [SendMessageOptions](#sendmessageoptions) | Yes  | Options (including the callback) for sending SMS messages. For details, see [SendMessageOptions](#sendmessageoptions).|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Telephony Error Codes](errorcode-telephony.md).

| ID|                 Error Message                    |
| -------- | -------------------------------------------- |
| 201      | Permission denied.                           |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                            |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Operation failed. Cannot connect to service. |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error code.                          |

**Example**

```ts
import { sms } from '@kit.TelephonyKit';
import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';

let sendCallback: AsyncCallback<sms.ISendShortMessageCallback> = (err: BusinessError, data: sms.ISendShortMessageCallback) => {
    if (err) {
        console.error(`sendCallback: err->${JSON.stringify(err)}`);
        return;
    }
    console.info(`sendCallback: data->${JSON.stringify(data)}`); 
};
let deliveryCallback: AsyncCallback<sms.IDeliveryShortMessageCallback> = (err: BusinessError, data: sms.IDeliveryShortMessageCallback) => {
    if (err) {
        console.error(`deliveryCallback: err->${JSON.stringify(err)}`);
        return;
    }
    console.info(`deliveryCallback: data->${JSON.stringify(data)}`);
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

## sms.sendShortMessage<sup>10+</sup>

sendShortMessage\(options: SendMessageOptions, callback: AsyncCallback&lt;void&gt;\): void

Sends an SMS message. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.SEND_MESSAGES (available only for system applications)

**System capability**: SystemCapability.Telephony.SmsMms

**Parameters**

| Name  | Type                       | Mandatory| Description                                    |
| -------- | --------------------------- | ---- | ---------------------------------------- |
| options | [SendMessageOptions](#sendmessageoptions) | Yes  | Options (including the callback) for sending SMS messages. For details, see [SendMessageOptions](#sendmessageoptions).|
| callback | AsyncCallback&lt;void&gt; | Yes  | Callback used to return the result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Telephony Error Codes](errorcode-telephony.md).

| ID|                 Error Message                    |
| -------- | -------------------------------------------- |
| 201      | Permission denied.                           |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                             |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Operation failed. Cannot connect to service. |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error code.                          |

**Example**

```ts
import { sms } from '@kit.TelephonyKit';
import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';

let sendCallback: AsyncCallback<sms.ISendShortMessageCallback> = (err: BusinessError, data: sms.ISendShortMessageCallback) => {
    if (err) {
        console.error(`sendCallback: err->${JSON.stringify(err)}`);
        return;
    }
    console.info(`sendCallback: data->${JSON.stringify(data)}`);
};
let deliveryCallback: AsyncCallback<sms.IDeliveryShortMessageCallback> = (err: BusinessError, data: sms.IDeliveryShortMessageCallback) => {
    if (err) {
        console.error(`deliveryCallback: err->${JSON.stringify(err)}`);
        return;
    }
    console.info(`deliveryCallback: data->${JSON.stringify(data)}`);
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
sms.sendShortMessage(options, (err: BusinessError) => {
    if (err) {
        console.error(`callback: err->${JSON.stringify(err)}`);
        return;
    }
});
```

## sms.sendShortMessage<sup>10+</sup>

sendShortMessage\(options: SendMessageOptions\): Promise&lt;void&gt;

Sends an SMS message. This API uses a promise to return the result.

**Required permissions**: ohos.permission.SEND_MESSAGES (available only for system applications)

**System capability**: SystemCapability.Telephony.SmsMms

**Parameters**

| Name  | Type                       | Mandatory| Description                                    |
| -------- | --------------------------- | ---- | ---------------------------------------- |
| options | [SendMessageOptions](#sendmessageoptions) | Yes  | Options (including the callback) for sending SMS messages. For details, see [SendMessageOptions](#sendmessageoptions).|

**Return value**

| Type           | Description                                                        |
| --------------- | ------------------------------------------------------------ |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Telephony Error Codes](errorcode-telephony.md).

| ID|                 Error Message                    |
| -------- | -------------------------------------------- |
| 201      | Permission denied.                           |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                            |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Operation failed. Cannot connect to service. |
| 8300003  | System internal error.                       |
| 8300999  | Unknown error code.                          |

**Example**

```ts
import { sms } from '@kit.TelephonyKit';
import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';

let sendCallback: AsyncCallback<sms.ISendShortMessageCallback> = (err: BusinessError, data: sms.ISendShortMessageCallback) => {
    if (err) {
        console.error(`sendCallback: err->${JSON.stringify(err)}`);
        return;
    }
    console.info(`sendCallback: data->${JSON.stringify(data)}`);
};
let deliveryCallback: AsyncCallback<sms.IDeliveryShortMessageCallback> = (err: BusinessError, data: sms.IDeliveryShortMessageCallback) => {
    if (err) {
        console.error(`deliveryCallback: err->${JSON.stringify(err)}`);
        return;
    }
    console.info(`deliveryCallback: data->${JSON.stringify(data)}`);
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
let promise = sms.sendShortMessage(options);
promise.then(() => {
    console.info(`sendShortMessage success`);
}).catch((err: BusinessError) => {
    console.error(`sendShortMessage failed, promise: errCode:${err.code},errMsg:${err.message}`);
});

```


## sms.getDefaultSmsSlotId<sup>7+</sup>

getDefaultSmsSlotId\(callback: AsyncCallback&lt;number&gt;\): void

Obtains the default slot ID of the SIM card used to send SMS messages. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Telephony.SmsMms

**Parameters**

| Name  | Type                       | Mandatory| Description                                    |
| -------- | --------------------------- | ---- | ---------------------------------------- |
| callback | AsyncCallback&lt;number&gt; | Yes  | Callback used to return the result.<br>- **0**: card slot 1<br>- **1**: card slot 2|

**Example**

```ts
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

sms.getDefaultSmsSlotId((err: BusinessError, data: number) => {
    if (err) {
        console.error(`callback: err->${JSON.stringify(err)}`);
        return;
    }
    console.info(`callback: data->${JSON.stringify(data)}`);
});
```


## sms.getDefaultSmsSlotId<sup>7+</sup>

getDefaultSmsSlotId\(\): Promise&lt;number&gt;

Obtains the default slot ID of the SIM card used to send SMS messages. This API uses a promise to return the result.

**System capability**: SystemCapability.Telephony.SmsMms

**Return value**

| Type           | Description                                                        |
| --------------- | ------------------------------------------------------------ |
| Promise&lt;number&gt; | Promise used to return the result.<br>- **0**: card slot 1<br>- **1**: card slot 2|

**Example**

```ts
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

sms.getDefaultSmsSlotId().then((data: number) => {
    console.info(`getDefaultSmsSlotId success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`getDefaultSmsSlotId failed, promise: errCode${err.code},errMsg:${err.message}`);
});
```

## sms.hasSmsCapability<sup>7+</sup>

hasSmsCapability\(\): boolean

Checks whether the current device can send and receive messages. This method uses the synchronous mode.

**System capability**: SystemCapability.Telephony.SmsMms

**Return value**

| Type   | Description                                                        |
| ------- | ------------------------------------------------------------ |
| boolean | - **true**: The device can send and receive SMS messages.<br>- **false**: The device cannot send or receive SMS messages.|

**Example**

```ts
import { sms } from '@kit.TelephonyKit';

let result = sms.hasSmsCapability(); 
console.info(`hasSmsCapability: ${JSON.stringify(result)}`);
```

## sms.getDefaultSmsSimId<sup>10+</sup>

getDefaultSmsSimId\(callback: AsyncCallback&lt;number&gt;\): void

Obtains the default ID of the SIM card used to send SMS messages. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Telephony.SmsMms

**Parameters**

| Name  | Type                       | Mandatory| Description                                    |
| -------- | --------------------------- | ---- | ---------------------------------------- |
| callback | AsyncCallback&lt;number&gt; | Yes  | Callback used to return the result.<br>The return value is bound to the SIM card and increases from 1.<br>The return value is **-1** if no SIM card is detected.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Telephony Error Codes](errorcode-telephony.md).

| ID|                 Error Message                    |
| -------- | -------------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.                            |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Operation failed. Cannot connect to service. |
| 8300003  | System internal error.                       |
| 8300004  | Do not have sim card.                        |
| 8300999  | Unknown error code.                          |
| 8301001  | SIM card is not activated.                   |

**Example**

```ts
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

sms.getDefaultSmsSimId((err: BusinessError, data: number) => {
    if (err) {
        console.error(`callback: err->${JSON.stringify(err)}`);
        return;
    }
    console.info(`callback: data->${JSON.stringify(data)}`);
});
```


## sms.getDefaultSmsSimId<sup>10+</sup>

getDefaultSmsSimId\(\): Promise&lt;number&gt;

Obtains the default ID of the SIM card used to send SMS messages. This API uses a promise to return the result.

**System capability**: SystemCapability.Telephony.SmsMms

**Return value**

| Type           | Description                                                        |
| --------------- | ------------------------------------------------------------ |
| Promise&lt;number&gt; | Promise used to return the result.<br>The return value is bound to the SIM card and increases from 1.<br>The return value is **-1** if no SIM card is detected.|

**Error codes**

For details about the error codes, see [Telephony Error Codes](errorcode-telephony.md).

| ID|                 Error Message                    |
| -------- | -------------------------------------------- |
| 8300001  | Invalid parameter value.                     |
| 8300002  | Operation failed. Cannot connect to service. |
| 8300003  | System internal error.                       |
| 8300004  | Do not have sim card.                        |
| 8300999  | Unknown error code.                          |
| 8301001  | SIM card is not activated.                   |

**Example**

```ts
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

let promise = sms.getDefaultSmsSimId();
promise.then((data: number) => {
    console.info(`getDefaultSmsSimId success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`getDefaultSmsSimId failed, promise: errCode:${err.code},errMsg:${err.message}`);
});
```


## ShortMessage

Defines an SMS message instance.

**System capability**: SystemCapability.Telephony.SmsMms

|         Name            |                  Type                  | Read-Only | Optional| Description                                                        |
| ------------------------ | --------------------------------------- | ---- | ---- | ------------------------------------------------------------ |
| hasReplyPath             | boolean                                 |  No |  No | Whether the received SMS contains **TP-Reply-Path**. The default value is **false**.<br>- **true**: yes<br>- **false**: no<br>**TP-Reply-Path**: The device returns a response based on the SMSC that sends the SMS message. |
| isReplaceMessage         | boolean                                 |  No |  No | Whether the received SMS message is a **replace short message**. The default value is **false**.<br>- **true**: yes<br>- **false**: no<br>For details, see [3GPP TS 23.040 9.2.3.9](https://www.3gpp.org/ftp/specs/archive/23_series/23.040).|
| isSmsStatusReportMessage | boolean                                 |  No |  No | Whether the received SMS message is an SMS delivery report. The default value is **false**.<br>- **true**: yes<br>- **false**: no<br>SMS delivery report: a message sent from the SMSC to show the current status of the SMS message you delivered.|
| messageClass             | [ShortMessageClass](#shortmessageclass) |  No |  No | Enumerates SMS message types.                                                  |
| pdu                      | Array&lt;number&gt;                     |  No |  No | PDU in the SMS message.                           |
| protocolId               | number                                  |  No |  No | Protocol identifier used for delivering the SMS message.                                  |
| scAddress                | string                                  |  No |  No | SMSC address.                                |
| scTimestamp              | number                                  |  No |  No | SMSC timestamp, in milliseconds. Number of milliseconds since the UTC time.         |
| status                   | number                                  |  No |  No | SMS message status sent by the SMSC in the **SMS-STATUS-REPORT** message.|
| visibleMessageBody       | string                                  |  No |  No | SMS message body.                                                  |
| visibleRawAddress        | string                                  |  No |  No | Sender address.                                                |


## ShortMessageClass

Enumerates SMS message types.

**System capability**: SystemCapability.Telephony.SmsMms

| Name            | Value  | Description                                    |
| ---------------- | ---- | ---------------------------------------- |
| UNKNOWN          | 0    | Unknown type.                              |
| INSTANT_MESSAGE  | 1    | Instant message, which is displayed immediately after being received.              |
| OPTIONAL_MESSAGE | 2    | Message stored in the device or SIM card.             |
| SIM_MESSAGE      | 3    | Message containing SIM card information, which is to be stored in the SIM card.|
| FORWARD_MESSAGE  | 4    | Message to be forwarded to another device.              |


## SendMessageOptions

Provides the options (including callbacks) for sending SMS messages. For example, you can specify the SMS message type by the optional parameter **content**.

**System capability**: SystemCapability.Telephony.SmsMms

|       Name      | Type                                                        | Read-Only| Optional| Description                                                        |
| ---------------- | ------------------------------------------------------------ | ---- | ---- | ------------------------------------------------------------ |
| slotId           | number                                                       |  No |  No | Slot ID of the SIM card used for sending SMS messages. <br>- **0**: card slot 1<br>- **1**: card slot 2    |
| destinationHost  | string                                                       |  No |  No | Destination address of an SMS message. The value is a mobile number with a country code, for example, **+861xxxxxxxxxx**.    |
| content          | string \| Array&lt;number&gt;                                |  No |  No | SMS message type. If the content is composed of character strings, the SMS message is a text message. If the content is composed of byte arrays, the SMS message is a data message.|
| serviceCenter    | string                                                       |  No |  Yes | SMS center address. The value is a mobile number with a country code, By default, the SMSC address in the SIM card is used.    |
| destinationPort  | number                                                       |  No |  Yes | Destination port of the SMS message. This field is mandatory only for a data message. Otherwise, this field is optional. If this field is not passed, the data port is not set. |
| sendCallback     | AsyncCallback&lt;[ISendShortMessageCallback](#isendshortmessagecallback)&gt; |  No |  Yes | Callback used to return the SMS message sending result. For details, see [ISendShortMessageCallback](#isendshortmessagecallback). This parameter is mandatory when a data SMS message is sent. It is optional when a text SMS message is sent. If this parameter is not set, the callback notification of the SMS message sending result will not be received.|
| deliveryCallback | AsyncCallback&lt;[IDeliveryShortMessageCallback](#ideliveryshortmessagecallback)&gt; |  No |  Yes | Callback used to return the SMS message delivery report. For details, see [IDeliveryShortMessageCallback](#ideliveryshortmessagecallback). This parameter is mandatory when a data SMS message is sent. When a text SMS message is sent, this parameter is optional. If this parameter is not set, the callback notification of the SMS message delivery report will not be received.|



## ISendShortMessageCallback

Provides the callback for the SMS message sending result. It consists of three parts: SMS message sending result, URI for storing the sent SMS message, and whether the SMS message is the last part of a long SMS message.

**System capability**: SystemCapability.Telephony.SmsMms

|   Name    | Type                           | Read-Only| Optional|                                               Description                                        |
| ---------- | ------------------------------- | ---- | ---- | ----------------------------------------------------------------------------------------- |
| isLastPart | boolean                         | No  | No  | Whether this SMS message is the last part of a long SMS message. The default value is **false**.<br>- **true**: yes<br>- **false**: no<br>|
| result     | [SendSmsResult](#sendsmsresult) | No  | No  | SMS message sending result.                                                                            |
| url        | string                          | No  | No  | URI for storing the sent SMS message.                                                                       |


## IDeliveryShortMessageCallback

Provides the callback for the SMS message delivery report.

**System capability**: SystemCapability.Telephony.SmsMms

| Name| Type               | Read-Only| Optional| Description          |
| ---- | ------------------- | ---- | ---- | -------------- |
| pdu  | Array&lt;number&gt; | No  | No  | SMS message delivery report.|


## SendSmsResult

Enumerates SMS message sending results.

**System capability**: SystemCapability.Telephony.SmsMms

| Name                                | Value  | Description                                                  |
| ------------------------------------ | ---- | ------------------------------------------------------ |
| SEND_SMS_SUCCESS                     | 0    | The SMS message is sent successfully.                                        |
| SEND_SMS_FAILURE_UNKNOWN             | 1    | Failed to send the SMS message due to an unknown reason.                              |
| SEND_SMS_FAILURE_RADIO_OFF           | 2    | Failed to send the SMS message because the modem is shut down.                  |
| SEND_SMS_FAILURE_SERVICE_UNAVAILABLE | 3    | Failed to send the SMS message because the network is unavailable or SMS message sending or receiving is not supported.|
