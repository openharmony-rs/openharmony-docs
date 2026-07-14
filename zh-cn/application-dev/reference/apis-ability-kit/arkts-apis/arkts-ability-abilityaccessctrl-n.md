# abilityAccessCtrl

**起始版本：** 8

**系统能力：** SystemCapability.Security.AccessToken

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createAtManager](arkts-ability-createatmanager-f.md#createatmanager-1) | 创建程序访问控制管理实例，用于权限校验、运行时权限申请、设置页授权引导和权限状态变化监听等场景。调用成功后返回AtManager实例，可用于后续的权限管理操作。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [AtManager](arkts-ability-atmanager-i.md) | 程序访问控制管理类，提供权限校验、运行时权限弹窗申请、设置页授权引导、全局开关请求和权限状态监听等能力。通过[createAtManager](arkts-ability-createatmanager-f.md#createatmanager-1)获取实例。 |
| [PermissionStateChangeInfo](arkts-ability-permissionstatechangeinfo-i.md) | 表示某次权限授权状态变化的详情。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AtManager](arkts-ability-atmanager-i-sys.md) | 程序访问控制管理类，提供权限校验、运行时权限弹窗申请、设置页授权引导、全局开关请求和权限状态监听等能力。通过[createAtManager](arkts-ability-createatmanager-f.md#createatmanager-1)获取实例。 |
| [PermissionStatusInfo](arkts-ability-permissionstatusinfo-i-sys.md) | 表示权限状态信息。 |
| [CliInfo](arkts-ability-cliinfo-i-sys.md) | 表示CLI（Command Line Interface，命令行界面）信息。 |
| [PermissionDialogDetail](arkts-ability-permissiondialogdetail-i-sys.md) | 表示单条命令的权限弹窗信息。 |
| [PermissionDialogResult](arkts-ability-permissiondialogresult-i-sys.md) | 表示权限弹窗查询结果。 |
| [CliPermissionDetail](arkts-ability-clipermissiondetail-i-sys.md) | 表示CLI指令声明的单个CLI权限的状态信息。 |
| [CliCommandPermissionResult](arkts-ability-clicommandpermissionresult-i-sys.md) | 表示单条CLI命令的权限信息。 |
| [CliPermissionsResult](arkts-ability-clipermissionsresult-i-sys.md) | 表示CLI权限查询结果。 |
| [CliAuthInfo](arkts-ability-cliauthinfo-i-sys.md) | 程序访问控制提供应用程序的权限校验和管理能力，支持应用在访问受保护资源前进行权限状态判断、运行时授权申请、设置页授权引导和权限状态变化监听。权限分为system_grant（系统自动授权）、user_grant（需用户手动授权）和manual_settings（手动设置授权）三类，应用需在配置文件中声明所需权限。权限管理机制详见[应用权限管控概述](../../../../security/AccessToken/app-permission-mgmt-overview.md)。该模块主要用于以下场景：- 在业务执行前校验当前应用是否具备访问受保护资源所需要的权限。- 在权限未授予时，拉起运行时权限弹窗或权限设置页面，请求用户授权。- 订阅当前应用的权限状态变化事件，在权限状态变化后及时调整业务流程。###### 核心枚举类型- **[GrantStatus](arkts-ability-grantstatus-e.md)：** 权限授权状态枚举，用于表示当前权限的授权状态。- **[SwitchType](arkts-ability-switchtype-e.md)：** 全局开关类型枚举，用于表示需要请求的系统全局开关类型。- **[PermissionStateChangeType](arkts-ability-permissionstatechangetype-e.md)：** 权限状态变化类型枚举，用于表示授权、取消授权等变化。- **[PermissionStatus](arkts-ability-permissionstatus-e.md)：** 权限状态枚举，用于表示当前权限状态。- **[SelectedResult](arkts-ability-selectedresult-e.md)：** 设置页授权选择结果枚举，用于表示用户在权限设置弹窗中的选择结果。###### 核心接口类型- **[PermissionStateChangeInfo](arkts-ability-permissionstatechangeinfo-i.md)：** 权限状态变化事件对象，用于返回变化类型、应用身份标识和权限名。- **[PermissionRequestResult](arkts-ability-permissionrequestresult-t.md)：** 权限申请结果对象，用于返回权限申请后的权限名列表、授权结果和弹窗展示结果。- **[Context](arkts-ability-context-t.md)：** 上下文对象，用于发起权限申请或打开权限设置弹窗。###### 核心类- **[AtManager](arkts-ability-atmanager-i.md)：** 程序访问控制管理类，提供权限校验、权限弹窗申请、设置页授权引导和权限状态监听等能力。![image_abilityAccessCtrl](../../../../reference/apis-ability-kit/figures/abilityAccessCtrl.png) |
| [ToolAuthResult](arkts-ability-toolauthresult-i-sys.md) | 程序访问控制提供应用程序的权限校验和管理能力，支持应用在访问受保护资源前进行权限状态判断、运行时授权申请、设置页授权引导和权限状态变化监听。权限分为system_grant（系统自动授权）、user_grant（需用户手动授权）和manual_settings（手动设置授权）三类，应用需在配置文件中声明所需权限。权限管理机制详见[应用权限管控概述](../../../../security/AccessToken/app-permission-mgmt-overview.md)。该模块主要用于以下场景：- 在业务执行前校验当前应用是否具备访问受保护资源所需要的权限。- 在权限未授予时，拉起运行时权限弹窗或权限设置页面，请求用户授权。- 订阅当前应用的权限状态变化事件，在权限状态变化后及时调整业务流程。###### 核心枚举类型- **[GrantStatus](arkts-ability-grantstatus-e.md)：** 权限授权状态枚举，用于表示当前权限的授权状态。- **[SwitchType](arkts-ability-switchtype-e.md)：** 全局开关类型枚举，用于表示需要请求的系统全局开关类型。- **[PermissionStateChangeType](arkts-ability-permissionstatechangetype-e.md)：** 权限状态变化类型枚举，用于表示授权、取消授权等变化。- **[PermissionStatus](arkts-ability-permissionstatus-e.md)：** 权限状态枚举，用于表示当前权限状态。- **[SelectedResult](arkts-ability-selectedresult-e.md)：** 设置页授权选择结果枚举，用于表示用户在权限设置弹窗中的选择结果。###### 核心接口类型- **[PermissionStateChangeInfo](arkts-ability-permissionstatechangeinfo-i.md)：** 权限状态变化事件对象，用于返回变化类型、应用身份标识和权限名。- **[PermissionRequestResult](arkts-ability-permissionrequestresult-t.md)：** 权限申请结果对象，用于返回权限申请后的权限名列表、授权结果和弹窗展示结果。- **[Context](arkts-ability-context-t.md)：** 上下文对象，用于发起权限申请或打开权限设置弹窗。###### 核心类- **[AtManager](arkts-ability-atmanager-i.md)：** 程序访问控制管理类，提供权限校验、权限弹窗申请、设置页授权引导和权限状态监听等能力。![image_abilityAccessCtrl](../../../../reference/apis-ability-kit/figures/abilityAccessCtrl.png) |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [GrantStatus](arkts-ability-grantstatus-e.md) | 表示授权状态的枚举。 |
| [SelectedResult](arkts-ability-selectedresult-e.md) | 程序访问控制提供应用程序的权限校验和管理能力，支持应用在访问受保护资源前进行权限状态判断、运行时授权申请、设置页授权引导和权限状态变化监听。权限分为system_grant（系统自动授权）、user_grant（需用户手动授权）和manual_settings（手动设置授权）三类，应用需在配置文件中声明所需权限。权限管理机制详见[应用权限管控概述](../../../../security/AccessToken/app-permission-mgmt-overview.md)。该模块主要用于以下场景：- 在业务执行前校验当前应用是否具备访问受保护资源所需要的权限。- 在权限未授予时，拉起运行时权限弹窗或权限设置页面，请求用户授权。- 订阅当前应用的权限状态变化事件，在权限状态变化后及时调整业务流程。###### 核心枚举类型- **[GrantStatus](arkts-ability-grantstatus-e.md)：** 权限授权状态枚举，用于表示当前权限的授权状态。- **[SwitchType](arkts-ability-switchtype-e.md)：** 全局开关类型枚举，用于表示需要请求的系统全局开关类型。- **[PermissionStateChangeType](arkts-ability-permissionstatechangetype-e.md)：** 权限状态变化类型枚举，用于表示授权、取消授权等变化。- **[PermissionStatus](arkts-ability-permissionstatus-e.md)：** 权限状态枚举，用于表示当前权限状态。- **[SelectedResult](arkts-ability-selectedresult-e.md)：** 设置页授权选择结果枚举，用于表示用户在权限设置弹窗中的选择结果。###### 核心接口类型- **[PermissionStateChangeInfo](arkts-ability-permissionstatechangeinfo-i.md)：** 权限状态变化事件对象，用于返回变化类型、应用身份标识和权限名。- **[PermissionRequestResult](arkts-ability-permissionrequestresult-t.md)：** 权限申请结果对象，用于返回权限申请后的权限名列表、授权结果和弹窗展示结果。- **[Context](arkts-ability-context-t.md)：** 上下文对象，用于发起权限申请或打开权限设置弹窗。###### 核心类- **[AtManager](arkts-ability-atmanager-i.md)：** 程序访问控制管理类，提供权限校验、权限弹窗申请、设置页授权引导和权限状态监听等能力。![image_abilityAccessCtrl](../../../../reference/apis-ability-kit/figures/abilityAccessCtrl.png) |
| [PermissionStateChangeType](arkts-ability-permissionstatechangetype-e.md) | 程序访问控制提供应用程序的权限校验和管理能力，支持应用在访问受保护资源前进行权限状态判断、运行时授权申请、设置页授权引导和权限状态变化监听。权限分为system_grant（系统自动授权）、user_grant（需用户手动授权）和manual_settings（手动设置授权）三类，应用需在配置文件中声明所需权限。权限管理机制详见[应用权限管控概述](../../../../security/AccessToken/app-permission-mgmt-overview.md)。该模块主要用于以下场景：- 在业务执行前校验当前应用是否具备访问受保护资源所需要的权限。- 在权限未授予时，拉起运行时权限弹窗或权限设置页面，请求用户授权。- 订阅当前应用的权限状态变化事件，在权限状态变化后及时调整业务流程。###### 核心枚举类型- **[GrantStatus](arkts-ability-grantstatus-e.md)：** 权限授权状态枚举，用于表示当前权限的授权状态。- **[SwitchType](arkts-ability-switchtype-e.md)：** 全局开关类型枚举，用于表示需要请求的系统全局开关类型。- **[PermissionStateChangeType](arkts-ability-permissionstatechangetype-e.md)：** 权限状态变化类型枚举，用于表示授权、取消授权等变化。- **[PermissionStatus](arkts-ability-permissionstatus-e.md)：** 权限状态枚举，用于表示当前权限状态。- **[SelectedResult](arkts-ability-selectedresult-e.md)：** 设置页授权选择结果枚举，用于表示用户在权限设置弹窗中的选择结果。###### 核心接口类型- **[PermissionStateChangeInfo](arkts-ability-permissionstatechangeinfo-i.md)：** 权限状态变化事件对象，用于返回变化类型、应用身份标识和权限名。- **[PermissionRequestResult](arkts-ability-permissionrequestresult-t.md)：** 权限申请结果对象，用于返回权限申请后的权限名列表、授权结果和弹窗展示结果。- **[Context](arkts-ability-context-t.md)：** 上下文对象，用于发起权限申请或打开权限设置弹窗。###### 核心类- **[AtManager](arkts-ability-atmanager-i.md)：** 程序访问控制管理类，提供权限校验、权限弹窗申请、设置页授权引导和权限状态监听等能力。![image_abilityAccessCtrl](../../../../reference/apis-ability-kit/figures/abilityAccessCtrl.png) |
| [PermissionStatus](arkts-ability-permissionstatus-e.md) | 程序访问控制提供应用程序的权限校验和管理能力，支持应用在访问受保护资源前进行权限状态判断、运行时授权申请、设置页授权引导和权限状态变化监听。权限分为system_grant（系统自动授权）、user_grant（需用户手动授权）和manual_settings（手动设置授权）三类，应用需在配置文件中声明所需权限。权限管理机制详见[应用权限管控概述](../../../../security/AccessToken/app-permission-mgmt-overview.md)。该模块主要用于以下场景：- 在业务执行前校验当前应用是否具备访问受保护资源所需要的权限。- 在权限未授予时，拉起运行时权限弹窗或权限设置页面，请求用户授权。- 订阅当前应用的权限状态变化事件，在权限状态变化后及时调整业务流程。###### 核心枚举类型- **[GrantStatus](arkts-ability-grantstatus-e.md)：** 权限授权状态枚举，用于表示当前权限的授权状态。- **[SwitchType](arkts-ability-switchtype-e.md)：** 全局开关类型枚举，用于表示需要请求的系统全局开关类型。- **[PermissionStateChangeType](arkts-ability-permissionstatechangetype-e.md)：** 权限状态变化类型枚举，用于表示授权、取消授权等变化。- **[PermissionStatus](arkts-ability-permissionstatus-e.md)：** 权限状态枚举，用于表示当前权限状态。- **[SelectedResult](arkts-ability-selectedresult-e.md)：** 设置页授权选择结果枚举，用于表示用户在权限设置弹窗中的选择结果。###### 核心接口类型- **[PermissionStateChangeInfo](arkts-ability-permissionstatechangeinfo-i.md)：** 权限状态变化事件对象，用于返回变化类型、应用身份标识和权限名。- **[PermissionRequestResult](arkts-ability-permissionrequestresult-t.md)：** 权限申请结果对象，用于返回权限申请后的权限名列表、授权结果和弹窗展示结果。- **[Context](arkts-ability-context-t.md)：** 上下文对象，用于发起权限申请或打开权限设置弹窗。###### 核心类- **[AtManager](arkts-ability-atmanager-i.md)：** 程序访问控制管理类，提供权限校验、权限弹窗申请、设置页授权引导和权限状态监听等能力。![image_abilityAccessCtrl](../../../../reference/apis-ability-kit/figures/abilityAccessCtrl.png) |
| [SwitchType](arkts-ability-switchtype-e.md) | 程序访问控制提供应用程序的权限校验和管理能力，支持应用在访问受保护资源前进行权限状态判断、运行时授权申请、设置页授权引导和权限状态变化监听。权限分为system_grant（系统自动授权）、user_grant（需用户手动授权）和manual_settings（手动设置授权）三类，应用需在配置文件中声明所需权限。权限管理机制详见[应用权限管控概述](../../../../security/AccessToken/app-permission-mgmt-overview.md)。该模块主要用于以下场景：- 在业务执行前校验当前应用是否具备访问受保护资源所需要的权限。- 在权限未授予时，拉起运行时权限弹窗或权限设置页面，请求用户授权。- 订阅当前应用的权限状态变化事件，在权限状态变化后及时调整业务流程。###### 核心枚举类型- **[GrantStatus](arkts-ability-grantstatus-e.md)：** 权限授权状态枚举，用于表示当前权限的授权状态。- **[SwitchType](arkts-ability-switchtype-e.md)：** 全局开关类型枚举，用于表示需要请求的系统全局开关类型。- **[PermissionStateChangeType](arkts-ability-permissionstatechangetype-e.md)：** 权限状态变化类型枚举，用于表示授权、取消授权等变化。- **[PermissionStatus](arkts-ability-permissionstatus-e.md)：** 权限状态枚举，用于表示当前权限状态。- **[SelectedResult](arkts-ability-selectedresult-e.md)：** 设置页授权选择结果枚举，用于表示用户在权限设置弹窗中的选择结果。###### 核心接口类型- **[PermissionStateChangeInfo](arkts-ability-permissionstatechangeinfo-i.md)：** 权限状态变化事件对象，用于返回变化类型、应用身份标识和权限名。- **[PermissionRequestResult](arkts-ability-permissionrequestresult-t.md)：** 权限申请结果对象，用于返回权限申请后的权限名列表、授权结果和弹窗展示结果。- **[Context](arkts-ability-context-t.md)：** 上下文对象，用于发起权限申请或打开权限设置弹窗。###### 核心类- **[AtManager](arkts-ability-atmanager-i.md)：** 程序访问控制管理类，提供权限校验、权限弹窗申请、设置页授权引导和权限状态监听等能力。![image_abilityAccessCtrl](../../../../reference/apis-ability-kit/figures/abilityAccessCtrl.png) |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [PermissionRequestToggleStatus](arkts-ability-permissionrequesttogglestatus-e-sys.md) | 程序访问控制提供应用程序的权限校验和管理能力，支持应用在访问受保护资源前进行权限状态判断、运行时授权申请、设置页授权引导和权限状态变化监听。权限分为system_grant（系统自动授权）、user_grant（需用户手动授权）和manual_settings（手动设置授权）三类，应用需在配置文件中声明所需权限。权限管理机制详见[应用权限管控概述](../../../../security/AccessToken/app-permission-mgmt-overview.md)。该模块主要用于以下场景：- 在业务执行前校验当前应用是否具备访问受保护资源所需要的权限。- 在权限未授予时，拉起运行时权限弹窗或权限设置页面，请求用户授权。- 订阅当前应用的权限状态变化事件，在权限状态变化后及时调整业务流程。###### 核心枚举类型- **[GrantStatus](arkts-ability-grantstatus-e.md)：** 权限授权状态枚举，用于表示当前权限的授权状态。- **[SwitchType](arkts-ability-switchtype-e.md)：** 全局开关类型枚举，用于表示需要请求的系统全局开关类型。- **[PermissionStateChangeType](arkts-ability-permissionstatechangetype-e.md)：** 权限状态变化类型枚举，用于表示授权、取消授权等变化。- **[PermissionStatus](arkts-ability-permissionstatus-e.md)：** 权限状态枚举，用于表示当前权限状态。- **[SelectedResult](arkts-ability-selectedresult-e.md)：** 设置页授权选择结果枚举，用于表示用户在权限设置弹窗中的选择结果。###### 核心接口类型- **[PermissionStateChangeInfo](arkts-ability-permissionstatechangeinfo-i.md)：** 权限状态变化事件对象，用于返回变化类型、应用身份标识和权限名。- **[PermissionRequestResult](arkts-ability-permissionrequestresult-t.md)：** 权限申请结果对象，用于返回权限申请后的权限名列表、授权结果和弹窗展示结果。- **[Context](arkts-ability-context-t.md)：** 上下文对象，用于发起权限申请或打开权限设置弹窗。###### 核心类- **[AtManager](arkts-ability-atmanager-i.md)：** 程序访问控制管理类，提供权限校验、权限弹窗申请、设置页授权引导和权限状态监听等能力。![image_abilityAccessCtrl](../../../../reference/apis-ability-kit/figures/abilityAccessCtrl.png) |
| [PermissionDecisionStatus](arkts-ability-permissiondecisionstatus-e-sys.md) | 权限决策状态枚举。 |
<!--DelEnd-->

