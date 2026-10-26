# AutomationControlControllerInfo（系统接口）

```TypeScript
interface AutomationControlControllerInfo
```

对目标应用具有自动化控制权限的控制方应用信息。

**起始版本：** 26.1.0

<!--Device-abilityAccessCtrl-interface AutomationControlControllerInfo--><!--Device-abilityAccessCtrl-interface AutomationControlControllerInfo-End-->

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

控制方应用的包名。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AutomationControlControllerInfo-bundleName: string--><!--Device-AutomationControlControllerInfo-bundleName: string-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## controllerTokenID

```TypeScript
controllerTokenID: number
```

控制方应用的身份标识。取值限定为整数。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AutomationControlControllerInfo-controllerTokenID: int--><!--Device-AutomationControlControllerInfo-controllerTokenID: int-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。
