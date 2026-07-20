# @ohos.abilityToolAccessCtrl

abilityToolAccessCtrl的命名空间

**起始版本：** 26.0.0

<!--Device-unnamed-declare namespace abilityToolAccessCtrl--><!--Device-unnamed-declare namespace abilityToolAccessCtrl-End-->

**系统能力：** SystemCapability.Security.Asset

**系统接口：** 此接口为系统接口。

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [grantToolPermissionsByUser](arkts-ability-abilitytoolaccessctrl-granttoolpermissionsbyuser-f-sys.md#granttoolpermissionsbyuser) | 根据用户授权结果授予工具权限。该功能根据用户的授权决定授予工具（CLI命令或API）的权限。授权成功后，会生成工单，用于权限验证。 |
| [requestToolPermissions](arkts-ability-abilitytoolaccessctrl-requesttoolpermissions-f-sys.md#requesttoolpermissions) | 根据指定的操作查询工具权限。该函数用于检查权限查询中指定的CLI命令或API的权限状态。对于每个操作，它返回权限状态、授权状态以及是否需要用户对话框。当needTicket设置为true时，远程授权会生成一个票据。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AuthStatusInfo](arkts-ability-abilitytoolaccessctrl-authstatusinfo-i-sys.md) | 授权状态信息。 |
| [CliCmdInfo](arkts-ability-abilitytoolaccessctrl-clicmdinfo-i-sys.md) | CLI命令信息。 |
| [OperationInfo](arkts-ability-abilitytoolaccessctrl-operationinfo-i-sys.md) | 操作信息。 |
| [PermissionInfo](arkts-ability-abilitytoolaccessctrl-permissioninfo-i-sys.md) | 权限信息。 |
| [PermissionQuery](arkts-ability-abilitytoolaccessctrl-permissionquery-i-sys.md) | 权限查询信息。 |
| [PermissionQueryResult](arkts-ability-abilitytoolaccessctrl-permissionqueryresult-i-sys.md) | 权限查询结果。 |
| [TicketInfo](arkts-ability-abilitytoolaccessctrl-ticketinfo-i-sys.md) | 凭据信息。 |
| [UserAuthResult](arkts-ability-abilitytoolaccessctrl-userauthresult-i-sys.md) | 用户授权结果。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AuthStatus](arkts-ability-abilitytoolaccessctrl-authstatus-e-sys.md) | 授权状态。 |
| [OperationType](arkts-ability-abilitytoolaccessctrl-operationtype-e-sys.md) | 操作类型。 |
<!--DelEnd-->

