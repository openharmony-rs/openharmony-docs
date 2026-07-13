# CliPermissionDetail（系统接口）

表示CLI指令声明的单个CLI权限的状态信息。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## cliPermissionStatus

```TypeScript
cliPermissionStatus: PermissionDecisionStatus
```

CLI指令声明的CLI权限的决策状态。

**类型：** PermissionDecisionStatus

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

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

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## usedPermissions

```TypeScript
usedPermissions: Array<Permissions>
```

由requiredCliPermission映射出的运行时权限列表。

**类型：** Array<Permissions>

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

