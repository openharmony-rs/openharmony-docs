# 获取CLI工具执行认证ticket(ArkTS)

<!--Kit: Ability Kit-->
<!--Subsystem: Security-->
<!--Owner: @gcw_3MIoLA9y-->
<!--Designer: @wkr321_ent-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->

## 接口介绍

开发者可以查阅API文档，获取CLI工具执行认证ticket接口的详细说明：[requestToolTicket(cliCmdInfos: CliCmdInfo[], ticketOpions: TicketOpions)](../../reference/apis-ability-kit/js-apis-abilityToolAccessCtrl.md#abilitytoolaccessctrlrequesttoolticket)。

在获取CLI工具执行认证ticket时，参数如下表所示：

**requestToolTicket入参：**

| 属性名称 | 类型 | 是否必选 | 说明 |
| -------- | -------- | -------- | -------- |
| cliCmdInfos | [CliCmdInfo](../../reference/apis-ability-kit/js-apis-abilityToolAccessCtrl.md#clicmdinfo)[] | 是 | CLI命令列表，列表长度不超过300。 |
| ticketOpions | [TicketOpions](../../reference/apis-ability-kit/js-apis-abilityToolAccessCtrl.md#ticketopions) | 是 | 生成ticket的可选参数，包含ticket过期时间等。 |

**CliCmdInfo参数：**

| 属性名称 | 类型 | 是否必选 | 说明 |
| -------- | -------- | -------- | -------- |
| cliCmdName | string | 是 | CLI命令名称，需传入系统支持的CLI命令名称，如'ohos-batteryManager'。长度不超过512字节，不能为空。 |
| subCliCmdName | string | 是 | CLI子命令名称，需传入指定CLI命令支持的子命令名称，如'total-energy'。长度不超过512字节，可为空字符串。 |

**TicketOpions参数：**

| 属性名称 | 类型 | 是否必选 | 说明 |
| -------- | -------- | -------- | -------- |
| ticketExpireTimeMs | number | 否 | ticket过期时间，单位为毫秒。取值范围：1~60000（60秒）。默认值为10000。 |

## 约束和限制

- 调用本接口前需申请`ohos.permission.EXEC_PUBLIC_CLI_TOOL`权限，申请方式请参考[声明权限](../AccessToken/declare-permissions.md)。
- ticketExpireTimeMs超过60秒（60000毫秒）将返回错误码24010000。
- 设备处于锁屏状态时不允许执行该操作，将返回错误码24010006。

## 代码示例

获取CLI命令`ohos-batteryManager total-energy`的执行认证ticket，ticket有效期为10秒。

1. 导入模块。
   <!-- @[import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/AssetStoreKit/AssetStoreArkTS/entry/src/main/ets/operations/request_tool_ticket.ets) -->
   
   ``` TypeScript
   import { abilityToolAccessCtrl } from '@ohos.abilityToolAccessCtrl';
   import { BusinessError } from '@kit.BasicServicesKit';
   ```

2. 参考如下示例代码，进行业务功能开发。
   <!-- @[requestToolTicket](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/AssetStoreKit/AssetStoreArkTS/entry/src/main/ets/operations/request_tool_ticket.ets) -->
   
   ``` TypeScript
   let cliCmdInfos: abilityToolAccessCtrl.CliCmdInfo[] = [{
      cliCmdName: 'ohos-batteryManager',
      subCliCmdName: 'total-energy'
    }];
    let ticketOpions: abilityToolAccessCtrl.TicketOpions = {
      ticketExpireTimeMs: 10000
    };
    abilityToolAccessCtrl.requestToolTicket(
     cliCmdInfos, ticketOpions).then((data: abilityToolAccessCtrl.TicketQueryResult) => {
      // ...
      if (data.ticket) {
        // 用户已授权所有所需权限，获取到已认证的ticket，可用于执行CLI工具。
        console.info('ticket: ' + data.ticket);
      } else {
        // 用户尚未授权所有权限，查看需要授权的权限列表。
        for (let i = 0; i < data.permissionResults.length; i++) {
          let permission = data.permissionResults[i].permission;
          let status = data.permissionResults[i].permissionStatus;
          console.info(`permission: ${permission}, status: ${status}`);
        }
        // 引导用户完成权限授权后，再次调用requestToolTicket获取ticket。
      }
    }).catch((err: BusinessError): void => {
      console.error(`requestToolTicket fail, code: ${err.code}, message: ${err.message}`);
      // ...
    });
   ```
