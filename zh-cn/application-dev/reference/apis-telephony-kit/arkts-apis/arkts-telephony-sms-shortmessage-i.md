# ShortMessage

短信实例。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-sms-export interface ShortMessage--><!--Device-sms-export interface ShortMessage-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

## hasReplyPath

```TypeScript
hasReplyPath: boolean
```

收到的短信是否包含“TP-Reply-Path”，默认为false。 -true：是 -false：否 “TP-Reply-Path”：设备根据发送SMS消息的短消息中心进行回复。

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ShortMessage-hasReplyPath: boolean--><!--Device-ShortMessage-hasReplyPath: boolean-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

## isReplaceMessage

```TypeScript
isReplaceMessage: boolean
```

收到的短信是否为“替换短信”，默认为false。 -true：是 -false：否 “替换短信”有关详细信息，参见 [“3GPP TS 23.040 9.2.3.9”](https://www.3gpp.org/ftp/specs/archive/23_series/23.040)。

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ShortMessage-isReplaceMessage: boolean--><!--Device-ShortMessage-isReplaceMessage: boolean-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

## isSmsStatusReportMessage

```TypeScript
isSmsStatusReportMessage: boolean
```

当前消息是否为“短信状态报告”，默认为false。 -true：是 -false：否 “短信状态报告”是一种特定格式的短信，被用来从Service Center到Mobile Station传输状态报告。

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ShortMessage-isSmsStatusReportMessage: boolean--><!--Device-ShortMessage-isSmsStatusReportMessage: boolean-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

## messageClass

```TypeScript
messageClass: ShortMessageClass
```

短信类型。

**类型：** [ShortMessageClass](arkts-telephony-sms-shortmessageclass-e.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ShortMessage-messageClass: ShortMessageClass--><!--Device-ShortMessage-messageClass: ShortMessageClass-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

## pdu

```TypeScript
pdu: Array<int>
```

SMS消息中的协议数据单元 (PDU)。

**类型：** Array&lt;int&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ShortMessage-pdu: Array<int>--><!--Device-ShortMessage-pdu: Array<int>-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

## protocolId

```TypeScript
protocolId: int
```

发送短信时使用的协议标识。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ShortMessage-protocolId: int--><!--Device-ShortMessage-protocolId: int-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

## scAddress

```TypeScript
scAddress: string
```

短消息服务中心(SMSC)地址。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ShortMessage-scAddress: string--><!--Device-ShortMessage-scAddress: string-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

## scTimestamp

```TypeScript
scTimestamp: long
```

SMSC时间戳。

**类型：** long

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ShortMessage-scTimestamp: long--><!--Device-ShortMessage-scTimestamp: long-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

## status

```TypeScript
status: int
```

SMS-STATUS-REPORT消息中的短信状态指示短信服务中心(SMSC)发送的短信状态。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ShortMessage-status: int--><!--Device-ShortMessage-status: int-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

## visibleMessageBody

```TypeScript
visibleMessageBody: string
```

短信正文。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ShortMessage-visibleMessageBody: string--><!--Device-ShortMessage-visibleMessageBody: string-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

## visibleRawAddress

```TypeScript
visibleRawAddress: string
```

发送者地址。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-ShortMessage-visibleRawAddress: string--><!--Device-ShortMessage-visibleRawAddress: string-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

