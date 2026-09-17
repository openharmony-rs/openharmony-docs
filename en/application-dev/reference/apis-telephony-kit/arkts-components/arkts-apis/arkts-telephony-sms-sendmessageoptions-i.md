# SendMessageOptions

Provides the options (including callbacks) for sending SMS messages. For example, you can specify the SMS message type by the optional parameter **content**.

**Since:** 6

**System capability:** SystemCapability.Telephony.SmsMms

## Modules to Import

```TypeScript
import { sms } from '@kit.TelephonyKit';
```

## content

```TypeScript
content: string | Array<number>
```

SMS message type. If the content is composed of character strings, the SMS message is a text message. If the content is composed of byte arrays, the SMS message is a data message.

**Type:** string &#124; Array&lt;number&gt;

**Since:** 6

**System capability:** SystemCapability.Telephony.SmsMms

## deliveryCallback

```TypeScript
deliveryCallback?: AsyncCallback<IDeliveryShortMessageCallback>
```

Callback used to return the SMS message delivery report. For details, see [IDeliveryShortMessageCallback](arkts-telephony-sms-ideliveryshortmessagecallback-i.md). This parameter is mandatory for sending an SMS message.

**Type:** [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[IDeliveryShortMessageCallback](arkts-telephony-sms-ideliveryshortmessagecallback-i.md)&gt;

**Since:** 6

**System capability:** SystemCapability.Telephony.SmsMms

## destinationHost

```TypeScript
destinationHost: string
```

Destination address of the SMS message.

**Type:** string

**Since:** 6

**System capability:** SystemCapability.Telephony.SmsMms

## destinationPort

```TypeScript
destinationPort?: number
```

Destination port of the SMS message. This field is mandatory only for a data message. Otherwise, it is optional.

**Type:** number

**Since:** 6

**System capability:** SystemCapability.Telephony.SmsMms

## sendCallback

```TypeScript
sendCallback?: AsyncCallback<ISendShortMessageCallback>
```

Callback used to return the SMS message sending result. For details, see [ISendShortMessageCallback](arkts-telephony-sms-isendshortmessagecallback-i.md). This parameter is mandatory for sending an SMS message.

**Type:** [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[ISendShortMessageCallback](arkts-telephony-sms-isendshortmessagecallback-i.md)&gt;

**Since:** 6

**System capability:** SystemCapability.Telephony.SmsMms

## serviceCenter

```TypeScript
serviceCenter?: string
```

SMSC address. By default, the SMSC address in the SIM card is used.

**Type:** string

**Since:** 6

**System capability:** SystemCapability.Telephony.SmsMms

## slotId

```TypeScript
slotId: number
```

Slot ID of the SIM card used for sending SMS messages.

- **0**: card slot 1.  
- **1**: card slot 2

**Type:** number

**Since:** 6

**System capability:** SystemCapability.Telephony.SmsMms
