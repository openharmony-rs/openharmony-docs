# SecureAccessFence简介

<!--Kit: Ability Kit-->
<!--Subsystem: Security-->
<!--Owner: @gcw_3MIoLA9y-->
<!--Designer: @wkr321_ent-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->

从API版本26.2.0开始，提供提供SecureAccessFence（安全访问围栏服务）能力，可用于CLI工具执行认证凭据的获取能力。

**获取CLI工具执行认证ticket：** 应用可通过接口获取CLI工具及其子命令的执行认证ticket。若用户尚未授予所需权限，接口将返回待授权权限列表及其状态；若所需权限均已授权，接口将直接返回已认证的ticket，供后续CLI工具执行时的权限校验使用。

## 基本概念

- **CLI命令：** 命令行界面（Command Line Interface）工具，如`ohos-batteryManager total-energy`等系统命令。安全访问围栏服务可对CLI命令的执行权限进行管控。
- **Ticket：** 安全访问围栏服务签发的执行认证凭据，用于CLI工具执行时的权限校验。当应用需要执行受控的CLI命令时，需先获取有效的ticket。

## 工作流程

1. 应用调用[requestToolTicket](../../reference/apis-ability-kit/js-apis-abilityToolAccessCtrl.md#abilitytoolaccessctrlrequesttoolticket)接口，传入需要执行认证的CLI命令列表。
2. 如果用户尚未授权CLI工具所需的权限，接口返回`permissionResults`列表，包含需要授权的权限名称及其状态。应用可引导用户完成权限授权。
3. 如果用户已授权所有所需权限，接口直接返回已认证的`ticket`字符串。
4. 应用使用获取到的ticket执行CLI工具。

## 约束与限制

- 调用[requestToolTicket](../../reference/apis-ability-kit/js-apis-abilityToolAccessCtrl.md#abilitytoolaccessctrlrequesttoolticket)接口需申请`ohos.permission.EXEC_PUBLIC_CLI_TOOL`权限，申请方式请参考[声明权限](../AccessToken/declare-permissions.md)。
- ticket过期时间最大值为60秒（60000毫秒），超过最大值将返回错误码24010000。
- 设备处于锁屏状态时，不允许执行该操作，将返回错误码24010006。
