# SmsMessageInfo

```TypeScript
interface SmsMessageInfo
```

短信消息信息。提供短信的详细信息，包括消息内容、发送方/接收方信息、时间戳以及使用的SIM卡槽位。

**起始版本：** 26.1.0

<!--Device-telephonyManager-interface SmsMessageInfo--><!--Device-telephonyManager-interface SmsMessageInfo-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## 导入模块

```TypeScript
import { telephonyManager } from '@kit.MDMKit';
```

## content

```TypeScript
content: string
```

短信内容。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SmsMessageInfo-content: string--><!--Device-SmsMessageInfo-content: string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## isSender

```TypeScript
isSender: boolean
```

短信方向：**true** 表示发送，**false** 表示接收。

**类型：** boolean

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SmsMessageInfo-isSender: boolean--><!--Device-SmsMessageInfo-isSender: boolean-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## telephoneNumber

```TypeScript
telephoneNumber: string
```

对方电话号码。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SmsMessageInfo-telephoneNumber: string--><!--Device-SmsMessageInfo-telephoneNumber: string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## time

```TypeScript
time: number
```

短信接收/发送时间（毫秒时间戳）。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SmsMessageInfo-time: number--><!--Device-SmsMessageInfo-time: number-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager
