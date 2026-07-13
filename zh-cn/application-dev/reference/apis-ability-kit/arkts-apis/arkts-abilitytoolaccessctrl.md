# @ohos.abilityToolAccessCtrl

abilityToolAccessCtrl的命名空间

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Security.Asset

**系统接口：** 此接口为系统接口。

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [grantToolPermissionsByUser](arkts-ability-granttoolpermissionsbyuser-f-sys.md#granttoolpermissionsbyuser-1) | 根据用户授权结果授予工具权限。该功能根据用户的授权决定授予工具（CLI命令或API）的权限。授权成功后，会生成工单，用于权限验证。 |
| [requestToolPermissions](arkts-ability-requesttoolpermissions-f-sys.md#requesttoolpermissions-1) | 根据指定的操作查询工具权限。该函数用于检查权限查询中指定的CLI命令或API的权限状态。对于每个操作，它返回权限状态、授权状态以及是否需要用户对话框。当needTicket设置为true时，远程授权会生成一个票据。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AuthStatusInfo](arkts-ability-authstatusinfo-i-sys.md) | 授权状态信息。 |
| [CliCmdInfo](arkts-ability-clicmdinfo-i-sys.md) | CLI命令信息。 |
| [OperationInfo](arkts-ability-operationinfo-i-sys.md) | 操作信息。 |
| [PermissionInfo](arkts-ability-permissioninfo-i-sys.md) | 权限信息。 |
| [PermissionQuery](arkts-ability-permissionquery-i-sys.md) | 权限查询信息。 |
| [PermissionQueryResult](arkts-ability-permissionqueryresult-i-sys.md) | 权限查询结果。 |
| [TicketInfo](arkts-ability-ticketinfo-i-sys.md) | 凭据信息。 |
| [UserAuthResult](arkts-ability-userauthresult-i-sys.md) | 用户授权结果。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AuthStatus](arkts-ability-authstatus-e-sys.md) | 授权状态。 |
| [OperationType](arkts-ability-operationtype-e-sys.md) | 操作类型。 |
<!--DelEnd-->

