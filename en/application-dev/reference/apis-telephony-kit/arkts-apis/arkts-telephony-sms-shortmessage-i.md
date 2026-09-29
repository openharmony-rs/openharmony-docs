# ShortMessage

```TypeScript
export interface ShortMessage
```

Defines an SMS message instance.

**Since:** 6

<!--Device-sms-export interface ShortMessage--><!--Device-sms-export interface ShortMessage-End-->

**System capability:** SystemCapability.Telephony.SmsMms

## Modules to Import

```TypeScript
import { sms } from '@kit.TelephonyKit';
```

## hasReplyPath

```TypeScript
hasReplyPath: boolean
```

Whether the received SMS contains **TP-Reply-Path**. The default value is **false**.

- **true**: yes  
- **false**: no

**TP-Reply-Path**: The device returns a response based on the SMSC that sends the SMS message.

**Type:** boolean

**Since:** 6

<!--Device-ShortMessage-hasReplyPath: boolean--><!--Device-ShortMessage-hasReplyPath: boolean-End-->

**System capability:** SystemCapability.Telephony.SmsMms

## isReplaceMessage

```TypeScript
isReplaceMessage: boolean
```

Whether the received SMS message is a **replace short message**. The default value is **false**.

- **true**: yes  
- **false**: no

For details, see [3GPP TS 23.040 9.2.3.9](https://www.3gpp.org/ftp/specs/archive/23_series/23.040).

**Type:** boolean

**Since:** 6

<!--Device-ShortMessage-isReplaceMessage: boolean--><!--Device-ShortMessage-isReplaceMessage: boolean-End-->

**System capability:** SystemCapability.Telephony.SmsMms

## isSmsStatusReportMessage

```TypeScript
isSmsStatusReportMessage: boolean
```

Whether the received SMS message is an SMS delivery report. The default value is **false**.

- **true**: yes  
- **false**: no

SMS delivery report: a message sent from the SMSC to show the current status of the SMS message you delivered.

**Type:** boolean

**Since:** 6

<!--Device-ShortMessage-isSmsStatusReportMessage: boolean--><!--Device-ShortMessage-isSmsStatusReportMessage: boolean-End-->

**System capability:** SystemCapability.Telephony.SmsMms

## messageClass

```TypeScript
messageClass: ShortMessageClass
```

Enumerates SMS message types.

**Type:** [ShortMessageClass](arkts-telephony-sms-shortmessageclass-e.md)

**Since:** 6

<!--Device-ShortMessage-messageClass: ShortMessageClass--><!--Device-ShortMessage-messageClass: ShortMessageClass-End-->

**System capability:** SystemCapability.Telephony.SmsMms

## pdu

```TypeScript
pdu: Array<number>
```

PDU in the SMS message.

**Type:** Array&lt;number&gt;

**Since:** 6

<!--Device-ShortMessage-pdu: Array<int>--><!--Device-ShortMessage-pdu: Array<int>-End-->

**System capability:** SystemCapability.Telephony.SmsMms

## protocolId

```TypeScript
protocolId: number
```

Protocol identifier used for delivering the SMS message.

**Type:** number

**Since:** 6

<!--Device-ShortMessage-protocolId: int--><!--Device-ShortMessage-protocolId: int-End-->

**System capability:** SystemCapability.Telephony.SmsMms

## scAddress

```TypeScript
scAddress: string
```

SMSC address.

**Type:** string

**Since:** 6

<!--Device-ShortMessage-scAddress: string--><!--Device-ShortMessage-scAddress: string-End-->

**System capability:** SystemCapability.Telephony.SmsMms

## scTimestamp

```TypeScript
scTimestamp: number
```

SMSC timestamp.

**Type:** number

**Since:** 6

<!--Device-ShortMessage-scTimestamp: long--><!--Device-ShortMessage-scTimestamp: long-End-->

**System capability:** SystemCapability.Telephony.SmsMms

## status

```TypeScript
status: number
```

SMS message status sent by the SMSC in the **SMS-STATUS-REPORT** message.

**Type:** number

**Since:** 6

<!--Device-ShortMessage-status: int--><!--Device-ShortMessage-status: int-End-->

**System capability:** SystemCapability.Telephony.SmsMms

## visibleMessageBody

```TypeScript
visibleMessageBody: string
```

SMS message body.

**Type:** string

**Since:** 6

<!--Device-ShortMessage-visibleMessageBody: string--><!--Device-ShortMessage-visibleMessageBody: string-End-->

**System capability:** SystemCapability.Telephony.SmsMms

## visibleRawAddress

```TypeScript
visibleRawAddress: string
```

Sender address.

**Type:** string

**Since:** 6

<!--Device-ShortMessage-visibleRawAddress: string--><!--Device-ShortMessage-visibleRawAddress: string-End-->

**System capability:** SystemCapability.Telephony.SmsMms
