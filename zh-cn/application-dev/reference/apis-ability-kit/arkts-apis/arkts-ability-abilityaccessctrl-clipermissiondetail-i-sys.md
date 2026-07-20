# CliPermissionDetail（系统接口）

表示CLI指令声明的单个CLI权限的状态信息。

**起始版本：** 26.0.0

<!--Device-abilityAccessCtrl-interface CliPermissionDetail--><!--Device-abilityAccessCtrl-interface CliPermissionDetail-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { Context, Permissions, PermissionRequestResult } from '@kit.AbilityKit';
```

## cliPermissionStatus

```TypeScript
cliPermissionStatus: PermissionDecisionStatus
```

CLI指令声明的CLI权限的决策状态。

**类型：** PermissionDecisionStatus

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CliPermissionDetail-cliPermissionStatus: PermissionDecisionStatus--><!--Device-CliPermissionDetail-cliPermissionStatus: PermissionDecisionStatus-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## requiredCliPermission

```TypeScript
requiredCliPermission: Permissions
```

调用CLI所需的CLI权限。

**类型：** Permissions

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CliPermissionDetail-requiredCliPermission: Permissions--><!--Device-CliPermissionDetail-requiredCliPermission: Permissions-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## usedPermissions

```TypeScript
usedPermissions: Array<Permissions>
```

由requiredCliPermission映射出的运行时权限列表。

**类型：** Array&lt;Permissions&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CliPermissionDetail-usedPermissions: Array<Permissions>--><!--Device-CliPermissionDetail-usedPermissions: Array<Permissions>-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

