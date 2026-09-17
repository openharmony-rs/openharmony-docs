# MmsParams（系统接口）

发送彩信的参数。

**起始版本：** 11

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { sms } from '@kit.TelephonyKit';
```

## data

```TypeScript
data: string
```

彩信PDU地址。

**类型：** string

**起始版本：** 11

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

## mmsc

```TypeScript
mmsc: string
```

彩信中心地址。

**类型：** string

**起始版本：** 11

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

## mmsConfig

```TypeScript
mmsConfig?: MmsConfig
```

彩信配置文件，参考[MmsConfig](arkts-telephony-sms-mmsconfig-i-sys.md)。

**类型：** [MmsConfig](arkts-telephony-sms-mmsconfig-i-sys.md)

**起始版本：** 11

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

## slotId

```TypeScript
slotId: number
```

用于发送短信的SIM卡槽ID：

- 0：卡槽1  
- 1：卡槽2

**类型：** number

**起始版本：** 11

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。
