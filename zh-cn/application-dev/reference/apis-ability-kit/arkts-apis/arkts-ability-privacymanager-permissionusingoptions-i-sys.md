# PermissionUsingOptions（系统接口）

权限使用可选参数集。

**起始版本：** 26.0.0

<!--Device-privacyManager-interface PermissionUsingOptions--><!--Device-privacyManager-interface PermissionUsingOptions-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { privacyManager } from '@kit.AbilityKit';
```

## enhancedIdentity

```TypeScript
enhancedIdentity?: string
```

扩展身份，用于标识调用方的附加身份信息。当需要区分同一应用下不同调用来源的权限使用记录时传入此字段。长度不超过48个字符，调用[startUsingPermission](arkts-ability-privacymanager-startusingpermission-f-sys.md#startusingpermission-1)或[stopUsingPermission](arkts-ability-privacymanager-stopusingpermission-f-sys.md#stopusingpermission-1)时传入超长值会返回错误码12100001。

默认值：空字符串。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PermissionUsingOptions-enhancedIdentity?: string--><!--Device-PermissionUsingOptions-enhancedIdentity?: string-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

