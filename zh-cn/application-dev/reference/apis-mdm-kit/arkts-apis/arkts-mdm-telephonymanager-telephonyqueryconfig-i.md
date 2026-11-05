# TelephonyQueryConfig

```TypeScript
interface TelephonyQueryConfig
```

查询短信和通话记录的选项。提供电话相关查询的通用查询参数。

**起始版本：** 26.1.0

<!--Device-telephonyManager-interface TelephonyQueryConfig--><!--Device-telephonyManager-interface TelephonyQueryConfig-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## 导入模块

```TypeScript
import { telephonyManager } from '@kit.MDMKit';
```

## endTime

```TypeScript
endTime: number
```

查询结束时间（时间戳，单位：秒）。按通话/短信记录创建时间匹配。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TelephonyQueryConfig-endTime: number--><!--Device-TelephonyQueryConfig-endTime: number-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## startTime

```TypeScript
startTime: number
```

查询开始时间（时间戳，单位：秒）。按通话/短信记录创建时间匹配。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TelephonyQueryConfig-startTime: number--><!--Device-TelephonyQueryConfig-startTime: number-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## telephoneNumber

```TypeScript
telephoneNumber?: string
```

要过滤的电话号码（可选）。默认值为空字符串，表示查询时所有记录。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TelephonyQueryConfig-telephoneNumber?: string--><!--Device-TelephonyQueryConfig-telephoneNumber?: string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager
