# ShortMessage

短信实例。

**起始版本：** 6

**系统能力：** SystemCapability.Telephony.SmsMms

## 导入模块

```TypeScript
import { sms } from '@kit.TelephonyKit';
```

## hasReplyPath

```TypeScript
hasReplyPath: boolean
```

收到的短信是否包含“TP-Reply-Path”，默认为false。

-true：是

-false：否

“TP-Reply-Path”：设备根据发送SMS消息的短消息中心进行回复。

**类型：** boolean

**起始版本：** 6

**系统能力：** SystemCapability.Telephony.SmsMms

## isReplaceMessage

```TypeScript
isReplaceMessage: boolean
```

收到的短信是否为“替换短信”，默认为false。

-true：是

-false：否

“替换短信”有关详细信息，参见 [“3GPP TS 23.040 9.2.3.9”](https://www.3gpp.org/ftp/specs/archive/23_series/23.040)。

**类型：** boolean

**起始版本：** 6

**系统能力：** SystemCapability.Telephony.SmsMms

## isSmsStatusReportMessage

```TypeScript
isSmsStatusReportMessage: boolean
```

当前消息是否为“短信状态报告”，默认为false。

-true：是

-false：否

“短信状态报告”是一种特定格式的短信，被用来从Service Center到Mobile Station传输状态报告。

**类型：** boolean

**起始版本：** 6

**系统能力：** SystemCapability.Telephony.SmsMms

## messageClass

```TypeScript
messageClass: ShortMessageClass
```

短信类型。

**类型：** [ShortMessageClass](arkts-telephony-sms-shortmessageclass-e.md)

**起始版本：** 6

**系统能力：** SystemCapability.Telephony.SmsMms

## pdu

```TypeScript
pdu: Array<number>
```

SMS消息中的协议数据单元 (PDU)。

**类型：** Array&lt;number&gt;

**起始版本：** 6

**系统能力：** SystemCapability.Telephony.SmsMms

## protocolId

```TypeScript
protocolId: number
```

发送短信时使用的协议标识。

**类型：** number

**起始版本：** 6

**系统能力：** SystemCapability.Telephony.SmsMms

## scAddress

```TypeScript
scAddress: string
```

短消息服务中心(SMSC)地址。

**类型：** string

**起始版本：** 6

**系统能力：** SystemCapability.Telephony.SmsMms

## scTimestamp

```TypeScript
scTimestamp: number
```

SMSC时间戳。

**类型：** number

**起始版本：** 6

**系统能力：** SystemCapability.Telephony.SmsMms

## status

```TypeScript
status: number
```

SMS-STATUS-REPORT消息中的短信状态指示短信服务中心(SMSC)发送的短信状态。

**类型：** number

**起始版本：** 6

**系统能力：** SystemCapability.Telephony.SmsMms

## visibleMessageBody

```TypeScript
visibleMessageBody: string
```

短信正文。

**类型：** string

**起始版本：** 6

**系统能力：** SystemCapability.Telephony.SmsMms

## visibleRawAddress

```TypeScript
visibleRawAddress: string
```

发送者地址。

**类型：** string

**起始版本：** 6

**系统能力：** SystemCapability.Telephony.SmsMms
