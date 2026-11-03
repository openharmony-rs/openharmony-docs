# 基于安全访问围栏服务获取CLI凭据(Ticket)

<!--Kit: Ability Kit-->
<!--Subsystem: Security-->
<!--Owner: @gcw_3MIoLA9y-->
<!--Designer: @wkr321_ent-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->

从API版本26.1.0开始，提供SecureAccessFence（安全访问围栏服务）能力。当应用执行CLI工具操作（如查询电池信息、获取设备状态等）时，系统要求操作经用户授权后方可执行，以确保安全可控。

SecureAccessFence提供CLI工具执行认证ticket的获取能力：应用通过`requestToolTicket`接口传入待执行的CLI命令列表，系统自动检查相应权限的授权状态——若所需权限均已授权，直接返回已认证的ticket；若存在未授权权限，则返回待授权权限列表，应用可引导用户完成授权后再次获取ticket。

## 能力范围

- **获取CLI工具执行认证ticket：** 应用通过接口获取CLI工具及其子命令的执行认证ticket。若用户尚未授予所需权限，接口返回待授权权限列表及其状态；若所需权限均已授权，接口直接返回已认证的ticket，供后续CLI工具执行时的权限校验使用。

## 基本概念

- **CLI命令：** 命令行界面（Command Line Interface）工具，如`ohos-batteryManager total-energy`等系统命令。安全访问围栏服务对CLI命令的执行权限进行管控。
- **Ticket：** 安全访问围栏服务签发的执行认证凭据，用于CLI工具执行时的权限校验。当应用需要执行受控的CLI命令时，需先获取有效的ticket。

## 实现原理

SecureAccessFence的工作流程如下：

1. 应用调用[requestToolTicket](../../reference/apis-ability-kit/js-apis-abilityToolAccessCtrl.md#abilitytoolaccessctrlrequesttoolticket)接口，传入需要执行认证的CLI命令列表。
2. 如果用户尚未授权CLI工具所需的权限，接口返回`permissionResults`列表，包含需要授权的权限名称及其状态。应用可引导用户完成权限授权。
3. 如果用户已授权所有所需权限，接口直接返回已认证的`ticket`字符串。
4. 应用使用获取到的ticket执行CLI工具。

## 开发流程

获取CLI工具执行认证ticket的开发流程如下：

1. 导入安全访问围栏服务模块。
2. 构建CLI命令信息（CliCmdInfo），指定需要执行的CLI命令及其子命令。
3. 构建ticket选项（TicketOpions），设置ticket过期时间。
4. 调用`requestToolTicket`接口获取ticket。
5. 处理返回结果：若ticket不为空，直接用于执行CLI工具；若ticket为空，引导用户授权后重新获取。
6. 添加错误处理逻辑，处理入参错误、设备锁屏等异常场景。

## 开发步骤

调用[requestToolTicket](../../reference/apis-ability-kit/js-apis-abilityToolAccessCtrl.md#abilitytoolaccessctrlrequesttoolticket)接口需申请`ohos.permission.EXEC_PUBLIC_CLI_TOOL`权限，申请方式请参考[声明权限](../AccessToken/declare-permissions.md)。

以获取CLI命令`ohos-batteryManager total-energy`的执行认证ticket为例，ticket有效期为10秒。

1. 导入安全访问围栏服务模块和BusinessError错误类型。

   导入后可使用`abilityToolAccessCtrl`模块提供的`requestToolTicket`接口获取CLI工具执行认证ticket。

   <!-- @[import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/AssetStoreKit/AssetStoreArkTS/entry/src/main/ets/operations/request_tool_ticket.ets) -->
   
   ``` TypeScript
   import { abilityToolAccessCtrl } from '@ohos.abilityToolAccessCtrl';
   import { BusinessError } from '@kit.BasicServicesKit';
   ```

2. 构建CLI命令信息。

   `cliCmdName`为CLI命令名称，需传入系统支持的CLI命令名称，如`ohos-batteryManager`，长度不超过512字节，不能为空。`subCliCmdName`为CLI子命令名称，如`total-energy`，长度不超过512字节，可为空字符串。`cliCmdInfos`数组长度不超过300。详细参数说明请参考[CliCmdInfo](../../reference/apis-ability-kit/js-apis-abilityToolAccessCtrl.md#clicmdinfo)。

   ```typescript
   let cliCmdInfos: abilityToolAccessCtrl.CliCmdInfo[] = [{
     cliCmdName: 'ohos-batteryManager',
     subCliCmdName: 'total-energy'
   }];
   ```

3. 构建ticket选项。

   `ticketExpireTimeMs`为ticket过期时间，单位为毫秒，取值范围1~60000（60秒），默认值10000。详细参数说明请参考[TicketOpions](../../reference/apis-ability-kit/js-apis-abilityToolAccessCtrl.md#ticketopions)。

   ```typescript
   let ticketOpions: abilityToolAccessCtrl.TicketOpions = {
     ticketExpireTimeMs: 10000
   };
   ```

4. 调用requestToolTicket接口获取ticket，并处理返回结果。

   ```typescript
   abilityToolAccessCtrl.requestToolTicket(cliCmdInfos, ticketOpions)
     .then((data: abilityToolAccessCtrl.TicketQueryResult) => {
       if (data.ticket) {
         // 用户已授权所有所需权限，获取到已认证的ticket，可用于执行CLI工具
         console.info('ticket: ' + data.ticket);
       } else {
         // 用户尚未授权所有权限，查看需要授权的权限列表
         for (let i = 0; i < data.permissionResults.length; i++) {
           let permission = data.permissionResults[i].permission;
           let status = data.permissionResults[i].permissionStatus;
           console.info(`permission: ${permission}, status: ${status}`);
         }
         // 引导用户完成权限授权后，再次调用requestToolTicket获取ticket
       }
     })
   ```

   接口返回`TicketQueryResult`对象，包含`ticket`和`permissionResults`两个字段。当用户已授权所有所需权限时，`ticket`字段返回已认证的ticket字符串，应用可使用该ticket执行CLI工具；当用户尚未授权所有权限时，`ticket`为空字符串，`permissionResults`列表包含待授权权限名称及其状态，应用需引导用户完成授权后重新调用接口。接口详细说明请参考[requestToolTicket](../../reference/apis-ability-kit/js-apis-abilityToolAccessCtrl.md#abilitytoolaccessctrlrequesttoolticket)。

5. 添加错误处理逻辑，处理接口调用异常。

   ```typescript
   .catch((err: BusinessError): void => {
     console.error(`requestToolTicket fail, code: ${err.code}, message: ${err.message}`);
     if (err.code === 24010000) {
       // 入参错误，检查ticketExpireTimeMs是否在1~60000范围内，cliCmdInfos长度是否超过300
     } else if (err.code === 24010006) {
       // 设备处于锁屏状态，请解锁设备后重新调用
     }
   });
   ```

   > **说明：**
   >
   > 常见错误码及处理方式如下。
   > - 24010000：入参错误。检查`ticketExpireTimeMs`取值是否在1~60000范围内，`cliCmdInfos`列表是否为空或长度超过300，CLI命令名称是否为空。
   > - 24010006：设备处于锁屏状态。解锁设备后重新调用接口。
   > - 24010001：系统服务工作异常。可稍后重试，若问题持续请检查系统日志。
   > - 完整错误码列表请参考[安全访问围栏服务错误码](../../reference/apis-ability-kit/errorcode-abilityToolAccessCtrl.md)。
