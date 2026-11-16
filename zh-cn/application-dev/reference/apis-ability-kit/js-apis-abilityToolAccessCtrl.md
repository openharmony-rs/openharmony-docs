# @ohos.abilityToolAccessCtrl (安全访问围栏服务)

<!--Kit: Ability Kit-->
<!--Subsystem: Security-->
<!--Owner: @gcw_3MIoLA9y-->
<!--Designer: @wkr321_ent-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->

安全访问围栏服务模块提供工具（CLI命令）的执行认证凭据获取能力，以及应用控制权限的查询与请求能力。通过本模块，应用可以获取CLI工具及其子命令的执行认证ticket。如果用户尚未授权CLI工具所需的权限，接口将返回需要授权的权限列表及其状态；如果用户已授权所有所需权限，接口将直接返回已认证的ticket。此外，应用还可以查询指定应用是否允许被外部工具控制，或向用户请求对指定应用的控制权限。

当需要获取CLI工具执行认证ticket，或查询、请求应用控制权限时，使用本模块接口。

**起始版本：** 26.0.0

## 导入模块

```ts
import { abilityToolAccessCtrl } from '@kit.AbilityKit';
```

## abilityToolAccessCtrl.requestToolTicket

requestToolTicket(cliCmdInfos: CliCmdInfo[], ticketOptions: TicketOptions): Promise&lt;TicketQueryResult&gt;

获取CLI工具的执行认证ticket。使用Promise异步回调。

传入CLI命令列表，如果用户尚未授权CLI工具所需的权限，返回需要授权的权限列表及其状态；如果用户已授权所有所需权限，返回已认证的ticket。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.EXEC_PUBLIC_CLI_TOOL

**系统能力：** SystemCapability.Security.Asset

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| cliCmdInfos | [CliCmdInfo](#clicmdinfo)[] | 是 | CLI命令列表，指定需要获取执行认证ticket的CLI命令及其子命令。数组长度不超过300。 |
| ticketOptions | [TicketOptions](#ticketoptions) | 是 | 生成ticket的可选参数，包含ticket过期时间等。 |

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
let ticketOptions: abilityToolAccessCtrl.TicketOptions = {
  ticketExpireTimeMs: 10000
};
abilityToolAccessCtrl.requestToolTicket(cliCmdInfos, ticketOptions).then((data: abilityToolAccessCtrl.TicketQueryResult) => {
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

## abilityToolAccessCtrl.queryControlAppStatus

queryControlAppStatus(appInfo: AppInfo[]): Promise&lt;ControlAppStatusResult[]&gt;

查询指定应用的控制权限状态。使用Promise异步回调。

检查输入列表中的每个应用是否被允许或拒绝被外部工具控制。结果列表与输入列表顺序一一对应。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.CONTROL_DEVICE

**系统能力：** SystemCapability.Security.Asset

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| appInfo | [AppInfo](#appinfo)[] | 是 | 应用信息列表，指定需要查询控制权限状态的应用。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;[ControlAppStatusResult](#controlappstatusresult)[]&gt; | Promise对象，返回控制权限状态结果列表，与输入列表顺序一一对应。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[安全访问围栏服务错误码](errorcode-abilityToolAccessCtrl.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 24010000 | Invalid parameter. appInfo is empty, bundleName is invalid, etc. |
| 24010001 | Service is abnormal. Possible cause: IPC failed. |
| 24010002 | Common internal error. Possible cause: dependent service unavailable, resource access failure, etc. |

**示例：**

```ts
import { abilityToolAccessCtrl } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let appInfo: abilityToolAccessCtrl.AppInfo[] = [{
  bundleName: 'com.example.demo',
  index: 0
}];
abilityToolAccessCtrl.queryControlAppStatus(appInfo).then((data: abilityToolAccessCtrl.ControlAppStatusResult[]) => {
  console.info('queryControlAppStatus success, data: ' + JSON.stringify(data));
  for (let i = 0; i < data.length; i++) {
    let bundleName = data[i].appInfo.bundleName;
    let status = data[i].status;
    console.info(`bundleName: ${bundleName}, status: ${status}`);
  }
}).catch((err: BusinessError): void => {
  console.error(`queryControlAppStatus fail, code: ${err.code}, message: ${err.message}`);
});
```

## abilityToolAccessCtrl.requestControlAppPermissionFromUser

requestControlAppPermissionFromUser(context: Context, appInfo: AppInfo[]): Promise&lt;ControlAppStatusResult[]&gt;

向用户请求指定应用的控制权限。使用Promise异步回调。

弹出用户对话框，获取用户对每个应用的控制授权决定。返回结果反映用户对每个应用的允许或拒绝决策，与输入列表顺序一一对应。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.CONTROL_DEVICE

**系统能力：** SystemCapability.Security.Asset

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| context | Context | 是 | 应用上下文。<br>FA模型的应用Context定义见[Context](../apis-ability-kit/js-apis-inner-app-context.md)。<br>Stage模型的应用Context定义见[Context](../apis-ability-kit/js-apis-inner-application-context.md)。 |
| appInfo | [AppInfo](#appinfo)[] | 是 | 应用信息列表，指定需要请求控制权限的应用。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;[ControlAppStatusResult](#controlappstatusresult)[]&gt; | Promise对象，返回控制权限状态结果列表，与输入列表顺序一一对应。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[安全访问围栏服务错误码](errorcode-abilityToolAccessCtrl.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 24010000 | Invalid parameter. context is invalid, appInfo is empty, bundleName is invalid, etc. |
| 24010001 | Service is abnormal. Possible cause: IPC failed. |
| 24010002 | Common internal error. Possible cause: dependent service unavailable, resource access failure, etc. |

**示例：**

```ts
import { abilityToolAccessCtrl, common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let context: Context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let appInfo: abilityToolAccessCtrl.AppInfo[] = [{
  bundleName: 'com.example.demo',
  index: 0
}];
abilityToolAccessCtrl.requestControlAppPermissionFromUser(context, appInfo).then((data: abilityToolAccessCtrl.ControlAppStatusResult[]) => {
  console.info('requestControlAppPermissionFromUser success, data: ' + JSON.stringify(data));
  for (let i = 0; i < data.length; i++) {
    let bundleName = data[i].appInfo.bundleName;
    let status = data[i].status;
    console.info(`bundleName: ${bundleName}, status: ${status}`);
  }
}).catch((err: BusinessError): void => {
  console.error(`requestControlAppPermissionFromUser fail, code: ${err.code}, message: ${err.message}`);
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

## TicketOptions

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

## ControlAppStatus

表示应用控制权限状态枚举。

**起始版本：** 26.1.0

**系统能力：** SystemCapability.Security.Asset

| 名称 | 值 | 说明 |
| -------- | -------- | -------- |
| ALLOW | 0x01 | 允许控制权限。 |
| DENY | 0x02 | 控制权限被拒绝。 |

## AppInfo

表示应用信息。

**起始版本：** 26.1.0

**系统能力：** SystemCapability.Security.Asset

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| bundleName | string | 否 | 否 | 应用包名，用于唯一标识一个应用。 |
| index | number | 否 | 否 | 应用分身索引。0表示主应用，大于0表示对应的分身应用。 |

## ControlAppStatusResult

表示应用控制权限状态查询结果。

**起始版本：** 26.1.0

**系统能力：** SystemCapability.Security.Asset

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| appInfo | [AppInfo](#appinfo) | 否 | 否 | 应用信息。 |
| status | [ControlAppStatus](#controlappstatus) | 否 | 否 | 控制权限状态。 |
