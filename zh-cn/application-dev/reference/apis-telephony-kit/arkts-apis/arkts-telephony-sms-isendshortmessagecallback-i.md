# ISendShortMessageCallback

回调实例。返回短信发送结果、存储已发送短信的URI和是否为长短信的最后一部分。

**起始版本：** 23

<!--Device-sms-export interface ISendShortMessageCallback--><!--Device-sms-export interface ISendShortMessageCallback-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

## 导入模块

```TypeScript
import { sms } from '@kit.TelephonyKit';
```

## isLastPart

```TypeScript
isLastPart: boolean
```

指定这是否是长短信的最后一部分。默认为false。 -true：是 -false：否

**类型：** boolean

**起始版本：** 23

<!--Device-ISendShortMessageCallback-isLastPart: boolean--><!--Device-ISendShortMessageCallback-isLastPart: boolean-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

## result

```TypeScript
result: SendSmsResult
```

短信发送结果。

**类型：** [SendSmsResult](arkts-telephony-sms-sendsmsresult-e.md)

**起始版本：** 23

<!--Device-ISendShortMessageCallback-result: SendSmsResult--><!--Device-ISendShortMessageCallback-result: SendSmsResult-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

## url

```TypeScript
url: string
```

存储发送短信的URI。

**类型：** string

**起始版本：** 23

<!--Device-ISendShortMessageCallback-url: string--><!--Device-ISendShortMessageCallback-url: string-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

