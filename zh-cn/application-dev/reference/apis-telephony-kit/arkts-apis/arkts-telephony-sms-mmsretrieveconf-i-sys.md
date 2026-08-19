# MmsRetrieveConf（系统接口）

彩信检索配置。

**起始版本：** 23

<!--Device-sms-export interface MmsRetrieveConf--><!--Device-sms-export interface MmsRetrieveConf-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { sms } from '@kit.TelephonyKit';
```

## cc

```TypeScript
cc?: Array<MmsAddress>
```

抄送

**类型：** Array&lt;[MmsAddress](arkts-telephony-sms-mmsaddress-i-sys.md)&gt;

**起始版本：** 23

<!--Device-MmsRetrieveConf-cc?: Array<MmsAddress>--><!--Device-MmsRetrieveConf-cc?: Array<MmsAddress>-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

## contentType

```TypeScript
contentType: string
```

内容类型

**类型：** string

**起始版本：** 23

<!--Device-MmsRetrieveConf-contentType: string--><!--Device-MmsRetrieveConf-contentType: string-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

## date

```TypeScript
date: long
```

日期

**类型：** long

**起始版本：** 23

<!--Device-MmsRetrieveConf-date: long--><!--Device-MmsRetrieveConf-date: long-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

## deliveryReport

```TypeScript
deliveryReport?: int
```

状态报告

**类型：** int

**起始版本：** 23

<!--Device-MmsRetrieveConf-deliveryReport?: int--><!--Device-MmsRetrieveConf-deliveryReport?: int-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

## from

```TypeScript
from?: MmsAddress
```

来源

**类型：** [MmsAddress](arkts-telephony-sms-mmsaddress-i-sys.md)

**起始版本：** 23

<!--Device-MmsRetrieveConf-from?: MmsAddress--><!--Device-MmsRetrieveConf-from?: MmsAddress-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

## messageId

```TypeScript
messageId: string
```

消息ID

**类型：** string

**起始版本：** 23

<!--Device-MmsRetrieveConf-messageId: string--><!--Device-MmsRetrieveConf-messageId: string-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

## priority

```TypeScript
priority?: MmsPriorityType
```

优先

**类型：** [MmsPriorityType](arkts-telephony-sms-mmsprioritytype-e-sys.md)

**起始版本：** 23

<!--Device-MmsRetrieveConf-priority?: MmsPriorityType--><!--Device-MmsRetrieveConf-priority?: MmsPriorityType-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

## readReport

```TypeScript
readReport?: int
```

阅读报告

**类型：** int

**起始版本：** 23

<!--Device-MmsRetrieveConf-readReport?: int--><!--Device-MmsRetrieveConf-readReport?: int-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

## retrieveStatus

```TypeScript
retrieveStatus?: int
```

检索状态

**类型：** int

**起始版本：** 23

<!--Device-MmsRetrieveConf-retrieveStatus?: int--><!--Device-MmsRetrieveConf-retrieveStatus?: int-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

## retrieveText

```TypeScript
retrieveText?: string
```

检索文本

**类型：** string

**起始版本：** 23

<!--Device-MmsRetrieveConf-retrieveText?: string--><!--Device-MmsRetrieveConf-retrieveText?: string-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

## subject

```TypeScript
subject?: string
```

主题

**类型：** string

**起始版本：** 23

<!--Device-MmsRetrieveConf-subject?: string--><!--Device-MmsRetrieveConf-subject?: string-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

## to

```TypeScript
to: Array<MmsAddress>
```

发送至

**类型：** Array&lt;[MmsAddress](arkts-telephony-sms-mmsaddress-i-sys.md)&gt;

**起始版本：** 23

<!--Device-MmsRetrieveConf-to: Array<MmsAddress>--><!--Device-MmsRetrieveConf-to: Array<MmsAddress>-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

## transactionId

```TypeScript
transactionId: string
```

事务ID

**类型：** string

**起始版本：** 23

<!--Device-MmsRetrieveConf-transactionId: string--><!--Device-MmsRetrieveConf-transactionId: string-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

## version

```TypeScript
version: MmsVersionType
```

版本

**类型：** [MmsVersionType](arkts-telephony-sms-mmsversiontype-e-sys.md)

**起始版本：** 23

<!--Device-MmsRetrieveConf-version: MmsVersionType--><!--Device-MmsRetrieveConf-version: MmsVersionType-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

