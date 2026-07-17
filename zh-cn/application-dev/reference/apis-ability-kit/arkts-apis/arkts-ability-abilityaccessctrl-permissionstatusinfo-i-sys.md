# PermissionStatusInfo（系统接口）

表示权限状态信息。

**起始版本：** 26.0.0

<!--Device-abilityAccessCtrl-interface PermissionStatusInfo--><!--Device-abilityAccessCtrl-interface PermissionStatusInfo-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { Context, Permissions, PermissionRequestResult } from '@kit.AbilityKit';
```

## grantFlags

```TypeScript
grantFlags: number
```

权限标志，取值范围如下：  
- 0：用户未设置该权限。  
- 1：用户已设置该权限，若权限未授予，允许再次弹出权限弹窗请求授权。  
- 2：用户已设置该权限，若权限未授予，不允许再次弹出权限弹窗请求授权，需用户在系统设置中授权。  
- 4：系统已设置该权限。  
- 8：系统已预授权该权限，且允许取消授权。  
- 16：安全控件已设置该权限。  
- 32：安全策略已固定该权限，用户不能授权或取消授权。  
- 64：仅在当前生命周期前台期间允许使用该权限。  
- 128：管理员策略已固定该权限，用户不能授权或取消授权，管理员可取消固定。  
- 256：管理员策略取消固定该权限，用户可授权或取消授权。  
- 512：用户策略限制该权限。取值限定为整数。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PermissionStatusInfo-grantFlags: int--><!--Device-PermissionStatusInfo-grantFlags: int-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## grantStatus

```TypeScript
grantStatus: GrantStatus
```

权限授权状态。

**类型：** GrantStatus

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PermissionStatusInfo-grantStatus: GrantStatus--><!--Device-PermissionStatusInfo-grantStatus: GrantStatus-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## grantTimestamp

```TypeScript
grantTimestamp?: number
```

授权状态变化的时间戳。该字段为可选字段，当权限状态变化时返回。单位为：毫秒。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PermissionStatusInfo-grantTimestamp?: long--><!--Device-PermissionStatusInfo-grantTimestamp?: long-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## permissionName

```TypeScript
permissionName: Permissions
```

权限名称。

**类型：** Permissions

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PermissionStatusInfo-permissionName: Permissions--><!--Device-PermissionStatusInfo-permissionName: Permissions-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

## tokenID

```TypeScript
tokenID: number
```

应用的身份标识。取值限定为整数。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PermissionStatusInfo-tokenID: int--><!--Device-PermissionStatusInfo-tokenID: int-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

