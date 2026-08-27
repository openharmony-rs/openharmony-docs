# SendMessageOptions

发送短信的参数和回调。根据SendMessageOptions中的可选参数content的值判断短信类型。

**起始版本：** 6

**系统能力：** SystemCapability.Telephony.SmsMms

## 导入模块

```TypeScript
```

## content

```TypeScript
content: string | Array<number>
```

如果内容是字符串，则这是一条文本短信。如果内容是字节数组，则这是一条数据短信。

**类型：** string \| Array&lt;number&gt;

**起始版本：** 6

**系统能力：** SystemCapability.Telephony.SmsMms

## deliveryCallback

```TypeScript
deliveryCallback?: AsyncCallback<IDeliveryShortMessageCallback>
```

短信送达结果回调，返回短信递送报告，参考[IDeliveryShortMessageCallback](arkts-telephony-sms-ideliveryshortmessagecallback-i.md)。发送数据短信时，此项必填。

**类型：** [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[IDeliveryShortMessageCallback](arkts-telephony-sms-ideliveryshortmessagecallback-i.md)&gt;

**起始版本：** 6

**系统能力：** SystemCapability.Telephony.SmsMms

## destinationHost

```TypeScript
destinationHost: string
```

短信的发送地址。

**类型：** string

**起始版本：** 6

**系统能力：** SystemCapability.Telephony.SmsMms

## destinationPort

```TypeScript
destinationPort?: number
```

如果发送数据消息，destinationPort 是必需的。否则是可选的。

**类型：** number

**起始版本：** 6

**系统能力：** SystemCapability.Telephony.SmsMms

## sendCallback

```TypeScript
sendCallback?: AsyncCallback<ISendShortMessageCallback>
```

短信发送结果回调，返回短信发送的结果，参考[ISendShortMessageCallback](arkts-telephony-sms-isendshortmessagecallback-i.md)。发送数据短信时，此项必填。

**类型：** [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[ISendShortMessageCallback](arkts-telephony-sms-isendshortmessagecallback-i.md)&gt;

**起始版本：** 6

**系统能力：** SystemCapability.Telephony.SmsMms

## serviceCenter

```TypeScript
serviceCenter?: string
```

短信中心地址。默认使用SIM卡中的短信中心地址。

**类型：** string

**起始版本：** 6

**系统能力：** SystemCapability.Telephony.SmsMms

## slotId

```TypeScript
slotId: number
```

用于发送短信的SIM卡槽ID：  
- 0：卡槽1。  
- 1：卡槽2。

**类型：** number

**起始版本：** 6

**系统能力：** SystemCapability.Telephony.SmsMms
