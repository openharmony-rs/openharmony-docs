# SystemUpdateInfo

待更新的系统版本信息。

**起始版本：** 12

<!--Device-systemManager-export interface SystemUpdateInfo--><!--Device-systemManager-export interface SystemUpdateInfo-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## 导入模块

```TypeScript
import { systemManager } from '@kit.MDMKit';
```

## firstReceivedTime

```TypeScript
firstReceivedTime: number
```

第一次收到系统更新包的时间（单位：秒）。单位为： 秒，取值应为≥0的整数。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SystemUpdateInfo-firstReceivedTime: number--><!--Device-SystemUpdateInfo-firstReceivedTime: number-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## packageType

```TypeScript
packageType: string
```

待更新的系统更新包类型，类型分为normal和patch类型。

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SystemUpdateInfo-packageType: string--><!--Device-SystemUpdateInfo-packageType: string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## versionName

```TypeScript
versionName: string
```

待更新的系统版本名称。

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SystemUpdateInfo-versionName: string--><!--Device-SystemUpdateInfo-versionName: string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

