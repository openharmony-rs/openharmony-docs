# @ohos.abilityToolAccessCtrl(This module provides the capabilities of tools access control)

abilityToolAccessCtrl的命名空间

**起始版本：** 26.0.0

**模型约束：** 此接口可在Stage模型和FA模型下使用。

<!--Device-unnamed-declare namespace abilityToolAccessCtrl--><!--Device-unnamed-declare namespace abilityToolAccessCtrl-End-->

**系统能力：** SystemCapability.Security.Asset

## 导入模块

```TypeScript
import { abilityToolAccessCtrl } from '@kit.AbilityKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [queryControlAppStatus](arkts-ability-abilitytoolaccessctrl-querycontrolappstatus-f.md#querycontrolappstatus-1) | 查询指定应用的控制权限状态。此函数检查输入列表中的每个应用程序是否被允许或拒绝被外部工具控制。结果列表与输入顺序相对应。 |
| [requestControlAppPermissionFromUser](arkts-ability-abilitytoolaccessctrl-requestcontrolapppermissionfromuser-f.md#requestcontrolapppermissionfromuser-1) | 向用户请求指定应用的控制权限。该函数会弹出一个用户对话框，获取对每个应用的控制授权决 。返回结果反映用户对每个应用的允许或拒绝决策。 |
| [requestToolTicket](arkts-ability-abilitytoolaccessctrl-requesttoolticket-f.md#requesttoolticket-1) | 获取CLI工具的执行认证票据。该函数用于获取CLI工具及子命令的执行认证票据。如果CLI工具所需权限用户尚未授权，会返回需要授权的权限列表及权限状态。如果CLI工具所需权限用户均授权，会返回授权的票据。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [generateControlledDevicePackage](arkts-ability-abilitytoolaccessctrl-generatecontrolleddevicepackage-f-sys.md#generatecontrolleddevicepackage-1) | 生成受控设备的授权包。根据权限查询列表生成远程授权包。生成的包可以发送到控制器设备进行权限验证。 |
| [generateControllerDevicePackage](arkts-ability-abilitytoolaccessctrl-generatecontrollerdevicepackage-f-sys.md#generatecontrollerdevicepackage-1) | 生成控制器设备的授权包。根据远程用户授权结果生成远程授权包。生成的包可以发送到受控设备进行权限验证。 |
| [generateTaskChallenge](arkts-ability-abilitytoolaccessctrl-generatetaskchallenge-f-sys.md#generatetaskchallenge-1) | 为任务认证令牌生成挑战值。此函数基于任务身份信息生成挑战值。 |
| [generateTaskIdentity](arkts-ability-abilitytoolaccessctrl-generatetaskidentity-f-sys.md#generatetaskidentity-1) | 为代理命令生成基于任务的身份验证身份。该函数根据调用者身份和基本任务属性（例如任务 ID 和任务过期时间）生成认证标识。 |
| [getRemoteGrantStatus](arkts-ability-abilitytoolaccessctrl-getremotegrantstatus-f-sys.md#getremotegrantstatus-1) | 获取远程授权状态。该功能用于查询远程授权特性的使能状态。启用时，设备可以向远程设备授予权限；禁用时，不允许远程授权。 |
| [grantToolPermissionsByUser](arkts-ability-abilitytoolaccessctrl-granttoolpermissionsbyuser-f-sys.md#granttoolpermissionsbyuser-1) | 根据用户授权结果授予工具权限。该功能根据用户的授权决定授予工具（CLI命令或API）的权限。授权成功后，会生成工单，用于权限验证。 |
| [requestToolPermissions](arkts-ability-abilitytoolaccessctrl-requesttoolpermissions-f-sys.md#requesttoolpermissions-1) | 根据指定的操作查询工具权限。该函数用于检查权限查询中指定的CLI命令或API的权限状态。对于每个操作，它返回权限状态、授权状态以及是否需要用户对话框。当needTicket设置为true时，远程授权会生成一个票据。 |
| [revokeTaskIdentity](arkts-ability-abilitytoolaccessctrl-revoketaskidentity-f-sys.md#revoketaskidentity-1) | 批量撤销代理命令的任务认证标识。批量撤销任务鉴权标识，删除任务属性的本地缓存。 |
| [updateRemoteGrantStatus](arkts-ability-abilitytoolaccessctrl-updateremotegrantstatus-f-sys.md#updateremotegrantstatus-1) | 更新远程授权状态。该功能用于开启或关闭远程授权特性。启用时，设备可以向远程设备授予权限；禁用时，不允许远程授权。 |
| [verifyControlledDevicePackage](arkts-ability-abilitytoolaccessctrl-verifycontrolleddevicepackage-f-sys.md#verifycontrolleddevicepackage-1) | 对受控设备的授权包进行校验。对被控设备发送的远程授权包进行校验。它验证票证以确保授权是合法的。 |
| [verifyControllerDevicePackage](arkts-ability-abilitytoolaccessctrl-verifycontrollerdevicepackage-f-sys.md#verifycontrollerdevicepackage-1) | 验证来自控制器设备的授权包。验证控制器设备发送的远程授权包。它验证票证和远程设备信息，以确保授权是合法的。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [AppInfo](arkts-ability-abilitytoolaccessctrl-appinfo-i.md) | 应用的相关信息。 |
| [CliCmdInfo](arkts-ability-abilitytoolaccessctrl-clicmdinfo-i.md) | CLI命令信息。 |
| [ControlAppStatusResult](arkts-ability-abilitytoolaccessctrl-controlappstatusresult-i.md) | 应用的相关信息。 |
| [PermissionInfo](arkts-ability-abilitytoolaccessctrl-permissioninfo-i.md) | 权限信息。 |
| [TicketParams](arkts-ability-abilitytoolaccessctrl-ticketparams-i.md) | 生成票据的可选参数 |
| [TicketQueryResult](arkts-ability-abilitytoolaccessctrl-ticketqueryresult-i.md) | 票据查询结果。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AuthStatusInfo](arkts-ability-abilitytoolaccessctrl-authstatusinfo-i-sys.md) | 授权状态信息。 |
| [OperationInfo](arkts-ability-abilitytoolaccessctrl-operationinfo-i-sys.md) | 操作信息。 |
| [PermissionInfo](arkts-ability-abilitytoolaccessctrl-permissioninfo-i-sys.md) | 权限信息。 |
| [PermissionQuery](arkts-ability-abilitytoolaccessctrl-permissionquery-i-sys.md) | 权限查询信息。 |
| [PermissionQueryResult](arkts-ability-abilitytoolaccessctrl-permissionqueryresult-i-sys.md) | 权限查询结果。 |
| [RemoteAuthPackage](arkts-ability-abilitytoolaccessctrl-remoteauthpackage-i-sys.md) | 远程授权包。 |
| [RemoteControlParams](arkts-ability-abilitytoolaccessctrl-remotecontrolparams-i-sys.md) | 远程控制交互参数 |
| [RemoteInfo](arkts-ability-abilitytoolaccessctrl-remoteinfo-i-sys.md) | 远端设备信息。 |
| [RemoteUserAuthItem](arkts-ability-abilitytoolaccessctrl-remoteuserauthitem-i-sys.md) | 远程用户授权项。 |
| [RemoteUserAuthResults](arkts-ability-abilitytoolaccessctrl-remoteuserauthresults-i-sys.md) | 远程用户授权结果。 |
| [TaskIdentity](arkts-ability-abilitytoolaccessctrl-taskidentity-i-sys.md) | 任务标识。 |
| [TaskIdentityInfo](arkts-ability-abilitytoolaccessctrl-taskidentityinfo-i-sys.md) | 用于生成任务标识的任务标识输入信息。 |
| [TicketInfo](arkts-ability-abilitytoolaccessctrl-ticketinfo-i-sys.md) | 凭据信息。 |
| [UserAuthResult](arkts-ability-abilitytoolaccessctrl-userauthresult-i-sys.md) | 用户授权结果。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ControlAppStatus](arkts-ability-abilitytoolaccessctrl-controlappstatus-e.md) | 任务标识。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AuthStatus](arkts-ability-abilitytoolaccessctrl-authstatus-e-sys.md) | 授权状态。 |
| [ExecuteType](arkts-ability-abilitytoolaccessctrl-executetype-e-sys.md) | 任务执行类别。 |
| [OperationType](arkts-ability-abilitytoolaccessctrl-operationtype-e-sys.md) | 操作类型。 |
| [RemoteGrantStatus](arkts-ability-abilitytoolaccessctrl-remotegrantstatus-e-sys.md) | 远程授权状态。 |
| [Role](arkts-ability-abilitytoolaccessctrl-role-e-sys.md) | 设备角色。 |
<!--DelEnd-->
