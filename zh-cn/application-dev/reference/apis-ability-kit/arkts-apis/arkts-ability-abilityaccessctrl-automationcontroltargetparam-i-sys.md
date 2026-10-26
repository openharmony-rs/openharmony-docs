# AutomationControlTargetParam（系统接口）

```TypeScript
interface AutomationControlTargetParam
```

表示目标应用及其自动化控制状态。

**起始版本：** 26.1.0

<!--Device-abilityAccessCtrl-interface AutomationControlTargetParam--><!--Device-abilityAccessCtrl-interface AutomationControlTargetParam-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { abilityAccessCtrl, Context, PermissionRequestResult, Permissions } from '@kit.AbilityKit';
```

## status

```TypeScript
status: AutomationControlStatus
```

自动化控制状态。

**类型：** [AutomationControlStatus](arkts-ability-abilityaccessctrl-automationcontrolstatus-e-sys.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AutomationControlTargetParam-status: AutomationControlStatus--><!--Device-AutomationControlTargetParam-status: AutomationControlStatus-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## targetTokenID

```TypeScript
targetTokenID: number
```

目标被控制应用的Token ID。取值限定为整数。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AutomationControlTargetParam-targetTokenID: int--><!--Device-AutomationControlTargetParam-targetTokenID: int-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。
