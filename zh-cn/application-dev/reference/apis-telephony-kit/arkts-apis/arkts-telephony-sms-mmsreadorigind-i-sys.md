# MmsReadOrigInd（系统接口）

彩信读取原始索引。

**起始版本：** 23

<!--Device-sms-export interface MmsReadOrigInd--><!--Device-sms-export interface MmsReadOrigInd-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { sms } from '@kit.TelephonyKit';
```

## date

```TypeScript
date: long
```

日期

**类型：** long

**起始版本：** 23

<!--Device-MmsReadOrigInd-date: long--><!--Device-MmsReadOrigInd-date: long-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

## from

```TypeScript
from: MmsAddress
```

来源

**类型：** [MmsAddress](arkts-telephony-sms-mmsaddress-i-sys.md)

**起始版本：** 23

<!--Device-MmsReadOrigInd-from: MmsAddress--><!--Device-MmsReadOrigInd-from: MmsAddress-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

## messageId

```TypeScript
messageId: string
```

消息ID

**类型：** string

**起始版本：** 23

<!--Device-MmsReadOrigInd-messageId: string--><!--Device-MmsReadOrigInd-messageId: string-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

## readStatus

```TypeScript
readStatus: int
```

阅读状态

**类型：** int

**起始版本：** 23

<!--Device-MmsReadOrigInd-readStatus: int--><!--Device-MmsReadOrigInd-readStatus: int-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

## to

```TypeScript
to: Array<MmsAddress>
```

发送至

**类型：** Array&lt;[MmsAddress](arkts-telephony-sms-mmsaddress-i-sys.md)&gt;

**起始版本：** 23

<!--Device-MmsReadOrigInd-to: Array<MmsAddress>--><!--Device-MmsReadOrigInd-to: Array<MmsAddress>-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

## version

```TypeScript
version: MmsVersionType
```

版本

**类型：** [MmsVersionType](arkts-telephony-sms-mmsversiontype-e-sys.md)

**起始版本：** 23

<!--Device-MmsReadOrigInd-version: MmsVersionType--><!--Device-MmsReadOrigInd-version: MmsVersionType-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

