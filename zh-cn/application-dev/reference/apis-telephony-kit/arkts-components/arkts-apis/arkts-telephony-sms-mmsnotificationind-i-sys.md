# MmsNotificationInd（系统接口）

```TypeScript
export interface MmsNotificationInd
```

彩信通知索引。

**起始版本：** 8

<!--Device-sms-export interface MmsNotificationInd--><!--Device-sms-export interface MmsNotificationInd-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { sms } from '@kit.TelephonyKit';
```

## contentClass

```TypeScript
contentClass?: number
```

内容类

**类型：** number

**起始版本：** 8

<!--Device-MmsNotificationInd-contentClass?: int--><!--Device-MmsNotificationInd-contentClass?: int-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

## contentLocation

```TypeScript
contentLocation: string
```

内容位置

**类型：** string

**起始版本：** 8

<!--Device-MmsNotificationInd-contentLocation: string--><!--Device-MmsNotificationInd-contentLocation: string-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

## deliveryReport

```TypeScript
deliveryReport?: number
```

状态报告

**类型：** number

**起始版本：** 8

<!--Device-MmsNotificationInd-deliveryReport?: int--><!--Device-MmsNotificationInd-deliveryReport?: int-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

## expiry

```TypeScript
expiry: number
```

到期

**类型：** number

**起始版本：** 8

<!--Device-MmsNotificationInd-expiry: int--><!--Device-MmsNotificationInd-expiry: int-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

## from

```TypeScript
from?: MmsAddress
```

来源

**类型：** [MmsAddress](arkts-telephony-sms-mmsaddress-i-sys.md)

**起始版本：** 8

<!--Device-MmsNotificationInd-from?: MmsAddress--><!--Device-MmsNotificationInd-from?: MmsAddress-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

## messageClass

```TypeScript
messageClass: number
```

消息类

**类型：** number

**起始版本：** 8

<!--Device-MmsNotificationInd-messageClass: int--><!--Device-MmsNotificationInd-messageClass: int-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

## messageSize

```TypeScript
messageSize: number
```

消息大小

**类型：** number

**起始版本：** 8

<!--Device-MmsNotificationInd-messageSize: long--><!--Device-MmsNotificationInd-messageSize: long-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

## subject

```TypeScript
subject?: string
```

主题

**类型：** string

**起始版本：** 8

<!--Device-MmsNotificationInd-subject?: string--><!--Device-MmsNotificationInd-subject?: string-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

## transactionId

```TypeScript
transactionId: string
```

事务ID

**类型：** string

**起始版本：** 8

<!--Device-MmsNotificationInd-transactionId: string--><!--Device-MmsNotificationInd-transactionId: string-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

## version

```TypeScript
version: MmsVersionType
```

版本

**类型：** [MmsVersionType](arkts-telephony-sms-mmsversiontype-e-sys.md)

**起始版本：** 8

<!--Device-MmsNotificationInd-version: MmsVersionType--><!--Device-MmsNotificationInd-version: MmsVersionType-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。
