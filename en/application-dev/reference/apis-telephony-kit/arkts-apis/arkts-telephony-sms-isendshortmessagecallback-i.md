# ISendShortMessageCallback

```TypeScript
export interface ISendShortMessageCallback
```

Provides the callback for the SMS message sending result. It consists of three parts: SMS message sending result, URI for storing the sent SMS message, and whether the SMS message is the last part of a long SMS message.

**Since:** 6

<!--Device-sms-export interface ISendShortMessageCallback--><!--Device-sms-export interface ISendShortMessageCallback-End-->

**System capability:** SystemCapability.Telephony.SmsMms

## Modules to Import

```TypeScript
import { sms } from '@kit.TelephonyKit';
```

## isLastPart

```TypeScript
isLastPart: boolean
```

Whether this SMS message is the last part of a long SMS message. The default value is **false**.

- **true**: yes  
- **false**: no

**Type:** boolean

**Since:** 6

<!--Device-ISendShortMessageCallback-isLastPart: boolean--><!--Device-ISendShortMessageCallback-isLastPart: boolean-End-->

**System capability:** SystemCapability.Telephony.SmsMms

## result

```TypeScript
result: SendSmsResult
```

SMS message sending result.

**Type:** [SendSmsResult](arkts-telephony-sms-sendsmsresult-e.md)

**Since:** 6

<!--Device-ISendShortMessageCallback-result: SendSmsResult--><!--Device-ISendShortMessageCallback-result: SendSmsResult-End-->

**System capability:** SystemCapability.Telephony.SmsMms

## url

```TypeScript
url: string
```

URI for storing the sent SMS message.

**Type:** string

**Since:** 6

<!--Device-ISendShortMessageCallback-url: string--><!--Device-ISendShortMessageCallback-url: string-End-->

**System capability:** SystemCapability.Telephony.SmsMms
