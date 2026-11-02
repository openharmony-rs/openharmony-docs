# @ohos.abilityToolAccessCtrl (安全访问围栏服务)

<!--Kit: Ability Kit-->
<!--Subsystem: Security-->
<!--Owner: @gcw_3MIoLA9y-->
<!--Designer: @wkr321_ent-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->

安全访问围栏服务模块提供工具（CLI命令）的执行认证凭据获取能力。通过本模块，应用可以获取CLI工具及其子命令的执行认证ticket。如果用户尚未授权CLI工具所需的权限，接口将返回需要授权的权限列表及其状态；如果用户已授权所有所需权限，接口将直接返回已认证的ticket。

当需要获取CLI工具执行认证ticket时，使用本模块接口。

**起始版本：** 26.1.0

## 导入模块

```ts
import { abilityToolAccessCtrl } from '@kit.AbilityKit';
```

## abilityToolAccessCtrl.requestToolTicket

requestToolTicket(cliCmdInfos: CliCmdInfo[], ticketOpions: TicketOpions): Promise&lt;TicketQueryResult&gt;

获取CLI工具的执行认证ticket。使用Promise异步回调。

传入CLI命令列表，如果用户尚未授权CLI工具所需的权限，返回需要授权的权限列表及其状态；如果用户已授权所有所需权限，返回已认证的ticket。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.EXEC_PUBLIC_CLI_TOOL

**系统能力：** SystemCapability.Security.Asset

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| cliCmdInfos | [CliCmdInfo](#clicmdinfo)[] | 是 | CLI命令列表，指定需要获取执行认证ticket的CLI命令及其子命令。数组长度不超过300。 |
| ticketOpions | [TicketOpions](#ticketopions) | 是 | 生成ticket的可选参数，包含ticket过期时间等。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;[TicketQueryResult](#ticketqueryresult)&gt; | Promise对象，返回ticket查询结果，包含权限状态信息和ticket字符串。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[安全访问围栏服务错误码](errorcode-abilityToolAccessCtrl.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission denial. The interface caller does not have permission "ohos.permission.EXEC_PUBLIC_CLI_TOOL". |
| 24010000 | Invalid parameter. TicketExpireTime exceeds 60s, etc. |
| 24010001 | Service is abnormal. Possible cause: IPC failed. |
| 24010002 | Common internal error. Possible cause: dependent service unavailable, resource access failure, etc. |
| 24010006 | The requested operation is not allowed to be executed while the device is locked. |

**示例：**

```ts
import { abilityToolAccessCtrl } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let cliCmdInfos: abilityToolAccessCtrl.CliCmdInfo[] = [{
  cliCmdName: 'ohos-batteryManager',
  subCliCmdName: 'total-energy'
}];
let ticketOpions: abilityToolAccessCtrl.TicketOpions = {
  ticketExpireTimeMs: 10000
};
abilityToolAccessCtrl.requestToolTicket(cliCmdInfos, ticketOpions).then((data: abilityToolAccessCtrl.TicketQueryResult) => {
  console.info('requestToolTicket success, data: ' + JSON.stringify(data));
  if (data.ticket) {
    // 用户已授权所有所需权限，获取到已认证的ticket。
    console.info('ticket: ' + data.ticket);
  } else {
    // 用户尚未授权所有权限，查看需要授权的权限列表。
    for (let i = 0; i < data.permissionResults.length; i++) {
      let permission = data.permissionResults[i].permission;
      let status = data.permissionResults[i].permissionStatus;
      console.info(`permission: ${permission}, status: ${status}`);
    }
  }
}).catch((err: BusinessError): void => {
  console.error(`requestToolTicket fail, code: ${err.code}, message: ${err.message}`);
});
```

## CliCmdInfo

表示CLI（Command Line Interface，命令行界面）命令信息。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Security.Asset

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| cliCmdName | string | 否 | 否 | CLI命令名称，用于指定CLI命令。需传入系统支持的CLI命令名称，如'ohos-batteryManager'。<br>长度不超过512字节，不能为空。 |
| subCliCmdName | string | 否 | 否 | CLI子命令名称，用于指定CLI子命令。需传入指定CLI命令支持的子命令名称，如'total-energy'。<br>长度不超过512字节，可为空字符串。 |

## TicketOpions

表示生成ticket的可选参数。

**起始版本：** 26.1.0

**系统能力：** SystemCapability.Security.Asset

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| ticketExpireTimeMs | number | 否 | 是 | ticket过期时间，单位为毫秒。取值范围：1~60000（60秒）。<br>默认值：10000 |

## TicketQueryResult

表示ticket查询结果。

**起始版本：** 26.1.0

**系统能力：** SystemCapability.Security.Asset

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| permissionResults | abilityAccessCtrl.[PermissionInfo](#permissioninfo)[] | 否 | 否 | 权限状态结果列表。当用户尚未授权CLI工具所需的权限时，返回需要授权的权限列表及其状态。 |
| ticket | string | 否 | 否 | ticket字符串，用于权限验证。当用户已授权所有所需权限时，返回已认证的ticket；当用户尚未授权所有权限时，该项为空字符串。 |

## PermissionInfo

表示权限信息。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Security.Asset

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| permission | string | 否 | 否 | 权限名称，合法的权限名取值可在[应用权限列表](../../security/AccessToken/app-permissions.md)中查询。 |
| permissionStatus | abilityAccessCtrl.[PermissionStatus](js-apis-abilityAccessCtrl.md#permissionstatus20) | 否 | 否 | 权限状态。 |
