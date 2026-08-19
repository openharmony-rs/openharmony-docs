# MmsSendReq（系统接口）

彩信发送请求。

**起始版本：** 23

<!--Device-sms-export interface MmsSendReq--><!--Device-sms-export interface MmsSendReq-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { sms } from '@kit.TelephonyKit';
```

## bcc

```TypeScript
bcc?: Array<MmsAddress>
```

暗抄送

**类型：** Array&lt;[MmsAddress](arkts-telephony-sms-mmsaddress-i-sys.md)&gt;

**起始版本：** 23

<!--Device-MmsSendReq-bcc?: Array<MmsAddress>--><!--Device-MmsSendReq-bcc?: Array<MmsAddress>-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

## cc

```TypeScript
cc?: Array<MmsAddress>
```

抄送

**类型：** Array&lt;[MmsAddress](arkts-telephony-sms-mmsaddress-i-sys.md)&gt;

**起始版本：** 23

<!--Device-MmsSendReq-cc?: Array<MmsAddress>--><!--Device-MmsSendReq-cc?: Array<MmsAddress>-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

## contentType

```TypeScript
contentType: string
```

内容类型

**类型：** string

**起始版本：** 23

<!--Device-MmsSendReq-contentType: string--><!--Device-MmsSendReq-contentType: string-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

## date

```TypeScript
date?: long
```

日期

**类型：** long

**起始版本：** 23

<!--Device-MmsSendReq-date?: long--><!--Device-MmsSendReq-date?: long-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

## deliveryReport

```TypeScript
deliveryReport?: int
```

交付报告

**类型：** int

**起始版本：** 23

<!--Device-MmsSendReq-deliveryReport?: int--><!--Device-MmsSendReq-deliveryReport?: int-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

## expiry

```TypeScript
expiry?: int
```

到期

**类型：** int

**起始版本：** 23

<!--Device-MmsSendReq-expiry?: int--><!--Device-MmsSendReq-expiry?: int-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

## from

```TypeScript
from: MmsAddress
```

彩信来源

**类型：** [MmsAddress](arkts-telephony-sms-mmsaddress-i-sys.md)

**起始版本：** 23

<!--Device-MmsSendReq-from: MmsAddress--><!--Device-MmsSendReq-from: MmsAddress-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

## messageClass

```TypeScript
messageClass?: int
```

消息类

**类型：** int

**起始版本：** 23

<!--Device-MmsSendReq-messageClass?: int--><!--Device-MmsSendReq-messageClass?: int-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

## priority

```TypeScript
priority?: MmsPriorityType
```

优先

**类型：** [MmsPriorityType](arkts-telephony-sms-mmsprioritytype-e-sys.md)

**起始版本：** 23

<!--Device-MmsSendReq-priority?: MmsPriorityType--><!--Device-MmsSendReq-priority?: MmsPriorityType-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

## readReport

```TypeScript
readReport?: int
```

阅读报告

**类型：** int

**起始版本：** 23

<!--Device-MmsSendReq-readReport?: int--><!--Device-MmsSendReq-readReport?: int-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

## senderVisibility

```TypeScript
senderVisibility?: int
```

发件人可见性

**类型：** int

**起始版本：** 23

<!--Device-MmsSendReq-senderVisibility?: int--><!--Device-MmsSendReq-senderVisibility?: int-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

## subject

```TypeScript
subject?: string
```

主题

**类型：** string

**起始版本：** 23

<!--Device-MmsSendReq-subject?: string--><!--Device-MmsSendReq-subject?: string-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

## to

```TypeScript
to?: Array<MmsAddress>
```

发送至

**类型：** Array&lt;[MmsAddress](arkts-telephony-sms-mmsaddress-i-sys.md)&gt;

**起始版本：** 23

<!--Device-MmsSendReq-to?: Array<MmsAddress>--><!--Device-MmsSendReq-to?: Array<MmsAddress>-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

## transactionId

```TypeScript
transactionId: string
```

事务ID

**类型：** string

**起始版本：** 23

<!--Device-MmsSendReq-transactionId: string--><!--Device-MmsSendReq-transactionId: string-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

## version

```TypeScript
version: MmsVersionType
```

版本

**类型：** [MmsVersionType](arkts-telephony-sms-mmsversiontype-e-sys.md)

**起始版本：** 23

<!--Device-MmsSendReq-version: MmsVersionType--><!--Device-MmsSendReq-version: MmsVersionType-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

