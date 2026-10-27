# ControlAppStatusResult

```TypeScript
interface ControlAppStatusResult
```

应用的相关信息。

**起始版本：** 26.1.0

<!--Device-abilityToolAccessCtrl-interface ControlAppStatusResult--><!--Device-abilityToolAccessCtrl-interface ControlAppStatusResult-End-->

**系统能力：** SystemCapability.Security.Asset

## 导入模块

```TypeScript
import { abilityToolAccessCtrl } from '@kit.AbilityKit';
```

## appInfo

```TypeScript
appInfo: AppInfo
```

应用信息。

**类型：** [AppInfo](arkts-ability-abilitytoolaccessctrl-appinfo-i.md)

**起始版本：** 26.1.0

**模型约束：** 此接口可在Stage模型和FA模型下使用。

<!--Device-ControlAppStatusResult-appInfo: AppInfo--><!--Device-ControlAppStatusResult-appInfo: AppInfo-End-->

**系统能力：** SystemCapability.Security.Asset

## status

```TypeScript
status: ControlAppStatus
```

控制权限状态。

**类型：** [ControlAppStatus](arkts-ability-abilitytoolaccessctrl-controlappstatus-e.md)

**起始版本：** 26.1.0

**模型约束：** 此接口可在Stage模型和FA模型下使用。

<!--Device-ControlAppStatusResult-status: ControlAppStatus--><!--Device-ControlAppStatusResult-status: ControlAppStatus-End-->

**系统能力：** SystemCapability.Security.Asset
