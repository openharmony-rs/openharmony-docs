# CallLogInfo

```TypeScript
interface CallLogInfo
```

通话记录信息。提供通话记录的详细信息，包括通话时长、通话方向（呼入/呼出）、时间戳以及使用的SIM卡槽位。

**起始版本：** 26.1.0

<!--Device-telephonyManager-interface CallLogInfo--><!--Device-telephonyManager-interface CallLogInfo-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## 导入模块

```TypeScript
import { telephonyManager } from '@kit.MDMKit';
```

## createTime

```TypeScript
createTime: number
```

通话记录创建时间（时间戳，单位：秒）。来电时为开始振铃时刻，去电时为拨出时刻。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CallLogInfo-createTime: number--><!--Device-CallLogInfo-createTime: number-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## endTime

```TypeScript
endTime: number
```

通话结束时间（时间戳，单位：秒）。通话未接通时为挂断时间。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CallLogInfo-endTime: number--><!--Device-CallLogInfo-endTime: number-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## isIncoming

```TypeScript
isIncoming: boolean
```

通话方向：**true** 表示来电（呼入），**false** 表示去电（呼出）。

**类型：** boolean

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CallLogInfo-isIncoming: boolean--><!--Device-CallLogInfo-isIncoming: boolean-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## slotId

```TypeScript
slotId: number
```

SIM 卡槽位 ID。0表示卡槽1，1表示卡槽2。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CallLogInfo-slotId: number--><!--Device-CallLogInfo-slotId: number-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## startTime

```TypeScript
startTime: number
```

通话接通时间（时间戳，单位：秒）。通话未接通时为0。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CallLogInfo-startTime: number--><!--Device-CallLogInfo-startTime: number-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## telephoneNumber

```TypeScript
telephoneNumber: string
```

对方电话号码。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CallLogInfo-telephoneNumber: string--><!--Device-CallLogInfo-telephoneNumber: string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager
