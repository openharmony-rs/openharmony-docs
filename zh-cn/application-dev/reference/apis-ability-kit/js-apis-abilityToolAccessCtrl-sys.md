# @ohos.abilityToolAccessCtrl (工具访问控制)(系统接口)

<!--Kit: Ability Kit-->
<!--Subsystem: Security-->
<!--Owner: @gcw_3MIoLA9y-->
<!--Designer: @wkr321_ent-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->

工具访问控制模块提供工具（CLI命令和API接口）的权限管理能力，包括权限查询、用户授权、远程授权等功能。权限查询用于检查工具的权限状态，用户授权用于根据用户决定授予工具权限，远程授权通过ticket机制实现跨设备权限管理。模块支持ticket验证机制和跨设备协同授权，能够提升权限管理安全性并简化授权流程。

当需要查询CLI命令或API接口的权限状态、进行工具权限授权、或管理远程设备的授权时，使用本模块接口。

**起始版本：** 26.0.0

> **说明：**
>
> 本模块接口为系统接口。

## 导入模块

```ts
import { abilityToolAccessCtrl } from '@kit.AbilityKit';
```

## abilityToolAccessCtrl.requestToolPermissions

requestToolPermissions(permissionQuery: PermissionQuery): Promise&lt;PermissionQueryResult&gt;

