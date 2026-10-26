# abilityAccessCtrl（程序访问控制管理）

```TypeScript
declare namespace abilityAccessCtrl
```

提供应用程序的权限校验和管理能力，支持应用在访问受保护资源前进行权限状态判断、运行时授权申请、设置页授权引导和权限状态变化监听。

**起始版本：** 8

**模型约束：** 此接口可在Stage模型和FA模型下使用。

<!--Device-unnamed-declare namespace abilityAccessCtrl--><!--Device-unnamed-declare namespace abilityAccessCtrl-End-->

**系统能力：** SystemCapability.Security.AccessToken

## 导入模块

```TypeScript
import { abilityAccessCtrl, Context, PermissionRequestResult, Permissions } from '@kit.AbilityKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createAtManager](arkts-ability-abilityaccessctrl-createatmanager-f.md#createatmanager-1) | 创建程序访问控制管理实例，用于权限校验、运行时权限申请、设置页授权引导和权限状态变化监听等场景。调用成功后返回AtManager实例，可用于后续的权限管理操作。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [AtManager](arkts-ability-abilityaccessctrl-atmanager-i.md) | 程序访问控制管理类，提供权限校验、运行时权限弹窗申请、设置页授权引导、全局开关请求和权限状态监听等能力。通过[createAtManager](arkts-ability-abilityaccessctrl-createatmanager-f.md)获取实例。 |
| [PermissionStateChangeInfo](arkts-ability-abilityaccessctrl-permissionstatechangeinfo-i.md) | 表示某次权限授权状态变化的详情。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AtManager](arkts-ability-abilityaccessctrl-atmanager-i-sys.md) | 程序访问控制管理类，提供权限校验、运行时权限弹窗申请、设置页授权引导、全局开关请求和权限状态监听等能力。通过[createAtManager](arkts-ability-abilityaccessctrl-createatmanager-f.md)获取实例。 |
| [AutomationControlControllerInfo](arkts-ability-abilityaccessctrl-automationcontrolcontrollerinfo-i-sys.md) | 对目标应用具有自动化控制权限的控制方应用信息。 |
| [AutomationControlTargetParam](arkts-ability-abilityaccessctrl-automationcontroltargetparam-i-sys.md) | 表示目标应用及其自动化控制状态。 |
| [AutomationControlTargetResult](arkts-ability-abilityaccessctrl-automationcontroltargetresult-i-sys.md) | 针对指定的控制方应用，对应的被自动化控制应用的信息和控制状态。 |
| [PermissionStatusInfo](arkts-ability-abilityaccessctrl-permissionstatusinfo-i-sys.md) | 表示权限状态信息。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [GrantStatus](arkts-ability-abilityaccessctrl-grantstatus-e.md) | 表示授权状态的枚举。 |
| [PermissionStateChangeType](arkts-ability-abilityaccessctrl-permissionstatechangetype-e.md) | 程序访问控制提供应用程序的权限校验和管理能力，支持应用在访问受保护资源前进行权限状态判断、运行时授权申请、设置页授权引导和权限状态变化监听。权限分为system_grant（系统自动授权）、user_grant（需用户手动授权）和manual_settings（手动设置授权）三类，应用需在配置文件中声明所需权限。权限管理机制详见[应用权限管控概述](../../../security/AccessToken/app-permission-mgmt-overview.md)。 |
| [PermissionStatus](arkts-ability-abilityaccessctrl-permissionstatus-e.md) | 程序访问控制提供应用程序的权限校验和管理能力，支持应用在访问受保护资源前进行权限状态判断、运行时授权申请、设置页授权引导和权限状态变化监听。权限分为system_grant（系统自动授权）、user_grant（需用户手动授权）和manual_settings（手动设置授权）三类，应用需在配置文件中声明所需权限。权限管理机制详见[应用权限管控概述](../../../security/AccessToken/app-permission-mgmt-overview.md)。 |
| [SelectedResult](arkts-ability-abilityaccessctrl-selectedresult-e.md) | 程序访问控制提供应用程序的权限校验和管理能力，支持应用在访问受保护资源前进行权限状态判断、运行时授权申请、设置页授权引导和权限状态变化监听。权限分为system_grant（系统自动授权）、user_grant（需用户手动授权）和manual_settings（手动设置授权）三类，应用需在配置文件中声明所需权限。权限管理机制详见[应用权限管控概述](../../../security/AccessToken/app-permission-mgmt-overview.md)。 |
| [SwitchType](arkts-ability-abilityaccessctrl-switchtype-e.md) | 程序访问控制提供应用程序的权限校验和管理能力，支持应用在访问受保护资源前进行权限状态判断、运行时授权申请、设置页授权引导和权限状态变化监听。权限分为system_grant（系统自动授权）、user_grant（需用户手动授权）和manual_settings（手动设置授权）三类，应用需在配置文件中声明所需权限。权限管理机制详见[应用权限管控概述](../../../security/AccessToken/app-permission-mgmt-overview.md)。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AutomationControlSetResult](arkts-ability-abilityaccessctrl-automationcontrolsetresult-e-sys.md) | 设置目标应用自动化控制状态结果的枚举。 |
| [AutomationControlStatus](arkts-ability-abilityaccessctrl-automationcontrolstatus-e-sys.md) | 自动化控制开关状态值。 |
| [PermissionRequestToggleStatus](arkts-ability-abilityaccessctrl-permissionrequesttogglestatus-e-sys.md) | 程序访问控制提供应用程序的权限校验和管理能力，支持应用在访问受保护资源前进行权限状态判断、运行时授权申请、设置页授权引导和权限状态变化监听。权限分为system_grant（系统自动授权）、user_grant（需用户手动授权）和manual_settings（手动设置授权）三类，应用需在配置文件中声明所需权限。权限管理机制详见[应用权限管控概述](../../../security/AccessToken/app-permission-mgmt-overview.md)。 |
<!--DelEnd-->
