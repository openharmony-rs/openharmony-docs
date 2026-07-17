# PermissionDecisionStatus（系统接口）

权限决策状态枚举。

**起始版本：** 26.0.0

<!--Device-abilityAccessCtrl-export enum PermissionDecisionStatus--><!--Device-abilityAccessCtrl-export enum PermissionDecisionStatus-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## NEED_PERMISSION_DIALOG

```TypeScript
NEED_PERMISSION_DIALOG = 0
```

表示需要弹出权限对话框。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PermissionDecisionStatus-NEED_PERMISSION_DIALOG = 0--><!--Device-PermissionDecisionStatus-NEED_PERMISSION_DIALOG = 0-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## NO_DIALOG_DENIED

```TypeScript
NO_DIALOG_DENIED = 1
```

表示无需弹窗，权限已被用户拒绝。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PermissionDecisionStatus-NO_DIALOG_DENIED = 1--><!--Device-PermissionDecisionStatus-NO_DIALOG_DENIED = 1-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## NO_DIALOG_RESTRICTED

```TypeScript
NO_DIALOG_RESTRICTED = 2
```

表示无需弹窗，权限受系统或策略限制。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PermissionDecisionStatus-NO_DIALOG_RESTRICTED = 2--><!--Device-PermissionDecisionStatus-NO_DIALOG_RESTRICTED = 2-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## NO_DIALOG_GRANTED

```TypeScript
NO_DIALOG_GRANTED = 3
```

表示无需弹窗，权限已授予。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PermissionDecisionStatus-NO_DIALOG_GRANTED = 3--><!--Device-PermissionDecisionStatus-NO_DIALOG_GRANTED = 3-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## NO_DIALOG_NOT_DECLARED

```TypeScript
NO_DIALOG_NOT_DECLARED = 4
```

表示无需弹窗，但权限未声明。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PermissionDecisionStatus-NO_DIALOG_NOT_DECLARED = 4--><!--Device-PermissionDecisionStatus-NO_DIALOG_NOT_DECLARED = 4-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## NO_DIALOG_CLI_PERMISSION_RESOLVED

```TypeScript
NO_DIALOG_CLI_PERMISSION_RESOLVED = 5
```

表示无需弹窗，CLI权限已完成运行时权限解析。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PermissionDecisionStatus-NO_DIALOG_CLI_PERMISSION_RESOLVED = 5--><!--Device-PermissionDecisionStatus-NO_DIALOG_CLI_PERMISSION_RESOLVED = 5-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

