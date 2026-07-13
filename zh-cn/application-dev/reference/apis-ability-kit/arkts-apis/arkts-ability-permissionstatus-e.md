# PermissionStatus

程序访问控制提供应用程序的权限校验和管理能力，支持应用在访问受保护资源前进行权限状态判断、运行时授权申请、设置页授权引导和权限状态变化监听。权限分为system_grant（系统自动授权）、user_grant（需用户手动授权）和
manual_settings（手动设置授权）三类，应用需在配置文件中声明所需权限。权限管理机制详见[应用权限管控概述](../../../../security/AccessToken/app-permission-mgmt-overview.md)。

该模块主要用于以下场景：

- 在业务执行前校验当前应用是否具备访问受保护资源所需要的权限。
- 在权限未授予时，拉起运行时权限弹窗或权限设置页面，请求用户授权。
- 订阅当前应用的权限状态变化事件，在权限状态变化后及时调整业务流程。

###### 核心枚举类型

- **[GrantStatus](arkts-ability-grantstatus-e.md)：** 权限授权状态枚举，用于表示当前权限的授权状态。
- **[SwitchType](arkts-ability-switchtype-e.md)：** 全局开关类型枚举，用于表示需要请求的系统全局开关类型。
- **[PermissionStateChangeType](arkts-ability-permissionstatechangetype-e.md)：** 权限状态变化类型枚举，用于表示授权、取消授权等变化。
- **[PermissionStatus](arkts-ability-permissionstatus-e.md)：** 权限状态枚举，用于表示当前权限状态。
- **[SelectedResult](arkts-ability-selectedresult-e.md)：** 设置页授权选择结果枚举，用于表示用户在权限设置弹窗中的选择结果。

###### 核心接口类型

- **[PermissionStateChangeInfo](arkts-ability-permissionstatechangeinfo-i.md)：** 权限状态变化事件对象，用于返回变化类型、应用身份标识和权限名。
- **[PermissionRequestResult](arkts-ability-permissionrequestresult-t.md)：** 权限申请结果对象，用于返回权限申请后的权限名列表、授权结果和弹窗展示结果。
- **[Context](arkts-ability-context-t.md)：** 上下文对象，用于发起权限申请或打开权限设置弹窗。

###### 核心类

- **[AtManager](arkts-ability-atmanager-i.md)：** 程序访问控制管理类，提供权限校验、权限弹窗申请、设置页授权引导和权限状态监听等能力。

![image_abilityAccessCtrl](../../../../reference/apis-ability-kit/figures/abilityAccessCtrl.png)

**起始版本：** 20

**系统能力：** SystemCapability.Security.AccessToken

## DENIED

```TypeScript
DENIED = -1
```

表示用户未授权。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.AccessToken

## GRANTED

```TypeScript
GRANTED = 0
```

表示已授权。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.AccessToken

## NOT_DETERMINED

```TypeScript
NOT_DETERMINED = 1
```

表示未操作。应用声明[用户授权权限](permissions:Permissions)但暂未调用
[requestPermissionsFromUser](arkts-ability-atmanager-i.md#requestpermissionsfromuser-1)
接口请求授权，或用户在设置中将权限状态修改为每次询问时，查询权限状态返回此值。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.AccessToken

## INVALID

```TypeScript
INVALID = 2
```

表示无效。应用未[声明权限](../../../../security/AccessToken/declare-permissions.md)或当前无法处理。例如：当模糊位置权限的状态为NOT_DETERMINED时，查询精确位置
权限状态，返回此值。

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.AccessToken

## RESTRICTED

```TypeScript
RESTRICTED = 3
```

表示受限。<!--RP2-->应用被禁止通过[requestPermissionsFromUser](arkts-ability-atmanager-i.md#requestpermissionsfromuser-1)
接口请求用户授权。<!--RP2End-->

**起始版本：** 20

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.AccessToken

