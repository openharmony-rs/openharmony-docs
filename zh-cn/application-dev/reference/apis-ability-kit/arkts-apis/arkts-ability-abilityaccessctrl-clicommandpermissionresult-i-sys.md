# CliCommandPermissionResult（系统接口）

表示单条CLI命令的权限信息。

**起始版本：** 26.0.0

<!--Device-abilityAccessCtrl-interface CliCommandPermissionResult--><!--Device-abilityAccessCtrl-interface CliCommandPermissionResult-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { Context, Permissions, PermissionRequestResult } from '@kit.AbilityKit';
```

## requiredCliPermissions

```TypeScript
requiredCliPermissions: Array<CliPermissionDetail>
```

当前CLI命令依赖的CLI权限信息列表。

**类型：** Array&lt;CliPermissionDetail&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CliCommandPermissionResult-requiredCliPermissions: Array<CliPermissionDetail>--><!--Device-CliCommandPermissionResult-requiredCliPermissions: Array<CliPermissionDetail>-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

