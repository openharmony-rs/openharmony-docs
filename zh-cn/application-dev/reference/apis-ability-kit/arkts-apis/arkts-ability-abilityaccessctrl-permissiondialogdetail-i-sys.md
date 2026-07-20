# PermissionDialogDetail（系统接口）

表示单条命令的权限弹窗信息。

**起始版本：** 26.0.0

<!--Device-abilityAccessCtrl-interface PermissionDialogDetail--><!--Device-abilityAccessCtrl-interface PermissionDialogDetail-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { Context, Permissions, PermissionRequestResult } from '@kit.AbilityKit';
```

## authResult

```TypeScript
authResult: string
```

授权结果字符串。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PermissionDialogDetail-authResult: string--><!--Device-PermissionDialogDetail-authResult: string-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## needPermissionDialog

```TypeScript
needPermissionDialog: boolean
```

当前CLI命令是否需要权限弹窗，true表示需要权限弹窗，false表示不需要权限弹窗。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PermissionDialogDetail-needPermissionDialog: boolean--><!--Device-PermissionDialogDetail-needPermissionDialog: boolean-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## permissionNameList

```TypeScript
permissionNameList: Array<Permissions>
```

发起CLI相关操作的智能体当前未满足的权限名称列表。若相关权限不满足，CLI将无法拉起，或拉起后的CLI进程无法获得对应权限。

**类型：** Array&lt;Permissions&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PermissionDialogDetail-permissionNameList: Array<Permissions>--><!--Device-PermissionDialogDetail-permissionNameList: Array<Permissions>-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## statusList

```TypeScript
statusList: Array<PermissionDecisionStatus>
```

权限决策状态列表。

**类型：** Array&lt;PermissionDecisionStatus&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PermissionDialogDetail-statusList: Array<PermissionDecisionStatus>--><!--Device-PermissionDialogDetail-statusList: Array<PermissionDecisionStatus>-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

