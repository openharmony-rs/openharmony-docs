# CBConfigListConfigs（系统接口）

定义小区广播列表配置

**起始版本：** 23

<!--Device-sms-export interface CBConfigListConfigs--><!--Device-sms-export interface CBConfigListConfigs-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { sms } from '@kit.TelephonyKit';
```

## messageIds

```TypeScript
messageIds: int[]
```

定义当前小区广播列表的消息号

**类型：** int[]

**起始版本：** 23

<!--Device-CBConfigListConfigs-messageIds: int[]--><!--Device-CBConfigListConfigs-messageIds: int[]-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

## ranType

```TypeScript
ranType: RanType
```

定义当前小区广播列表接入网类型

**类型：** [RanType](arkts-telephony-sms-rantype-e-sys.md)

**起始版本：** 23

<!--Device-CBConfigListConfigs-ranType: RanType--><!--Device-CBConfigListConfigs-ranType: RanType-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

## slotId

```TypeScript
slotId: int
```

指定当前小区广播配置列表对应的卡槽

**类型：** int

**起始版本：** 23

<!--Device-CBConfigListConfigs-slotId: int--><!--Device-CBConfigListConfigs-slotId: int-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