根据指定操作查询工具权限。检查入参[permissionQuery](#permissionquery)的[operationInfo](#operationinfo)属性中指定的CLI命令或API接口的权限状态，返回每个操作的权限状态、授权状态以及是否需要用户弹窗。当[permissionQuery.needTicket](#permissionquery)设置为true时，将生成用于远程授权的ticket。使用Promise异步回调。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**需要权限：** ohos.permission.QUERY_TOOL_PERMISSIONS

**系统能力：** SystemCapability.Security.Asset

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| permissionQuery | [PermissionQuery](#permissionquery) | 是 | 权限查询信息，包含操作信息列表、是否需要生成ticket、远程设备信息等。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;[PermissionQueryResult](#permissionqueryresult)&gt; | Promise对象。返回权限查询结果，包含是否需要弹窗、权限状态信息和ticket信息。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[工具访问控制错误码](errorcode-abilityToolAccessCtrl-sys.md)。


| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission denial. The interface caller does not have permission "ohos.permission.QUERY_TOOL_PERMISSIONS". |
| 202 | The caller is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 24010000 | Invalid parameter. OperationType and operationInfo do not match, specified callerTokenId does not exist, ticketExpireTime exceeds 24h, etc. |
| 24010001 | Service is abnormal. Possible cause: IPC failed. |
| 24010002 | Common internal error. Possible cause: dependent service unavailable, resource access failed, etc. |
| 24010003 | The account is not logged in, network is unavailable, timeout, etc. |
| 24010006 | The requested operation is not allowed to be executed while the device is locked. |

**示例：**

```ts
import { abilityToolAccessCtrl } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let permissionQuery: abilityToolAccessCtrl.PermissionQuery = {
  operationInfo: [{
    operationType: abilityToolAccessCtrl.OperationType.CLI,
    info: {
      cliCmdName: 'ohos-displayManager',
      subCliCmdName: 'set-brightness'
    }
  }],
  needTicket: true,
  ticketExpireTimeMs: 10000,
};
abilityToolAccessCtrl.requestToolPermissions(permissionQuery).then((data: abilityToolAccessCtrl.PermissionQueryResult) => {
  console.info('requestToolPermissions success, data: ' + JSON.stringify(data));
}).catch((err: BusinessError): void => {
  console.error(`requestToolPermissions fail, code: ${err.code}, message: ${err.message}`);
});
```

## abilityToolAccessCtrl.grantToolPermissionsByUser

grantToolPermissionsByUser(userAuthResult: UserAuthResult[]): Promise&lt;TicketInfo[]&gt;

根据用户授权结果授予工具权限。根据用户的授权决定，为工具（CLI命令或API接口）授予权限。授权成功后，生成可用于权限验证的ticket。使用Promise异步回调。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**需要权限：** ohos.permission.MANAGE_TOOL_RUNTIME_PERMISSIONS

**系统能力：** SystemCapability.Security.Asset

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| userAuthResult | Array&lt;[UserAuthResult](#userauthresult)&gt; | 是 | 用户授权结果列表，包含权限信息和权限查询信息。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;Array&lt;[TicketInfo](#ticketinfo)&gt;&gt; | Promise对象。返回授权成功后生成的ticket信息列表。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[工具访问控制错误码](errorcode-abilityToolAccessCtrl-sys.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission denial. The interface caller does not have permission "ohos.permission.MANAGE_TOOL_RUNTIME_PERMISSIONS". |
| 202 | The caller is not a system application. |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 24010000 | Invalid parameter. OperationType and operationInfo do not match, specified callerTokenId does not exist, ticketExpireTime exceeds 24h, etc. |
| 24010001 | Service is abnormal. Possible cause: IPC failed. |
| 24010002 | Common internal error. Possible cause: dependent service unavailable, resource access failed, etc. |
| 24010003 | The account is not logged in, network is unavailable, timeout, etc. |
| 24010004 | Invalid permission. A permission in permissionInfo does not exist. |
| 24010005 | Grant permission failed. The application specified by the tokenID is not allowed to be granted with the specified permission, the specified permission cannot be granted by user, etc. |


**示例：**

```ts
import { abilityToolAccessCtrl, abilityAccessCtrl, Permissions } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let userAuthResult: Array<abilityToolAccessCtrl.UserAuthResult> = [{
  permissionInfo: [{
    permission: 'ohos.permission.cli.BUNDLE_ACTIVE_INFO' as Permissions,
    permissionStatus: abilityAccessCtrl.PermissionStatus.GRANTED
  }],
  permissionQuery: {
    operationInfo: [{
      operationType: abilityToolAccessCtrl.OperationType.CLI,
      info: 'ohos.permission.cli.BUNDLE_ACTIVE_INFO'
    }],
    needTicket: true
  }
}];
abilityToolAccessCtrl.grantToolPermissionsByUser(userAuthResult).then((data: Array<abilityToolAccessCtrl.TicketInfo>) => {
  console.info('grantToolPermissionsByUser success, data: ' + JSON.stringify(data));
}).catch((err: BusinessError): void => {
  console.error(`grantToolPermissionsByUser fail, code: ${err.code}, message: ${err.message}`);
});
```

## abilityToolAccessCtrl.generateControllerDevicePackage

generateControllerDevicePackage(remoteUserAuthResult: RemoteUserAuthResults[]): Promise&lt;RemoteAuthPackage[]&gt;

在主控设备上，根据用户远程授权结果生成远程授权结果包。生成的包可以发送到被控设备上，完成完整性校验后，执行权限授权。使用Promise异步回调。

**起始版本：** 26.1.0

**系统接口：** 此接口为系统接口。

**需要权限：** ohos.permission.QUERY_TOOL_PERMISSIONS

**系统能力：** SystemCapability.Security.Asset

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| remoteUserAuthResult | [RemoteUserAuthResults](#remoteuserauthresults)[] | 是 | 用户远程授权结果列表，包含授权结果和权限信息。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;[RemoteAuthPackage](#remoteauthpackage)[]&gt; | Promise对象，返回远程授权结果包列表。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[工具访问控制错误码](errorcode-abilityToolAccessCtrl-sys.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission denial. The interface caller does not have permission "ohos.permission.QUERY_TOOL_PERMISSIONS". |
| 202 | The caller is not a system application. |
| 24010000 | Invalid parameter. OperationType and operationInfo do not match, specified callerTokenId does not exist, etc. |
| 24010001 | Service is abnormal. Possible cause: IPC failed. |
| 24010002 | Common internal error. Possible cause: dependent service unavailable, resource access failed, etc. |
| 24010003 | The account is not logged in, network is unavailable, timeout, etc. |

**示例：**

```ts
import { abilityToolAccessCtrl } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let remoteUserAuthResult: Array<abilityToolAccessCtrl.RemoteUserAuthResults> = [{
  results: [{
    permission: 'ohos.permission.cli.BUNDLE_ACTIVE_INFO',
    authResult: 'GRANTED'
  }],
  permissionQuery: {
    operationInfo: [{
      operationType: abilityToolAccessCtrl.OperationType.CLI,
      info: {
        cliCmdName: 'ohos-displayManager',
        subCliCmdName: 'set-brightness'
      }
    }],
    needTicket: true
  }
}];
abilityToolAccessCtrl.generateControllerDevicePackage(remoteUserAuthResult).then((data: Array<abilityToolAccessCtrl.RemoteAuthPackage>) => {
  console.info('generateControllerDevicePackage success, data: ' + JSON.stringify(data));
}).catch((err: BusinessError): void => {
  console.error(`generateControllerDevicePackage fail, code: ${err.code}, message: ${err.message}`);
});
```

## abilityToolAccessCtrl.generateControlledDevicePackage

generateControlledDevicePackage(permissionQuery: PermissionQuery[]): Promise&lt;RemoteAuthPackage[]&gt;

在被控设备上，根据权限查询列表生成远程授权请求包。生成的包可以发送到主控设备上，完成完整性校验后，发起用户授权确认。使用Promise异步回调。

**起始版本：** 26.1.0

**系统接口：** 此接口为系统接口。

**需要权限：** ohos.permission.QUERY_TOOL_PERMISSIONS

**系统能力：** SystemCapability.Security.Asset

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| permissionQuery | [PermissionQuery](#permissionquery)[] | 是 | 权限查询列表，包含CLI和API操作信息、远程授权交互信息等。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;[RemoteAuthPackage](#remoteauthpackage)[]&gt; | Promise对象，返回远程授权请求包列表。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[工具访问控制错误码](errorcode-abilityToolAccessCtrl-sys.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission denial. The interface caller does not have permission "ohos.permission.QUERY_TOOL_PERMISSIONS". |
| 202 | The caller is not a system application. |
| 24010000 | Invalid parameter. Permission exceeds 256 characters, specified tokenId is invalid, etc. |
| 24010001 | Service is abnormal. Possible cause: IPC failed. |
| 24010002 | Common internal error. Possible cause: dependent service unavailable, resource access failed, etc. |
| 24010003 | The account is not logged in, network is unavailable, timeout, etc. |

**示例：**

```ts
import { abilityToolAccessCtrl } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let permissionQuery: Array<abilityToolAccessCtrl.PermissionQuery> = [{
  operationInfo: [{
    operationType: abilityToolAccessCtrl.OperationType.CLI,
    info: {
      cliCmdName: 'ohos-displayManager',
      subCliCmdName: 'set-brightness'
    }
  }],
  needTicket: true,
  remoteInfo: {
    role: abilityToolAccessCtrl.Role.CONTROLLER,
    remoteId: 'device123',
    domainId: 'domain456'
  }
}];
abilityToolAccessCtrl.generateControlledDevicePackage(permissionQuery).then((data: Array<abilityToolAccessCtrl.RemoteAuthPackage>) => {
  console.info('generateControlledDevicePackage success, data: ' + JSON.stringify(data));
}).catch((err: BusinessError): void => {
  console.error(`generateControlledDevicePackage fail, code: ${err.code}, message: ${err.message}`);
});
```

## abilityToolAccessCtrl.verifyControllerDevicePackage

verifyControllerDevicePackage(ticketInfo: RemoteAuthPackage[], remoteInfo: RemoteInfo): Promise&lt;boolean[]&gt;

验证主控设备发送的远程授权结果包，检查消息凭据和远程设备信息以确保授权结果合法。使用Promise异步回调。

**起始版本：** 26.1.0

**系统接口：** 此接口为系统接口。

**需要权限：** ohos.permission.QUERY_TOOL_PERMISSIONS

**系统能力：** SystemCapability.Security.Asset

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| ticketInfo | [RemoteAuthPackage](#remoteauthpackage)[] | 是 | 远程授权包列表，包含远程消息、防重放挑战值和消息完整性凭据。 |
| remoteInfo | [RemoteInfo](#remoteinfo) | 是 | 远端设备信息，包含设备角色、设备ID、华为账号ID等。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;boolean[]&gt; | Promise对象。返回true表示验证通过；返回false表示验证失败。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[工具访问控制错误码](errorcode-abilityToolAccessCtrl-sys.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission denial. The interface caller does not have permission "ohos.permission.QUERY_TOOL_PERMISSIONS". |
| 202 | The caller is not a system application. |
| 24010000 | Invalid parameter. Format of ticketInfo or remoteInfo is invalid. |
| 24010001 | Service is abnormal. Possible cause: IPC failed. |
| 24010002 | Common internal error. Possible cause: dependent service unavailable, resource access failed, etc. |
| 24010003 | The account is not logged in, network is unavailable, timeout, etc. |

**示例：**

```ts
import { abilityToolAccessCtrl } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let ticketInfo: Array<abilityToolAccessCtrl.RemoteAuthPackage> = [{
  remoteMessage: 'test_message',
  challenge: 'test_challenge',
  ticket: 'test_ticket'
}];
let remoteInfo: abilityToolAccessCtrl.RemoteInfo = {
  role: abilityToolAccessCtrl.Role.CONTROLLER,
  remoteId: 'device123',
  domainId: 'domain456'
};
abilityToolAccessCtrl.verifyControllerDevicePackage(ticketInfo, remoteInfo).then((data: Array<boolean>) => {
  console.info('verifyControllerDevicePackage success, data: ' + JSON.stringify(data));
}).catch((err: BusinessError): void => {
  console.error(`verifyControllerDevicePackage fail, code: ${err.code}, message: ${err.message}`);
});
```

## abilityToolAccessCtrl.verifyControlledDevicePackage

verifyControlledDevicePackage(ticketInfo: RemoteAuthPackage[]): Promise&lt;boolean[]&gt;

验证被控设备发送的授权包，检查消息凭据以确保授权请求合法。使用Promise异步回调。

**起始版本：** 26.1.0

**系统接口：** 此接口为系统接口。

**需要权限：** ohos.permission.QUERY_TOOL_PERMISSIONS

**系统能力：** SystemCapability.Security.Asset

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| ticketInfo | [RemoteAuthPackage](#remoteauthpackage)[] | 是 | 远程授权包列表，包含远程消息、防重放挑战值和消息完整性凭据。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;boolean[]&gt; | Promise对象。返回true表示验证通过；返回false表示验证失败。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[工具访问控制错误码](errorcode-abilityToolAccessCtrl-sys.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission denial. The interface caller does not have permission "ohos.permission.QUERY_TOOL_PERMISSIONS". |
| 202 | The caller is not a system application. |
| 24010000 | Invalid parameter. Format of ticketInfo is invalid. |
| 24010001 | Service is abnormal. Possible cause: IPC failed. |
| 24010002 | Common internal error. Possible cause: dependent service unavailable, resource access failed, etc. |
| 24010003 | The account is not logged in, network is unavailable, timeout, etc. |

**示例：**

```ts
import { abilityToolAccessCtrl } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let ticketInfo: Array<abilityToolAccessCtrl.RemoteAuthPackage> = [{
  remoteMessage: 'test_message',
  challenge: 'test_challenge',
  ticket: 'test_ticket'
}];
abilityToolAccessCtrl.verifyControlledDevicePackage(ticketInfo).then((data: Array<boolean>) => {
  console.info('verifyControlledDevicePackage success, data: ' + JSON.stringify(data));
}).catch((err: BusinessError): void => {
  console.error(`verifyControlledDevicePackage fail, code: ${err.code}, message: ${err.message}`);
});
```

## abilityToolAccessCtrl.getRemoteGrantStatus

getRemoteGrantStatus(): Promise&lt;RemoteGrantStatus&gt;

查询远程授权开关的使能状态。启用时设备可以向远程设备发起远程授权，禁用时不允许远程授权。使用Promise异步回调。

**起始版本：** 26.1.0

**系统接口：** 此接口为系统接口。

**需要权限：** ohos.permission.QUERY_TOOL_PERMISSIONS

**系统能力：** SystemCapability.Security.Asset

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;[RemoteGrantStatus](#remotegrantstatus)&gt; | Promise对象，返回远程授权开关状态。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[工具访问控制错误码](errorcode-abilityToolAccessCtrl-sys.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission denial. The interface caller does not have permission "ohos.permission.QUERY_TOOL_PERMISSIONS". |
| 202 | The caller is not a system application. |
| 24010001 | Service is abnormal. Possible cause: IPC failed. |
| 24010002 | Common internal error. Possible cause: dependent service unavailable, resource access failed, etc. |

**示例：**

```ts
import { abilityToolAccessCtrl } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

abilityToolAccessCtrl.getRemoteGrantStatus().then((data: abilityToolAccessCtrl.RemoteGrantStatus) => {
  console.info('getRemoteGrantStatus success, data: ' + data);
}).catch((err: BusinessError): void => {
  console.error(`getRemoteGrantStatus fail, code: ${err.code}, message: ${err.message}`);
});
```

## abilityToolAccessCtrl.updateRemoteGrantStatus

updateRemoteGrantStatus(remoteGrantStatus: RemoteGrantStatus): Promise&lt;void&gt;

修改远程授权状态，开启或关闭远程授权使能开关。启用时设备可以向远程设备发起远程授权，禁用时不允许远程授权。使用Promise异步回调。

**起始版本：** 26.1.0

**系统接口：** 此接口为系统接口。

**需要权限：** ohos.permission.MANAGE_TOOL_RUNTIME_PERMISSIONS

**系统能力：** SystemCapability.Security.Asset

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| remoteGrantStatus | [RemoteGrantStatus](#remotegrantstatus) | 是 | 要设置的远程授权状态。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[工具访问控制错误码](errorcode-abilityToolAccessCtrl-sys.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission denial. The interface caller does not have permission "ohos.permission.MANAGE_TOOL_RUNTIME_PERMISSIONS". |
| 202 | The caller is not a system application. |
| 24010000 | Invalid parameter. RemoteGrantStatus is invalid. |
| 24010001 | Service is abnormal. Possible cause: IPC failed. |
| 24010002 | Common internal error. Possible cause: dependent service unavailable, resource access failed, etc. |

**示例：**

```ts
import { abilityToolAccessCtrl } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

abilityToolAccessCtrl.updateRemoteGrantStatus(abilityToolAccessCtrl.RemoteGrantStatus.ENABLE).then(() => {
  console.info('updateRemoteGrantStatus success');
}).catch((err: BusinessError): void => {
  console.error(`updateRemoteGrantStatus fail, code: ${err.code}, message: ${err.message}`);
});
```

## RemoteControlParams

表示远程控制交互参数。

**起始版本：** 26.1.0

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Security.Asset

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| challenge | string | 否 | 是 | 防重放挑战值，用于防止重放攻击。合法的challenge由[generateControlledDevicePackage](#abilitytoolaccessctrlgeneratecontrolleddevicepackage)接口获取。<br>默认值：空字符串。 |
| remoteControlTicket | string | 否 | 是 | 可信设备的远程控制凭证，用于远程控制场景同账号下可信设备的身份验证。<br>默认值：空字符串。 |
| controlledDeviceName | string | 否 | 是 | 被控设备的设备名称。<br>默认值：空字符串。 |
| controllerDeviceName | string | 否 | 是 | 主控设备的设备名称。<br>默认值：空字符串。 |
| signVerifyMsg | string | 否 | 是 | 签名认证需要的额外信息，如调用方包名，模块名等。<br>默认值：空字符串。 |

## CliCmdInfo

表示CLI（Command Line Interface，命令行界面）命令信息。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Security.Asset

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| cliCmdName | string | 否 | 否 | CLI命令名称，用于指定待查询或授权的CLI命令。需传入系统支持的CLI命令名称，如'ohos-displayManager'。 |
| subCliCmdName | string | 否 | 否 | CLI子命令名称，用于指定待查询或授权的CLI子命令。需传入指定CLI命令支持的子命令名称，如'set-brightness'。 |

## PermissionQuery

表示权限查询信息。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Security.Asset

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| operationInfo | Array&lt;[OperationInfo](#operationinfo)&gt; | 否 | 否 | 操作信息列表，指定待查询的CLI命令或API接口。 |
| needTicket | boolean | 否 | 是 | 是否需要生成ticket用于本地或远程授权。true表示需要生成ticket，false表示不需要。当设置为true时，仅在本次查询结果通过的情况下才会返回ticket信息。<br>默认值：false |
| ticketExpireTimeMs | number | 否 | 是 | ticket过期时间，单位为毫秒。取值范围：1~86400000（24小时），超过最大值将返回错误码24010000。需配合needTicket参数使用，仅当needTicket为true时本参数生效。默认值10000适用于常规授权场景，长时间远程授权场景可适当延长。<br>默认值：10000 |
| remoteInfo | [RemoteInfo](#remoteinfo) | 否 | 是 | 远端设备信息。用于远程授权场景，包含设备角色、设备ID、华为账号ID等远程设备相关信息。<br>**起始版本：** 26.1.0 |
| callerTokenId | number | 否 | 是 | 调用方进程的tokenId。当需要为其他进程查询或授权时，可指定目标进程的tokenId。<br>如果未传入该参数，默认获取调用方进程的tokenId。|
| domainId | string | 否 | 是 | 域标识。<br>如果未传入该参数，则默认获取调用方当前的域标识。|

## RemoteInfo

表示远端设备信息。

**起始版本：** 26.1.0

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Security.Asset

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| role | [Role](#role) | 否 | 否 | 设备角色，表示设备是控制器还是受控设备。 |
| remoteId | string | 否 | 否 | 远端设备ID，用于唯一标识远端设备。 |
| domainId | string | 否 | 否 | 华为账号ID，用于标识设备登录的华为账号。 |
| remoteControlParams | [RemoteControlParams](#remotecontrolparams) | 否 | 是 | 远程控制中的交互参数，包含防重放挑战值、远程控制凭证等信息。 |

## OperationInfo

表示操作信息。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Security.Asset

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| operationType | [OperationType](#operationtype) | 否 | 否 | 操作类型，表示操作是CLI命令还是API接口。 |
| info | [CliCmdInfo](#clicmdinfo) \| [Permissions](../../security/AccessToken/app-permissions.md) | 否 | 否 | 操作具体信息。当operationType为CLI时，info为CliCmdInfo；当operationType为API时，info为权限名称。如果operationType和info的类型不匹配，会导致参数错误。 |

## PermissionInfo

表示权限信息。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Security.Asset

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| permission | string | 否 | 否 | 权限名称，合法的权限名取值可在[应用权限列表](../../security/AccessToken/app-permissions.md)中查询。 |
| permissionStatus | [PermissionStatus](js-apis-abilityAccessCtrl.md#permissionstatus20) | 否 | 否 | 权限状态。 |
| authStatusInfo | [AuthStatusInfo](#authstatusinfo) | 否 | 是 | 授权状态信息。<br>该项作为出参；当PermissionInfo作为入参时，该项无需传入，如果传入会被忽略。默认值为undefined。|

## AuthStatusInfo

表示授权状态信息。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Security.Asset

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| authStatus | [AuthStatus](#authstatus) | 否 | 是 | 授权状态。作为入参时，该项无需传入，如果传入会被忽略；作为出参时，该项返回实际的授权状态，表示权限的授权结果。 |
| flag | number | 否 | 是 | 授权标志，用于标识权限授权的相关属性（如授权类型、授权持久性等）。<br>作为入参时，该项无需传入，如果传入会被忽略，默认值为0；作为出参时，该项返回实际的授权标志。|

## PermissionQueryResult

表示权限查询结果。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Security.Asset

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| needDialog | boolean | 否 | 否 | 是否需要弹窗。true表示需要弹窗请求用户授权，false表示不需要弹窗。 |
| permissionResults | Array&lt;[PermissionInfo](#permissioninfo)&gt; | 否 | 否 | 权限状态结果列表。 |
| ticket | [TicketInfo](#ticketinfo) | 否 | 是 | ticket信息。<br>当入参传入的[permissionQuery.needTicket](#permissionquery)为true，且本次查询结果通过时，返回ticket信息。 |

## TicketInfo

表示ticket信息。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Security.Asset

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| message | string | 否 | 否 | ticket消息，用于传递授权相关的授权信息、提示信息和状态描述。 |
| challenge | string | 否 | 否 | 挑战值，用于验证ticket的合法性。 |
| ticket | string | 否 | 否 | ticket字符串，用于权限验证。 |

## RemoteAuthPackage

表示远程授权包。

**起始版本：** 26.1.0

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Security.Asset

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| remoteMessage | string | 否 | 否 | 远程消息，用于传递远程授权相关的信息。 |
| challenge | string | 否 | 否 | 防重放挑战值，用于保护授权包的安全性。 |
| ticket | string | 否 | 否 | 远程消息的完整性签名信息，用于远程权限验证。 |

## UserAuthResult

表示用户授权结果。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Security.Asset

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| permissionInfo | Array&lt;[PermissionInfo](#permissioninfo)&gt; | 否 | 否 | 权限信息列表，包含权限名称和授权状态。 |
| permissionQuery | [PermissionQuery](#permissionquery) | 否 | 否 | 对应的权限查询信息。 |

## RemoteUserAuthResults

表示远程用户授权结果。

**起始版本：** 26.1.0

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Security.Asset

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| results | [RemoteUserAuthItem](#remoteuserauthitem)[] | 否 | 否 | 授权结果列表，包含权限名称和授权结果。 |
| permissionQuery | [PermissionQuery](#permissionquery) | 否 | 否 | 权限查询信息，用于关联授权结果与查询请求。 |

## RemoteUserAuthItem

表示远程用户授权项。

**起始版本：** 26.1.0

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Security.Asset

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| permission | string | 否 | 否 | 权限名称，合法的权限名取值可在[应用权限列表](../../security/AccessToken/app-permissions.md)中查询。 |
| authResult | string | 否 | 否 | 授权结果，表示权限的授权状态。支持的取值包括DENIED（用户未授权）、GRANTED（已授权）、NOT_DETERMINED（未操作授权）、INVALID（无效权限）、RESTRICTED（限制授权）。 |

## AuthStatus

表示授权状态枚举。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Security.Asset

| 名称 | 值 | 说明 |
| -------- | -------- | -------- |
| REQUIRE_AUTH | 0 | 需要授权。 |
| FORBIDDEN | 1 | 禁止授权。 |
| AUTHORIZED | 2 | 已授权。 |
| RESTRICTED | 3 | 受限制，权限受系统或策略限制。 |
| REMOTE_RESTRICTED | 4 | 远程受限制，远程设备的权限受限制。 |


## Role

表示设备角色枚举。

**起始版本：** 26.1.0

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Security.Asset

| 名称 | 值 | 说明 |
| -------- | -------- | -------- |
| CONTROLLER | 0x01 | 主控设备，发起远程控制的设备。 |
| CONTROLLED | 0x02 | 被控设备，接受远程控制指令的设备。 |


## OperationType

表示操作类型枚举。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Security.Asset

| 名称 | 值 | 说明 |
| -------- | -------- | -------- |
| CLI | 0x01 | CLI命令操作。 |
| API | 0x02 | API接口操作。 |

## RemoteGrantStatus

表示远程授权状态枚举。

**起始版本：** 26.1.0

**系统接口：** 此接口为系统接口。

**系统能力：** SystemCapability.Security.Asset

| 名称 | 值 | 说明 |
| -------- | -------- | -------- |
| ENABLE | 0x01 | 启用远程授权，允许设备向远程设备授予权限。 |
| DISABLE | 0x02 | 禁用远程授权，不允许远程授权。 |
