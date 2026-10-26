# AutomationControlTargetResult（系统接口）

```TypeScript
interface AutomationControlTargetResult
```

针对指定的控制方应用，对应的被自动化控制应用的信息和控制状态。

**起始版本：** 26.1.0

<!--Device-abilityAccessCtrl-interface AutomationControlTargetResult--><!--Device-abilityAccessCtrl-interface AutomationControlTargetResult-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { abilityAccessCtrl, Context, PermissionRequestResult, Permissions } from '@kit.AbilityKit';
```

## bundleName

```TypeScript
bundleName: string
```

目标被控制应用的包名。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AutomationControlTargetResult-bundleName: string--><!--Device-AutomationControlTargetResult-bundleName: string-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## status

```TypeScript
status: AutomationControlStatus
```

自动化控制状态。

**类型：** [AutomationControlStatus](arkts-ability-abilityaccessctrl-automationcontrolstatus-e-sys.md)

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AutomationControlTargetResult-status: AutomationControlStatus--><!--Device-AutomationControlTargetResult-status: AutomationControlStatus-End-->

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

<!--Device-AutomationControlTargetResult-targetTokenID: int--><!--Device-AutomationControlTargetResult-targetTokenID: int-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。
