# SendMessageOptions

发送短信的参数和回调。根据SendMessageOptions中的可选参数content的值判断短信类型。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-sms-export interface SendMessageOptions--><!--Device-sms-export interface SendMessageOptions-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

## content

```TypeScript
content: string | Array<int>
```

如果内容是字符串，则这是一条文本短信。如果内容是字节数组，则这是一条数据短信。

**类型：** string \| Array&lt;int&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-SendMessageOptions-content: string | Array<int>--><!--Device-SendMessageOptions-content: string | Array<int>-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

## deliveryCallback

```TypeScript
deliveryCallback?: AsyncCallback<IDeliveryShortMessageCallback>
```

短信送达结果回调，返回短信递送报告，参考[IDeliveryShortMessageCallback](arkts-telephony-sms-ideliveryshortmessagecallback-i.md#IDeliveryShortMessageCallback)。发送数据短信时，此项必填。

**类型：** [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[IDeliveryShortMessageCallback](arkts-telephony-sms-ideliveryshortmessagecallback-i.md)&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-SendMessageOptions-deliveryCallback?: AsyncCallback<IDeliveryShortMessageCallback>--><!--Device-SendMessageOptions-deliveryCallback?: AsyncCallback<IDeliveryShortMessageCallback>-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

## destinationHost

```TypeScript
destinationHost: string
```

短信的发送地址。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-SendMessageOptions-destinationHost: string--><!--Device-SendMessageOptions-destinationHost: string-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

## destinationPort

```TypeScript
destinationPort?: int
```

如果发送数据消息，destinationPort 是必需的。否则是可选的。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-SendMessageOptions-destinationPort?: int--><!--Device-SendMessageOptions-destinationPort?: int-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

## sendCallback

```TypeScript
sendCallback?: AsyncCallback<ISendShortMessageCallback>
```

短信发送结果回调，返回短信发送的结果，参考[ISendShortMessageCallback](arkts-telephony-sms-isendshortmessagecallback-i.md#ISendShortMessageCallback)。发送数据短信时，此项必填。

**类型：** [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[ISendShortMessageCallback](arkts-telephony-sms-isendshortmessagecallback-i.md)&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-SendMessageOptions-sendCallback?: AsyncCallback<ISendShortMessageCallback>--><!--Device-SendMessageOptions-sendCallback?: AsyncCallback<ISendShortMessageCallback>-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

## serviceCenter

```TypeScript
serviceCenter?: string
```

短信中心地址。默认使用SIM卡中的短信中心地址。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-SendMessageOptions-serviceCenter?: string--><!--Device-SendMessageOptions-serviceCenter?: string-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

## slotId

```TypeScript
slotId: int
```

用于发送短信的SIM卡槽ID： - 0：卡槽1。 - 1：卡槽2。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-SendMessageOptions-slotId: int--><!--Device-SendMessageOptions-slotId: int-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

