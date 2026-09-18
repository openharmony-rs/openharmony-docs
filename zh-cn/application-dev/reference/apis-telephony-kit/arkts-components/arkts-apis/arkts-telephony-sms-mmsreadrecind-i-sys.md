# MmsReadRecInd（系统接口）

彩信读取记录索引。

**起始版本：** 8

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { sms } from '@kit.TelephonyKit';
```

## date

```TypeScript
date?: number
```

日期

**类型：** number

**起始版本：** 8

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

## from

```TypeScript
from: MmsAddress
```

来源

**类型：** [MmsAddress](arkts-telephony-sms-mmsaddress-i-sys.md)

**起始版本：** 8

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

## messageId

```TypeScript
messageId: string
```

消息ID

**类型：** string

**起始版本：** 8

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

## readStatus

```TypeScript
readStatus: number
```

阅读状态

**类型：** number

**起始版本：** 8

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

## to

```TypeScript
to: Array<MmsAddress>
```

发送至

**类型：** Array&lt;[MmsAddress](arkts-telephony-sms-mmsaddress-i-sys.md)&gt;

**起始版本：** 8

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

## version

```TypeScript
version: MmsVersionType
```

版本

**类型：** [MmsVersionType](arkts-telephony-sms-mmsversiontype-e-sys.md)

**起始版本：** 8

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。
