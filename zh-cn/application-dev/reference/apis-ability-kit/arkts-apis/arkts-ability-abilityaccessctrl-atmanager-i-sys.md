# AtManager

程序访问控制管理类，提供权限校验、运行时权限弹窗申请、设置页授权引导、全局开关请求和权限状态监听等能力。通过[createAtManager](arkts-ability-abilityaccessctrl-createatmanager-f.md#createatmanager-1)获取实例。

**起始版本：** 8

<!--Device-abilityAccessCtrl-interface AtManager--><!--Device-abilityAccessCtrl-interface AtManager-End-->

**系统能力：** SystemCapability.Security.AccessToken

## 导入模块

```TypeScript
import { Context, Permissions, PermissionRequestResult } from '@kit.AbilityKit';
```

## generateCliAuthResult

```TypeScript
generateCliAuthResult(
      hostTokenID: number,
      agentID: string,
      authInfoList: Array<CliAuthInfo>): Promise<ToolAuthResult>
```

根据CLI授权信息生成授权结果。使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.MANAGE_TOOL_RUNTIME_PERMISSIONS

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AtManager-generateCliAuthResult(
      hostTokenID: int,
      agentID: string,
      authInfoList: Array<CliAuthInfo>): Promise<ToolAuthResult>--><!--Device-AtManager-generateCliAuthResult(
      hostTokenID: int,
      agentID: string,
      authInfoList: Array<CliAuthInfo>): Promise<ToolAuthResult>-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hostTokenID | number | 是 | 访问CLI指令的应用的tokenID。可通过应用BundleInfo中的ApplicationInfo中的[accessTokenId](arkts-ability-applicationinfo-i.md#accesstokenid)字段获取。传入无效值时返回错误码12100001。<br>取值限定为整数。取值约束：该参数必须为大于0的整数。<br>BundleInfo获取可参考：[bundleManager.getBundleInfoSync](arkts-ability-bundlemanager-getbundleinfosync-f.md#getbundleinfosync-1)。 |
| agentID | string | 是 | 用于标识发起CLI相关操作的智能体体标识。传入无效值时返回错误码12100001。<br>取值约束：长度不能超过48个字符。 |
| authInfoList | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<CliAuthInfo> | 是 | CLI授权信息列表，每项包含CLI信息（主命令和子命令名称）、待授权的权限名称列表和对应的授权结果列表。传入无效值时返回错误码12100001。<br>最大长度为99且不能为空。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<ToolAuthResult> | Promise对象，返回生成的授权结果，包含授权结果字符串列表，可用于传递给CLI工具执行命令。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. Interface caller does not have permission"ohos.permission.MANAGE_TOOL_RUNTIME_PERMISSIONS". |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. Interface caller is not a system application. |
| [12100001](../errorcode-access-token.md#12100001-入参错误) | Invalid parameter. The hostTokenID is 0, the agentID exceeds 48characters, authInfoList is empty or contains more than 99 items, the cliName in cliInfo of an item in authInfoList is empty or exceeds 256 characters, the subCliName in cliInfo of an item in authInfoList exceeds 256 characters, a permission name in permissionNames of an item in authInfoList is empty or exceeds256 characters, or the number of permissionNames does not equal the number of authorizationResults in an item in authInfoList. |
| [12100002](../errorcode-access-token.md#12100002-tokenid不存在) | The specified tokenID does not exist. |
| [12100003](../errorcode-access-token.md#12100003-权限名不存在) | A permission name in permissionNames of an item in authInfoList does not exist. |
| [12100007](../errorcode-access-token.md#12100007-系统服务工作异常) | Service exception. |
| [12100009](../errorcode-access-token.md#12100009-服务内部错误) | Common internal error. The account is not logged in, network is not connected or an internal error occurs when generating authorization results. |

**示例：**

```TypeScript
import { abilityAccessCtrl, Permissions } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let atManager: abilityAccessCtrl.AtManager = abilityAccessCtrl.createAtManager();
let hostTokenID: number = 0; // 获取方式可参考AtManager章节的描述。
let agentID: string = 'agent.demo';
let authInfoList: Array<abilityAccessCtrl.CliAuthInfo> = [{
  cliInfo: {
    cliName: 'ohos-example',
    subCliName: 'run'
  },
  permissionNames: ['ohos.permission.ACCESS_SYSTEM_SETTINGS' as Permissions],
  authorizationResults: [true]
}];
atManager.generateCliAuthResult(hostTokenID, agentID, authInfoList).then((data: abilityAccessCtrl.ToolAuthResult) => {
  console.info('generateCliAuthResult success, data: ' + JSON.stringify(data));
}).catch((err: BusinessError): void => {
  console.error(`generateCliAuthResult fail, code: ${err.code}, message: ${err.message}`);
});

```

## getCliPermissionRequestInfo

```TypeScript
getCliPermissionRequestInfo(agentID: string, cliInfoList: Array<CliInfo>): Promise<PermissionDialogResult>
```

查询CLI（Command Line Interface，命令行界面）命令是否需要权限弹窗，调用成功后，返回每条命令对应的权限弹窗判定结果。使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.QUERY_TOOL_PERMISSIONS

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AtManager-getCliPermissionRequestInfo(agentID: string, cliInfoList: Array<CliInfo>): Promise<PermissionDialogResult>--><!--Device-AtManager-getCliPermissionRequestInfo(agentID: string, cliInfoList: Array<CliInfo>): Promise<PermissionDialogResult>-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| agentID | string | 是 | 用于标识发起CLI相关操作的智能体标识。传入无效值时返回错误码12100001。<br>取值约束：长度不能超过48个字符。 |
| cliInfoList | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<CliInfo> | 是 | 待查询的CLI信息列表。每项包含一条命令及其子命令信息；建议按实际即将执行的命令集合传入，避免无关命令扩大判定范围。传入无效值时返回错误码12100001。<br>最大长度为99且不能为空。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<PermissionDialogResult> | Promise对象，返回每条CLI命令的权限弹窗判定结果，包含是否需要弹窗、未满足的权限列表及决策状态等信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. Interface caller does not have permission"ohos.permission.QUERY_TOOL_PERMISSIONS". |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. Interface caller is not a system application. |
| [12100001](../errorcode-access-token.md#12100001-入参错误) | Invalid parameter. The agentID exceeds 48 characters, cliInfoList is empty or exceeds 99 items, the cliName of an item in cliInfoList is empty or exceeds 256 characters, the subCliName of an item in cliInfoList exceeds 256 characters, or the CLI command does not exist. |
| [12100007](../errorcode-access-token.md#12100007-系统服务工作异常) | Service exception. |
| [12100009](../errorcode-access-token.md#12100009-服务内部错误) | Common inner error. The account is not logged in, network is not connected or an internal error occurs when querying CLI permissions or generating auth results. |

**示例：**

```TypeScript
import { abilityAccessCtrl } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let atManager: abilityAccessCtrl.AtManager = abilityAccessCtrl.createAtManager();
let agentID: string = 'agent.demo';
let cliInfoList: Array<abilityAccessCtrl.CliInfo> = [{
  cliName: 'ohos-example',
  subCliName: 'run'
}];
atManager.getCliPermissionRequestInfo(agentID, cliInfoList).then((data: abilityAccessCtrl.PermissionDialogResult) => {
  console.info('getCliPermissionRequestInfo success, data: ' + JSON.stringify(data));
}).catch((err: BusinessError): void => {
  console.error(`getCliPermissionRequestInfo fail, code: ${err.code}, message: ${err.message}`);
});

```

## getCliPermissions

```TypeScript
getCliPermissions(
      hostTokenID: number,
      agentID: string,
      cliInfoList: Array<CliInfo>): Promise<CliPermissionsResult>
```

查询指定应用使用的CLI命令依赖的CLI权限及映射的运行时权限。调用成功后返回每条命令的CLI权限决策状态和运行时权限映射列表。使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.MANAGE_TOOL_RUNTIME_PERMISSIONS

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AtManager-getCliPermissions(
      hostTokenID: int,
      agentID: string,
      cliInfoList: Array<CliInfo>): Promise<CliPermissionsResult>--><!--Device-AtManager-getCliPermissions(
      hostTokenID: int,
      agentID: string,
      cliInfoList: Array<CliInfo>): Promise<CliPermissionsResult>-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hostTokenID | number | 是 | 访问CLI指令的应用的tokenID。可通过应用BundleInfo中的ApplicationInfo中的[accessTokenId](arkts-ability-applicationinfo-i.md#accesstokenid)字段获取。传入无效值时返回错误码12100001。<br>取值限定为整数。取值约束：该参数必须为大于0的整数。<br>BundleInfo获取可参考：[bundleManager.getBundleInfoSync](arkts-ability-bundlemanager-getbundleinfosync-f.md#getbundleinfosync-1)。 |
| agentID | string | 是 | 用于标识发起CLI相关操作的智能体标识。传入无效值时返回错误码12100001。<br>取值约束：长度不能超过48个字符。 |
| cliInfoList | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<CliInfo> | 是 | 待查询的CLI信息列表。每项包含一条命令及其子命令信息。传入无效值时返回错误码12100001。<br>最大长度为99且不能为空。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<CliPermissionsResult> | Promise对象，返回每条CLI命令依赖的CLI权限及其对应的运行时权限映射信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. Interface caller does not have permission"ohos.permission.MANAGE_TOOL_RUNTIME_PERMISSIONS". |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. Interface caller is not a system application. |
| [12100001](../errorcode-access-token.md#12100001-入参错误) | Invalid parameter. The hostTokenID is 0, the agentID exceeds 48characters, cliInfoList is empty or contains more than 99 items, the cliName of an item in cliInfoList is empty or exceeds 256 characters, the subCliName of an item in cliInfoList exceeds 256 characters, or the CLI command does not exist. |
| [12100002](../errorcode-access-token.md#12100002-tokenid不存在) | The specified tokenID does not exist. |
| [12100007](../errorcode-access-token.md#12100007-系统服务工作异常) | Service exception. |
| [12100009](../errorcode-access-token.md#12100009-服务内部错误) | Common internal error. An internal error occurs when querying CLI permissions or runtime permission information. |

**示例：**

```TypeScript
import { abilityAccessCtrl } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let atManager: abilityAccessCtrl.AtManager = abilityAccessCtrl.createAtManager();
let hostTokenID: number = 0; // 获取方式可参考AtManager章节的描述。
let agentID: string = 'agent.demo';
let cliInfoList: Array<abilityAccessCtrl.CliInfo> = [{
  cliName: 'ohos-example',
  subCliName: 'run'
}];
atManager.getCliPermissions(hostTokenID, agentID, cliInfoList).then((data: abilityAccessCtrl.CliPermissionsResult) => {
  console.info('getCliPermissions success, data: ' + JSON.stringify(data));
}).catch((err: BusinessError): void => {
  console.error(`getCliPermissions fail, code: ${err.code}, message: ${err.message}`);
});

```

## getPermissionFlags

```TypeScript
getPermissionFlags(tokenID: number, permissionName: Permissions): Promise<number>
```

获取指定应用的指定权限的标志。使用Promise异步回调。

**起始版本：** 8

**需要权限：** ohos.permission.GET_SENSITIVE_PERMISSIONS or ohos.permission.GRANT_SENSITIVE_PERMISSIONS or ohos.permission.REVOKE_SENSITIVE_PERMISSIONS

<!--Device-AtManager-getPermissionFlags(tokenID: int, permissionName: Permissions): Promise<int>--><!--Device-AtManager-getPermissionFlags(tokenID: int, permissionName: Permissions): Promise<int>-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tokenID | number | 是 | 目标应用的身份标识。可通过应用BundleInfo中的ApplicationInfo中的[accessTokenId](arkts-ability-applicationinfo-i.md#accesstokenid)字段获取。传入无效值时返回错误码12100001。<br>取值限定为整数。取值约束：该参数必须为大于0的整数。<br>BundleInfo获取可参考：[bundleManager.getBundleInfoSync](arkts-ability-bundlemanager-getbundleinfosync-f.md#getbundleinfosync-1)。 |
| permissionName | Permissions | 是 | 查询的权限名称。传入无效值时返回错误码12100001。<br>取值约束：权限名长度不能超过256个字符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<number> | Promise对象，返回查询到的权限标记值。标记值的含义请参见[PermissionStatusInfo](arkts-ability-abilityaccessctrl-permissionstatusinfo-i-sys.md)中的grantFlags字段说明。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. Interface caller does not have permission specified below. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. Interface caller is not a system app. |
| [12100001](../errorcode-access-token.md#12100001-入参错误) | Invalid parameter. The tokenID is 0, or the permissionName exceeds 256characters. |
| [12100002](../errorcode-access-token.md#12100002-tokenid不存在) | The specified tokenID does not exist. |
| [12100003](../errorcode-access-token.md#12100003-权限名不存在) | The specified permission does not exist or is not declared in the module.json file. |
| [12100006](../errorcode-access-token.md#12100006-指定的应用不支持被授予或被取消授予指定的权限) | The operation is not allowed. Either the application is a sandbox or the tokenID is from a remote device. |
| [12100007](../errorcode-access-token.md#12100007-系统服务工作异常) | Service exception. |

**示例：**

```TypeScript
import { abilityAccessCtrl } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let atManager: abilityAccessCtrl.AtManager = abilityAccessCtrl.createAtManager();
let tokenID: number = 0; // 获取tokenID的方式可参考AtManager章节的描述。
atManager.getPermissionFlags(tokenID, 'ohos.permission.GRANT_SENSITIVE_PERMISSIONS').then((data: number) => {
  console.info(`getPermissionFlags success, result: ${data}`);
}).catch((err: BusinessError): void => {
  console.error(`getPermissionFlags fail, code: ${err.code}, message: ${err.message}`);
});

```

## getPermissionRequestToggleStatus

```TypeScript
getPermissionRequestToggleStatus(permissionName: Permissions): Promise<PermissionRequestToggleStatus>
```

获取当前用户指定权限的弹窗开关状态。使用Promise异步回调。

**起始版本：** 12

**需要权限：** ohos.permission.GET_SENSITIVE_PERMISSIONS

<!--Device-AtManager-getPermissionRequestToggleStatus(permissionName: Permissions): Promise<PermissionRequestToggleStatus>--><!--Device-AtManager-getPermissionRequestToggleStatus(permissionName: Permissions): Promise<PermissionRequestToggleStatus>-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| permissionName | Permissions | 是 | 待查询弹窗开关状态的权限名称。传入无效值时返回错误码12100001。<br>取值约束：权限名长度不能超过256个字符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<PermissionRequestToggleStatus> | Promise对象，返回指定权限的弹窗开关状态值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. Interface caller does not have permission specified below. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. Interface caller is not a system app. |
| [12100001](../errorcode-access-token.md#12100001-入参错误) | Invalid parameter. The permissionName exceeds 256 characters, or the specified permission is not a user_grant permission. |
| [12100003](../errorcode-access-token.md#12100003-权限名不存在) | The specified permission does not exist. |
| [12100007](../errorcode-access-token.md#12100007-系统服务工作异常) | Service exception. |

**示例：**

```TypeScript
import { abilityAccessCtrl, Permissions } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let atManager: abilityAccessCtrl.AtManager = abilityAccessCtrl.createAtManager();
let permission: Permissions = 'ohos.permission.CAMERA';

atManager.getPermissionRequestToggleStatus(permission).then((res: abilityAccessCtrl.PermissionRequestToggleStatus) => {
  if (res == abilityAccessCtrl.PermissionRequestToggleStatus.CLOSED) {
    console.info('getPermissionRequestToggleStatus: The toggle status is close');
  } else {
    console.info('getPermissionRequestToggleStatus: The toggle status is open');
  }
}).catch((err: BusinessError): void => {
  console.error(`getPermissionRequestToggleStatus fail, code: ${err.code}, message: ${err.message}`);
});

```

## getPermissionsStatus

```TypeScript
getPermissionsStatus(tokenID: number, permissionList: Array<Permissions>): Promise<Array<PermissionStatus>>
```

获取指定应用权限状态列表。使用Promise异步回调。

**起始版本：** 12

**需要权限：** ohos.permission.GET_SENSITIVE_PERMISSIONS

<!--Device-AtManager-getPermissionsStatus(tokenID: int, permissionList: Array<Permissions>): Promise<Array<PermissionStatus>>--><!--Device-AtManager-getPermissionsStatus(tokenID: int, permissionList: Array<Permissions>): Promise<Array<PermissionStatus>>-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tokenID | number | 是 | 目标应用的身份标识。可通过应用BundleInfo中的ApplicationInfo中的[accessTokenId](arkts-ability-applicationinfo-i.md#accesstokenid)字段获取。传入无效值时返回错误码12100001。<br>取值限定为整数。取值约束：该参数必须为大于0的整数。<br>BundleInfo获取可参考：[bundleManager.getBundleInfoSync](arkts-ability-bundlemanager-getbundleinfosync-f.md#getbundleinfosync-1)。 |
| permissionList | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<Permissions> | 是 | 待获取权限状态的权限名列表。传入无效值时返回错误码12100001。<br>最大长度为1024且不能为空。取值约束：权限名长度不能超过256个字符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Array<PermissionStatus>> | Promise对象，返回查询到的权限状态列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. Interface caller does not have permission"ohos.permission.GET_SENSITIVE_PERMISSIONS". |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. Interface caller is not a system app. |
| [12100001](../errorcode-access-token.md#12100001-入参错误) | Invalid parameter. The tokenID is 0 or the permissionList is empty or exceeds the size limit. |
| [12100002](../errorcode-access-token.md#12100002-tokenid不存在) | The specified tokenID does not exist. |
| [12100007](../errorcode-access-token.md#12100007-系统服务工作异常) | Service exception. |

**示例：**

```TypeScript
import { abilityAccessCtrl } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let atManager: abilityAccessCtrl.AtManager = abilityAccessCtrl.createAtManager();
let tokenID: number = 0; // 获取tokenID的方式可参考AtManager章节的描述。
atManager.getPermissionsStatus(tokenID, ['ohos.permission.CAMERA']).then((data: Array<abilityAccessCtrl.PermissionStatus>) => {
  console.info(`getPermissionsStatus success, result: ${data}`);
}).catch((err: BusinessError): void => {
  console.error(`getPermissionsStatus fail, code: ${err.code}, message: ${err.message}`);
});

```

## getVersion

```TypeScript
getVersion(): Promise<number>
```

获取当前权限管理的数据版本号。使用Promise异步回调。

**起始版本：** 9

<!--Device-AtManager-getVersion(): Promise<int>--><!--Device-AtManager-getVersion(): Promise<int>-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<number> | Promise对象，返回查询到的版本号。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. Interface caller is not a system app. |

**示例：**

```TypeScript
import { abilityAccessCtrl } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let atManager: abilityAccessCtrl.AtManager = abilityAccessCtrl.createAtManager();
let promise = atManager.getVersion();
promise.then((data: number) => {
  console.info(`getVersion promise: data->${data}`);
}).catch((err: BusinessError): void => {
  console.error(`getVersion fail, code: ${err.code}, message: ${err.message}`);
});

```

## grantPermission

```TypeScript
grantPermission(tokenID: number, permissionName: Permissions, permissionFlags: number): Promise<void>
```

授予应用权限。调用成功后，指定应用获得该权限，可以访问相应的受保护资源。与[grantUserGrantedPermission](arkts-ability-abilityaccessctrl-atmanager-i-sys.md#grantusergrantedpermission-1)仅支持user_grant类型权限不同,该接口同时支持user_grant和manual_settings类型的权限授予。使用Promise异步回调。

**起始版本：** 21

**需要权限：** ohos.permission.GRANT_SENSITIVE_PERMISSIONS

<!--Device-AtManager-grantPermission(tokenID: int, permissionName: Permissions, permissionFlags: int): Promise<void>--><!--Device-AtManager-grantPermission(tokenID: int, permissionName: Permissions, permissionFlags: int): Promise<void>-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tokenID | number | 是 | 目标应用的身份标识。可通过应用BundleInfo中的ApplicationInfo中的[accessTokenId](arkts-ability-applicationinfo-i.md#accesstokenid)字段获取。传入无效值时返回错误码12100001。<br>取值限定为整数。取值约束：该参数必须为大于0的整数。<br>BundleInfo获取可参考：[bundleManager.getBundleInfoSync](arkts-ability-bundlemanager-getbundleinfosync-f.md#getbundleinfosync-1)。 |
| permissionName | Permissions | 是 | 被授予的权限名称。权限名长度不能超过256个字符，超过限制时返回错误码12100001。 |
| permissionFlags | number | 是 | 授权选项。<br>取值限定为整数。<br>- 1表示当次用户若选择禁止该权限，下次权限弹窗仍可以弹出申请用户授权。<br>- 2表示当次用户若选择禁止该权限，下次不会再弹出权限弹窗，用户需要在系统设置的权限管理中进行授权。<br>- 64表示当次用户若选择仅本次允许，权限仅本次授权。应用切换后台状态或退出后取消授权。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. Interface caller does not have permission"ohos.permission.GRANT_SENSITIVE_PERMISSIONS". |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. Interface caller is not a system app. |
| [12100001](../errorcode-access-token.md#12100001-入参错误) | Invalid parameter. The tokenID is 0, the permissionName exceeds 256 characters or is not declared in the module.json file, or the flags value is invalid. |
| [12100002](../errorcode-access-token.md#12100002-tokenid不存在) | The specified tokenID does not exist. |
| [12100003](../errorcode-access-token.md#12100003-权限名不存在) | The specified permission does not exist. |
| [12100006](../errorcode-access-token.md#12100006-指定的应用不支持被授予或被取消授予指定的权限) | The application specified by the tokenID is not allowed to be granted with the specified permission. Either the application is a sandbox or the tokenID is from a remote device. |
| [12100007](../errorcode-access-token.md#12100007-系统服务工作异常) | Service exception. |
| [12100014](../errorcode-access-token.md#12100014-非预期的权限) | Unexpected permission. The specified permission is not a user_grant or manual_settings permission. |

**示例：**

```TypeScript
import { abilityAccessCtrl } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let atManager: abilityAccessCtrl.AtManager = abilityAccessCtrl.createAtManager();
let tokenID: number = 0; // 获取tokenID的方式可参考AtManager章节的描述。
let permissionFlags: number = 2;
atManager.grantPermission(tokenID, 'ohos.permission.READ_AUDIO', permissionFlags).then(() => {
  console.info('grantPermission success');
}).catch((err: BusinessError): void => {
  console.error(`grantPermission fail, code: ${err.code}, message: ${err.message}`);
});

```

## grantUserGrantedPermission

```TypeScript
grantUserGrantedPermission(tokenID: number, permissionName: Permissions, permissionFlags: number): Promise<void>
```

授予应用user_grant权限。调用成功后，应用获得该user_grant权限，可以访问相应的受保护资源。使用Promise异步回调。

本接口仅支持授予user_grant类型的权限。若需要授予user_grant或manual_settings类型权限，建议使用[grantPermission](arkts-ability-abilityaccessctrl-atmanager-i-sys.md#grantpermission-1)。

**起始版本：** 8

**需要权限：** ohos.permission.GRANT_SENSITIVE_PERMISSIONS

<!--Device-AtManager-grantUserGrantedPermission(tokenID: int, permissionName: Permissions, permissionFlags: int): Promise<void>--><!--Device-AtManager-grantUserGrantedPermission(tokenID: int, permissionName: Permissions, permissionFlags: int): Promise<void>-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tokenID | number | 是 | 目标应用的身份标识。可通过应用BundleInfo中的ApplicationInfo中的[accessTokenId](arkts-ability-applicationinfo-i.md#accesstokenid)字段获取。传入无效值时返回错误码12100001。<br>取值限定为整数。取值约束：该参数必须为大于0的整数。<br>BundleInfo获取可参考：[bundleManager.getBundleInfoSync](arkts-ability-bundlemanager-getbundleinfosync-f.md#getbundleinfosync-1)。 |
| permissionName | Permissions | 是 | 被授予的权限名称。超过限制时返回错误码12100001。<br>取值约束：权限名长度不能超过256个字符。 |
| permissionFlags | number | 是 | 授权选项。<br>取值限定为整数。<br>- 1表示当次用户若选择禁止该权限，下次权限弹窗仍可以弹出申请用户授权。<br>- 2表示当次用户若选择禁止该权限，下次不会再弹出权限弹窗，用户需要在系统设置的权限管理中进行授权。<br>- 64表示当次用户若选择仅本次允许，权限仅本次授权。应用切换后台状态或退出后取消授权。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. Interface caller does not have permission"ohos.permission.GRANT_SENSITIVE_PERMISSIONS". |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. Interface caller is not a system app. |
| [12100001](../errorcode-access-token.md#12100001-入参错误) | Invalid parameter. The tokenID is 0, the permissionName exceeds 256characters or is not declared in the module.json file, or the flags value is invalid. |
| [12100002](../errorcode-access-token.md#12100002-tokenid不存在) | The specified tokenID does not exist. |
| [12100003](../errorcode-access-token.md#12100003-权限名不存在) | The specified permission does not exist or is not a user_grant permission. |
| [12100006](../errorcode-access-token.md#12100006-指定的应用不支持被授予或被取消授予指定的权限) | The application specified by the tokenID is not allowed to be granted with the specified permission.Either the application is a sandbox or the tokenID is from a remote device. |
| [12100007](../errorcode-access-token.md#12100007-系统服务工作异常) | Service exception. |

**示例：**

```TypeScript
import { abilityAccessCtrl } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let atManager: abilityAccessCtrl.AtManager = abilityAccessCtrl.createAtManager();
let tokenID: number = 0; // 获取tokenID的方式可参考AtManager章节的描述。
let permissionFlags: number = 1;
atManager.grantUserGrantedPermission(tokenID, 'ohos.permission.READ_AUDIO', permissionFlags).then(() => {
  console.info('grantUserGrantedPermission success');
}).catch((err: BusinessError): void => {
  console.error(`grantUserGrantedPermission fail, code: ${err.code}, message: ${err.message}`);
});

```

## grantUserGrantedPermission

```TypeScript
grantUserGrantedPermission(
        tokenID: number,
        permissionName: Permissions,
        permissionFlags: number,
        callback: AsyncCallback<void>
    ): void
```

授予应用user_grant权限。使用callback异步回调。调用成功后，应用获得该user_grant权限，可以访问相应的受保护资源。

**起始版本：** 8

**需要权限：** ohos.permission.GRANT_SENSITIVE_PERMISSIONS

<!--Device-AtManager-grantUserGrantedPermission(
        tokenID: int,
        permissionName: Permissions,
        permissionFlags: int,
        callback: AsyncCallback<void>
    ): void--><!--Device-AtManager-grantUserGrantedPermission(
        tokenID: int,
        permissionName: Permissions,
        permissionFlags: int,
        callback: AsyncCallback<void>
    ): void-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tokenID | number | 是 | 目标应用的身份标识。可通过应用BundleInfo中的ApplicationInfo中的[accessTokenId](arkts-ability-applicationinfo-i.md#accesstokenid)字段获取。传入无效值时返回错误码12100001。<br>取值限定为整数。取值约束：该参数必须为大于0的整数。<br>BundleInfo获取可参考：[bundleManager.getBundleInfoSync](arkts-ability-bundlemanager-getbundleinfosync-f.md#getbundleinfosync-1)。 |
| permissionName | Permissions | 是 | 被授予的权限名称。传入无效值时返回错误码12100001。<br>取值约束：权限名长度不能超过256个字符。 |
| permissionFlags | number | 是 | 授权选项。<br>取值限定为整数。<br>- 1表示当次用户若选择禁止该权限，下次权限弹窗仍可以弹出申请用户授权。<br>- 2表示当次用户若选择禁止该权限，下次不会再弹出权限弹窗，用户需要在系统设置的权限管理中进行授权。<br>- 64表示当次用户若选择仅本次允许，权限仅本次授权。应用切换后台状态或退出后取消授权。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。当授予权限成功时，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. Interface caller does not have permission"ohos.permission.GRANT_SENSITIVE_PERMISSIONS". |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. Interface caller is not a system app. |
| [12100001](../errorcode-access-token.md#12100001-入参错误) | Invalid parameter. The tokenID is 0, the permissionName exceeds 256characters or is not declared in the module.json file,or the flags value is invalid. |
| [12100002](../errorcode-access-token.md#12100002-tokenid不存在) | The specified tokenID does not exist. |
| [12100003](../errorcode-access-token.md#12100003-权限名不存在) | The specified permission does not exist or is not a user_grant permission. |
| [12100006](../errorcode-access-token.md#12100006-指定的应用不支持被授予或被取消授予指定的权限) | The application specified by the tokenID is not allowed to be granted with the specified permission. Either the application is a sandbox or the tokenID is from a remote device. |
| [12100007](../errorcode-access-token.md#12100007-系统服务工作异常) | Service exception. |

**示例：**

```TypeScript
import { abilityAccessCtrl } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let atManager: abilityAccessCtrl.AtManager = abilityAccessCtrl.createAtManager();
let tokenID: number = 0; // 获取tokenID的方式可参考AtManager章节的描述。
let permissionFlags: number = 1;
atManager.grantUserGrantedPermission(tokenID, 'ohos.permission.READ_AUDIO', permissionFlags, (err: BusinessError, data: void) => {
  if (err) {
    console.error(`grantUserGrantedPermission fail, code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('grantUserGrantedPermission success');
  }
});

```

## off('permissionStateChange')

```TypeScript
off(
      type: 'permissionStateChange',
      tokenIDList: Array<number>,
      permissionList: Array<Permissions>,
      callback?: Callback<PermissionStateChangeInfo>
    ): void
```

取消订阅指定tokenID列表与权限列表的权限状态变更事件。使用callback异步回调。

取消订阅时，若不传入callback，则批量取消与tokenIDList和permissionList完全匹配的所有监听回调。

> **说明**  
> 该接口通常与[on](abilityAccessCtrl.AtManager.on)配套使用，用于取消通过on创建的监听关系。

**起始版本：** 9

**需要权限：** ohos.permission.GET_SENSITIVE_PERMISSIONS

<!--Device-AtManager-off(
      type: 'permissionStateChange',
      tokenIDList: Array<int>,
      permissionList: Array<Permissions>,
      callback?: Callback<PermissionStateChangeInfo>
    ): void--><!--Device-AtManager-off(
      type: 'permissionStateChange',
      tokenIDList: Array<int>,
      permissionList: Array<Permissions>,
      callback?: Callback<PermissionStateChangeInfo>
    ): void-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'permissionStateChange' | 是 | 订阅事件类型，固定为'permissionStateChange'，权限状态变更事件。 |
| tokenIDList | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<number> | 是 | 取消订阅的tokenID列表，为空时表示取消订阅所有的应用的权限状态变化，必须与on的输入一致。应用的身份标识可通过应用BundleInfo中的ApplicationInfo中的[accessTokenId](arkts-ability-applicationinfo-i.md#accesstokenid)字段获取。传入无效值时返回错误码12100001。<br>最大长度为1024。取值约束：列表中的tokenID必须为大于0的整数。<br>BundleInfo获取可参考：[bundleManager.getBundleInfoSync](arkts-ability-bundlemanager-getbundleinfosync-f.md#getbundleinfosync-1)。 |
| permissionList | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<Permissions> | 是 | 取消订阅的权限名列表，为空时表示取消订阅所有的权限状态变化，必须与on的输入一致。传入无效值时返回错误码12100001。<br>最大长度为1024。取值约束：列表中的权限名需为有效权限名，权限名长度不能超过256个字符。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<PermissionStateChangeInfo> | 否 | 回调函数。返回取消订阅指定tokenID与指定权限名状态变更事件的对象，需与on注册时的callback一致。不传入此参数时，将取消与tokenIDList和permissionList完全匹配的所有监听回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. Interface caller does not have permission"ohos.permission.GET_SENSITIVE_PERMISSIONS". |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. Interface caller is not a system app. |
| [12100001](../errorcode-access-token.md#12100001-入参错误) | Invalid parameter. The tokenIDList or permissionList is not in the listening list. |
| [12100007](../errorcode-access-token.md#12100007-系统服务工作异常) | Service exception. |

**示例：**

```TypeScript
import { abilityAccessCtrl, Permissions, bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let atManager: abilityAccessCtrl.AtManager = abilityAccessCtrl.createAtManager();
  let bundleInfo: bundleManager.BundleInfo = bundleManager.getBundleInfoForSelfSync(bundleManager.BundleFlag.GET_BUNDLE_INFO_WITH_APPLICATION);
  let tokenIDList: Array<number> = [bundleInfo.appInfo.accessTokenId];
  let permissionList: Array<Permissions> = ['ohos.permission.DISTRIBUTED_DATASYNC'];
  atManager.off('permissionStateChange', tokenIDList, permissionList);
} catch (err) {
  let error = err as BusinessError;
  console.error(`catch errcode: ${error.code}, message: ${error.message}`);
}

```

## on('permissionStateChange')

```TypeScript
on(
      type: 'permissionStateChange',
      tokenIDList: Array<number>,
      permissionList: Array<Permissions>,
      callback: Callback<PermissionStateChangeInfo>
    ): void
```

订阅指定tokenID列表与权限列表的权限状态变更事件。使用callback异步回调。

允许指定tokenID列表与权限列表订阅多个callback。

> **说明**  
> 若新的订阅与已有订阅在tokenID列表和权限列表上存在交集，不允许使用相同的callback进行订阅。  
> 该接口通常与[off](abilityAccessCtrl.AtManager.of)配套使用，当不再需要监听时应调用off取消订阅。

**起始版本：** 9

**需要权限：** ohos.permission.GET_SENSITIVE_PERMISSIONS

<!--Device-AtManager-on(
      type: 'permissionStateChange',
      tokenIDList: Array<int>,
      permissionList: Array<Permissions>,
      callback: Callback<PermissionStateChangeInfo>
    ): void--><!--Device-AtManager-on(
      type: 'permissionStateChange',
      tokenIDList: Array<int>,
      permissionList: Array<Permissions>,
      callback: Callback<PermissionStateChangeInfo>
    ): void-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'permissionStateChange' | 是 | 订阅事件类型，固定为'permissionStateChange'，权限状态变更事件。 |
| tokenIDList | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<number> | 是 | 订阅的tokenID列表，为空时表示订阅所有的应用的权限状态变化。应用的身份标识可通过应用BundleInfo中的ApplicationInfo中的[accessTokenId](arkts-ability-applicationinfo-i.md#accesstokenid)字段获取。传入无效值时返回错误码12100001。<br>最大长度为1024。取值约束：列表中的tokenID必须为大于0的整数。<br>BundleInfo获取可参考：[bundleManager.getBundleInfoSync](arkts-ability-bundlemanager-getbundleinfosync-f.md#getbundleinfosync-1)。 |
| permissionList | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<Permissions> | 是 | 订阅的权限名列表，为空时表示订阅所有的权限状态变化。传入无效值时返回错误码12100001。<br>最大长度为1024且不能为空。取值约束：列表中的权限名需为有效权限名，权限名长度不能超过256个字符。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<PermissionStateChangeInfo> | 是 | 回调函数。订阅指定tokenID与指定权限名状态变更事件的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. Interface caller does not have permission"ohos.permission.GET_SENSITIVE_PERMISSIONS". |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. Interface caller is not a system app. |
| [12100001](../errorcode-access-token.md#12100001-入参错误) | Invalid parameter. Possible causes: 1. The tokenIDList or permissionList exceeds the size limit; 2. The tokenIDs or permissionNames in the list are all invalid. |
| [12100005](../errorcode-access-token.md#12100005-监听器数量超过限制) | The registration time has exceeded the limit. |
| [12100007](../errorcode-access-token.md#12100007-系统服务工作异常) | Service exception. |
| [12100008](../errorcode-access-token.md#12100008-内存申请失败) | Out of memory. |

**示例：**

```TypeScript
import { abilityAccessCtrl, Permissions, bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let atManager: abilityAccessCtrl.AtManager = abilityAccessCtrl.createAtManager();
  let bundleInfo: bundleManager.BundleInfo = bundleManager.getBundleInfoForSelfSync(bundleManager.BundleFlag.GET_BUNDLE_INFO_WITH_APPLICATION);
  let tokenIDList: Array<number> = [bundleInfo.appInfo.accessTokenId];
  let permissionList: Array<Permissions> = ['ohos.permission.DISTRIBUTED_DATASYNC'];

  atManager.on('permissionStateChange', tokenIDList, permissionList, (data: abilityAccessCtrl.PermissionStateChangeInfo) => {
    console.info('receive permission state change');
    console.info(`data change: ${data.change}, tokenID: ${data.tokenID}, permission name: ${data.permissionName}`);
    });
} catch (err) {
  let error = err as BusinessError;
  console.error(`catch errcode: ${error.code}, message: ${error.message}`);
}

```

## queryStatusByPermission

```TypeScript
queryStatusByPermission(
      permissionList: Array<Permissions>): Promise<Array<PermissionStatusInfo>>
```

根据权限列表查询所有已请求过该权限的应用及其权限状态。使用Promise异步回调。当查询的数据结果的大小超过50000条时，接口会直接返回12100015错误码。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.GET_SENSITIVE_PERMISSIONS

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AtManager-queryStatusByPermission(
      permissionList: Array<Permissions>): Promise<Array<PermissionStatusInfo>>--><!--Device-AtManager-queryStatusByPermission(
      permissionList: Array<Permissions>): Promise<Array<PermissionStatusInfo>>-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| permissionList | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<Permissions> | 是 | 待查询的权限名称列表。传入无效值时返回错误码12100001。<br>最大长度为1024且不能为空。取值约束：权限名长度不能超过256个字符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Array<PermissionStatusInfo>> | Promise对象，返回查询到的权限状态信息列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. Interface caller does not have permission"ohos.permission.GET_SENSITIVE_PERMISSIONS". |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. Interface caller is not a system application. |
| [12100001](../errorcode-access-token.md#12100001-入参错误) | Invalid parameter. The permissionList is empty or exceeds the size limit. |
| [12100003](../errorcode-access-token.md#12100003-权限名不存在) | The specified permission does not exist. |
| [12100007](../errorcode-access-token.md#12100007-系统服务工作异常) | Service exception. |
| [12100015](../errorcode-access-token.md#12100015-查询的数据超过上限) | The queried data exceeds the upper limit. |

**示例：**

```TypeScript
import { abilityAccessCtrl, Permissions } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let atManager: abilityAccessCtrl.AtManager = abilityAccessCtrl.createAtManager();
let permissionList: Array<Permissions> = ['ohos.permission.CAMERA'];
atManager.queryStatusByPermission(permissionList).then((data: Array<abilityAccessCtrl.PermissionStatusInfo>) => {
  console.info('queryStatusByPermission success, data: ' + JSON.stringify(data));
}).catch((err: BusinessError): void => {
  console.error(`queryStatusByPermission fail, code: ${err.code}, message: ${err.message}`);
});

```

## queryStatusByTokenID

```TypeScript
queryStatusByTokenID(tokenIDList: Array<number>): Promise<Array<PermissionStatusInfo>>
```

根据应用tokenID列表查询其所有的权限状态。使用Promise异步回调。当查询的数据结果的大小超过50000条时，接口会直接返回12100015错误码。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.GET_SENSITIVE_PERMISSIONS

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AtManager-queryStatusByTokenID(tokenIDList: Array<int>): Promise<Array<PermissionStatusInfo>>--><!--Device-AtManager-queryStatusByTokenID(tokenIDList: Array<int>): Promise<Array<PermissionStatusInfo>>-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tokenIDList | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<number> | 是 | 待查询的应用tokenID列表。应用的身份标识可通过应用BundleInfo中的ApplicationInfo中的[accessTokenId](arkts-ability-applicationinfo-i.md#accesstokenid)字段获取。传入无效值时返回错误码12100001。<br>最大长度为1024且不能为空。取值约束：列表中的tokenID必须为大于0的整数。<br>BundleInfo获取可参考：[bundleManager.getBundleInfoSync](arkts-ability-bundlemanager-getbundleinfosync-f.md#getbundleinfosync-1)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Array<PermissionStatusInfo>> | Promise对象，返回查询到的权限状态信息列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. Interface caller does not have permission "ohos.permission.GET_SENSITIVE_PERMISSIONS". |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. Interface caller is not a system application. |
| [12100001](../errorcode-access-token.md#12100001-入参错误) | Invalid parameter. The tokenIDList is empty or exceeds the size limit. |
| [12100002](../errorcode-access-token.md#12100002-tokenid不存在) | The specified tokenID does not exist. |
| [12100007](../errorcode-access-token.md#12100007-系统服务工作异常) | Service exception. |
| [12100015](../errorcode-access-token.md#12100015-查询的数据超过上限) | The queried data exceeds the upper limit. |

**示例：**

```TypeScript
import { abilityAccessCtrl } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let atManager: abilityAccessCtrl.AtManager = abilityAccessCtrl.createAtManager();
let tokenID: number = 0; // 获取tokenID的方式可参考AtManager章节的描述。
let tokenIDList: Array<number> = [tokenID];
atManager.queryStatusByTokenID(tokenIDList).then((data: Array<abilityAccessCtrl.PermissionStatusInfo>) => {
  console.info('queryStatusByTokenID success, data: ' + JSON.stringify(data));
}).catch((err: BusinessError): void => {
  console.error(`queryStatusByTokenID fail, code: ${err.code}, message: ${err.message}`);
});

```

## requestPermissionOnApplicationSetting

```TypeScript
requestPermissionOnApplicationSetting(tokenID: number): Promise<void>
```

拉起应用权限设置页面。使用Promise异步回调。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AtManager-requestPermissionOnApplicationSetting(tokenID: int): Promise<void>--><!--Device-AtManager-requestPermissionOnApplicationSetting(tokenID: int): Promise<void>-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tokenID | number | 是 | 目标应用的身份标识。可通过应用BundleInfo中的ApplicationInfo中的[accessTokenId](arkts-ability-applicationinfo-i.md#accesstokenid)字段获取。传入无效值时返回错误码12100001。<br>取值限定为整数。取值约束：该参数必须为大于0的整数。<br>BundleInfo获取可参考：[bundleManager.getBundleInfoSync](arkts-ability-bundlemanager-getbundleinfosync-f.md#getbundleinfosync-1)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. Interface caller is not a system app. |
| [12100002](../errorcode-access-token.md#12100002-tokenid不存在) | The specified tokenID does not exist. |
| [12100007](../errorcode-access-token.md#12100007-系统服务工作异常) | Service exception. |

**示例：**

```TypeScript
import { abilityAccessCtrl } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let atManager: abilityAccessCtrl.AtManager = abilityAccessCtrl.createAtManager();
let tokenID: number = 0; // 获取tokenID的方式可参考AtManager章节的描述。
atManager.requestPermissionOnApplicationSetting(tokenID).then(() => {
  console.info('requestPermissionOnApplicationSetting success');
}).catch((err: BusinessError): void => {
  console.error(`requestPermissionOnApplicationSetting fail, code: ${err.code}, message: ${err.message}`);
});

```

## requestPermissionsFromUserWithWindowId

```TypeScript
requestPermissionsFromUserWithWindowId(
        context: Context,
        windowId: number,
        permissionList: Array<Permissions>) : Promise<PermissionRequestResult>
```

基于窗口ID弹出弹窗请求用户授权，调用成功后，返回本次权限申请结果对象，开发者可根据权限申请结果继续窗口级授权后的业务流程。使用Promise异步回调。

适用于系统应用需要将权限申请弹窗明确附着到指定窗口的场景。

如果用户拒绝授权，将无法再次拉起弹窗，可通过以下方式重新获取权限：1. 在系统设置界面中手动授权；2. 调用[requestPermissionOnSetting](arkts-ability-abilityaccessctrl-atmanager-i.md#requestpermissiononsetting-1)，拉起权限设置弹窗引导用户授权。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AtManager-requestPermissionsFromUserWithWindowId(
        context: Context,
        windowId: int,
        permissionList: Array<Permissions>) : Promise<PermissionRequestResult>--><!--Device-AtManager-requestPermissionsFromUserWithWindowId(
        context: Context,
        windowId: int,
        permissionList: Array<Permissions>) : Promise<PermissionRequestResult>-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-arkui/arkts-components/arkts-arkui-context-t.md) | 是 | 请求权限的UIAbility/UIExtensionAbility的Context。若传入其他应用、无效页面或非Stage模型的Context，接口可能报错或无法拉起弹窗。 |
| windowId | number | 是 | 应用窗口的ID。可通过[window.findWindow](../../apis-arkui/arkts-apis/arkts-arkui-window-findwindow-f.md#findwindow-1)(窗口名).[getWindowProperties()](../../apis-arkui/arkts-apis/arkts-arkui-window-window-i.md#getwindowproperties-1).id获取。该参数必须对应当前有效窗口，传入已销毁、不可见或无效窗口ID时将返回12100001。<br>取值限定为整数。 |
| permissionList | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<Permissions> | 是 | 权限名列表。建议仅传入当前窗口场景下真正需要的敏感权限。<br>最小长度为1。取值约束：权限名长度不能超过256个字符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<PermissionRequestResult> | Promise对象，返回本次权限申请结果，包含权限数组、授权结果、是否展示弹窗以及失败原因等信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [12100001](../errorcode-access-token.md#12100001-入参错误) | Invalid parameter. windowId is invalid. |
| [12100009](../errorcode-access-token.md#12100009-服务内部错误) | Common inner error. An error occurs when creating the popup window or obtaining the user operation result. |

**示例：**

关于向用户申请授权的完整流程及示例，请参见[向用户申请授权](../../security/AccessToken/request-user-authorization.md)。

```TypeScript
import { abilityAccessCtrl, Context, PermissionRequestResult } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

let atManager: abilityAccessCtrl.AtManager = abilityAccessCtrl.createAtManager();
// 请在组件内获取context
let context: Context = this.getUIContext().getHostContext() as Context;
let windowId = 0; // 获取方式 let windowId = window.findWindow(窗口名).getWindowProperties().id;
// 基于窗口ID请求用户授权指定权限
atManager.requestPermissionsFromUserWithWindowId(context, windowId, ['ohos.permission.CAMERA']).then((data: PermissionRequestResult) => {
  console.info(`requestPermissionsFromUserWithWindowId success, result: ${data}`);
  console.info('requestPermissionsFromUserWithWindowId data permissions:' + data.permissions);
  console.info('requestPermissionsFromUserWithWindowId data authResults:' + data.authResults);
  console.info('requestPermissionsFromUserWithWindowId data dialogShownResults:' + data.dialogShownResults);
  console.info('requestPermissionsFromUserWithWindowId data errorReasons:' + data.errorReasons);
}).catch((err: BusinessError): void => {
  console.error(`requestPermissionsFromUserWithWindowId fail, code: ${err.code}, message: ${err.message}`);
});

```

## revokePermission

```TypeScript
revokePermission(
      tokenID: number,
      permissionName: Permissions,
      permissionFlags: number,
      killProcess?: boolean): Promise<void>
```

撤销应用权限。调用成功后，应用失去该权限，无法访问相应的受保护资源。根据killProcess参数的值决定是否终止应用进程。使用Promise异步回调。

当killProcess参数为true且权限状态从“已授权”变为“未授权”时，应用进程会被终止。

**起始版本：** 21

**需要权限：** ohos.permission.REVOKE_SENSITIVE_PERMISSIONS

<!--Device-AtManager-revokePermission(
      tokenID: int,
      permissionName: Permissions,
      permissionFlags: int,
      killProcess?: boolean): Promise<void>--><!--Device-AtManager-revokePermission(
      tokenID: int,
      permissionName: Permissions,
      permissionFlags: int,
      killProcess?: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tokenID | number | 是 | 目标应用的身份标识。可通过应用BundleInfo中的ApplicationInfo中的[accessTokenId](arkts-ability-applicationinfo-i.md#accesstokenid)字段获取。传入无效值时返回错误码12100001。<br>取值限定为整数。取值约束：该参数必须为大于0的整数。<br>BundleInfo获取可参考：[bundleManager.getBundleInfoSync](arkts-ability-bundlemanager-getbundleinfosync-f.md#getbundleinfosync-1)。 |
| permissionName | Permissions | 是 | 被撤销的权限名称。传入无效值时返回错误码12100001。<br>取值约束：权限名长度不能超过256个字符。 |
| permissionFlags | number | 是 | 授权选项。<br>取值限定为整数。<br>- 1表示当次用户若选择禁止该权限，下次权限弹窗仍可以弹出申请用户授权。<br>- 2表示当次用户若选择禁止该权限，下次不会再弹出权限弹窗，用户需要在系统设置的权限管理中进行授权。<br>- 64表示当次用户若选择仅本次允许，权限仅本次授权。应用切换后台状态或退出后取消授权。 |
| killProcess | boolean | 否 | 是否终止应用进程。<br>- true表示终止应用进程。<br>- false表示不终止应用进程。<br>- 默认值为true。<br><br>**起始版本：** 26.0.0 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. The interface invoker does not have permission"ohos.permission.REVOKE_SENSITIVE_PERMISSIONS". |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not a system application. The interface invoker is not a system application. |
| [12100001](../errorcode-access-token.md#12100001-入参错误) | Invalid parameter. The token ID is 0, the permission name exceeds 256 characters or is not declared in the module.json file,or the value of flags is invalid. |
| [12100002](../errorcode-access-token.md#12100002-tokenid不存在) | The specified tokenID does not exist. |
| [12100003](../errorcode-access-token.md#12100003-权限名不存在) | The specified permission does not exist. |
| [12100006](../errorcode-access-token.md#12100006-指定的应用不支持被授予或被取消授予指定的权限) | The specified permission is not allowed to be revoked from the application specified by the tokenID. Either the application is a sandbox or the tokenID is from a remote device. |
| [12100007](../errorcode-access-token.md#12100007-系统服务工作异常) | Service exception. |
| [12100014](../errorcode-access-token.md#12100014-非预期的权限) | Unexpected permission. The specified permission is not a user_grant or manual_settings permission. |

**示例：**

```TypeScript
import { abilityAccessCtrl } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let atManager: abilityAccessCtrl.AtManager = abilityAccessCtrl.createAtManager();
let tokenID: number = 0; // 获取tokenID的方式可参考AtManager章节的描述。
let permissionFlags: number = 2;
// 不终止应用进程
atManager.revokePermission(tokenID, 'ohos.permission.READ_AUDIO', permissionFlags, false).then(() => {
  console.info('revokePermission success, process not killed');
}).catch((err: BusinessError): void => {
  console.error(`revokePermission fail, code: ${err.code}, message: ${err.message}`);
});
// 终止应用进程（默认行为）
atManager.revokePermission(tokenID, 'ohos.permission.READ_AUDIO', permissionFlags).then(() => {
  console.info('revokePermission success');
}).catch((err: BusinessError): void => {
  console.error(`revokePermission fail, code: ${err.code}, message: ${err.message}`);
});

```

## revokeUserGrantedPermission

```TypeScript
revokeUserGrantedPermission(tokenID: number, permissionName: Permissions, permissionFlags: number): Promise<void>
```

撤销应用user_grant权限。调用成功后，应用失去该user_grant权限，无法访问相应的受保护资源。使用Promise异步回调。

本接口仅支持撤销user_grant类型的权限，且不支持控制是否终止应用进程。若需要撤销user_grant或manual_settings类型权限，或需要控制撤销权限后是否终止应用进程，建议使用[revokePermission](arkts-ability-abilityaccessctrl-atmanager-i-sys.md#revokepermission-1)。

当权限状态从“已授权”变为“未授权”时，应用进程会被终止。

**起始版本：** 8

**需要权限：** ohos.permission.REVOKE_SENSITIVE_PERMISSIONS

<!--Device-AtManager-revokeUserGrantedPermission(tokenID: int, permissionName: Permissions, permissionFlags: int): Promise<void>--><!--Device-AtManager-revokeUserGrantedPermission(tokenID: int, permissionName: Permissions, permissionFlags: int): Promise<void>-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tokenID | number | 是 | 目标应用的身份标识。可通过应用BundleInfo中的ApplicationInfo中的[accessTokenId](arkts-ability-applicationinfo-i.md#accesstokenid)字段获取。传入无效值时返回错误码12100001。<br>取值限定为整数。取值约束：该参数必须为大于0的整数。<br>BundleInfo获取可参考：[bundleManager.getBundleInfoSync](arkts-ability-bundlemanager-getbundleinfosync-f.md#getbundleinfosync-1)。 |
| permissionName | Permissions | 是 | 被撤销的权限名称。传入无效值时返回错误码12100001。<br>取值约束：权限名长度不能超过256个字符。 |
| permissionFlags | number | 是 | 授权选项。<br>取值限定为整数。<br>- 1表示当次用户若选择禁止该权限，下次权限弹窗仍可以弹出申请用户授权。<br>- 2表示当次用户若选择禁止该权限，下次不会再弹出权限弹窗，用户需要在系统设置的权限管理中进行授权。<br>- 64表示当次用户若选择仅本次允许，权限仅本次授权。应用切换后台状态或退出后取消授权。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. Interface caller does not have permission"ohos.permission.REVOKE_SENSITIVE_PERMISSIONS". |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. Interface caller is not a system app. |
| [12100001](../errorcode-access-token.md#12100001-入参错误) | Invalid parameter. The tokenID is 0, the permissionName exceeds 256characters or is not declared in the module.json file, or the flags value is invalid. |
| [12100002](../errorcode-access-token.md#12100002-tokenid不存在) | The specified tokenID does not exist. |
| [12100003](../errorcode-access-token.md#12100003-权限名不存在) | The specified permission does not exist or is not a user_grant permission. |
| [12100006](../errorcode-access-token.md#12100006-指定的应用不支持被授予或被取消授予指定的权限) | The application specified by the tokenID is not allowed to be revoked with the specified permission. Either the application is a sandbox or the tokenID is from a remote device. |
| [12100007](../errorcode-access-token.md#12100007-系统服务工作异常) | Service exception. |

**示例：**

```TypeScript
import { abilityAccessCtrl } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let atManager: abilityAccessCtrl.AtManager = abilityAccessCtrl.createAtManager();
let tokenID: number = 0; // 获取tokenID的方式可参考AtManager章节的描述。
let permissionFlags: number = 1;
atManager.revokeUserGrantedPermission(tokenID, 'ohos.permission.READ_AUDIO', permissionFlags).then(() => {
  console.info('revokeUserGrantedPermission success');
}).catch((err: BusinessError): void => {
  console.error(`revokeUserGrantedPermission fail, code: ${err.code}, message: ${err.message}`);
});

```

## revokeUserGrantedPermission

```TypeScript
revokeUserGrantedPermission(
        tokenID: number,
        permissionName: Permissions,
        permissionFlags: number,
        callback: AsyncCallback<void>
    ): void
```

撤销应用user_grant权限。使用callback异步回调。调用成功后，应用失去该user_grant权限，无法访问相应的受保护资源。

**起始版本：** 8

**需要权限：** ohos.permission.REVOKE_SENSITIVE_PERMISSIONS

<!--Device-AtManager-revokeUserGrantedPermission(
        tokenID: int,
        permissionName: Permissions,
        permissionFlags: int,
        callback: AsyncCallback<void>
    ): void--><!--Device-AtManager-revokeUserGrantedPermission(
        tokenID: int,
        permissionName: Permissions,
        permissionFlags: int,
        callback: AsyncCallback<void>
    ): void-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tokenID | number | 是 | 目标应用的身份标识。可通过应用BundleInfo中的ApplicationInfo中的[accessTokenId](arkts-ability-applicationinfo-i.md#accesstokenid)字段获取。传入无效值时返回错误码12100001。<br>取值限定为整数。取值约束：该参数必须为大于0的整数。<br>BundleInfo获取可参考：[bundleManager.getBundleInfoSync](arkts-ability-bundlemanager-getbundleinfosync-f.md#getbundleinfosync-1)。 |
| permissionName | Permissions | 是 | 被撤销的权限名称。传入无效值时返回错误码12100001。<br>取值约束：权限名长度不能超过256个字符。 |
| permissionFlags | number | 是 | 授权选项。<br>取值限定为整数。<br>- 1表示当次用户若选择禁止该权限，下次权限弹窗仍可以弹出申请用户授权。<br>- 2表示当次用户若选择禁止该权限，下次不会再弹出权限弹窗，用户需要在系统设置的权限管理中进行授权。<br>- 64表示当次用户若选择仅本次允许，权限仅本次授权。应用切换后台状态或退出后取消授权。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。当撤销权限成功时，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. Interface caller does not have permission"ohos.permission.REVOKE_SENSITIVE_PERMISSIONS". |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. Interface caller is not a system app. |
| [12100001](../errorcode-access-token.md#12100001-入参错误) | Invalid parameter. The tokenID is 0, the permissionName exceeds 256characters or is not declared in the module.json file, or the flags value is invalid. |
| [12100002](../errorcode-access-token.md#12100002-tokenid不存在) | The specified tokenID does not exist. |
| [12100003](../errorcode-access-token.md#12100003-权限名不存在) | The specified permission does not exist or is not a user_grant permission. |
| [12100006](../errorcode-access-token.md#12100006-指定的应用不支持被授予或被取消授予指定的权限) | The application specified by the tokenID is not allowed to be revoked with the specified permission. Either the application is a sandbox or the tokenID is from a remote device. |
| [12100007](../errorcode-access-token.md#12100007-系统服务工作异常) | Service exception. |

**示例：**

```TypeScript
import { abilityAccessCtrl } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let atManager: abilityAccessCtrl.AtManager = abilityAccessCtrl.createAtManager();
let tokenID: number = 0; // 获取tokenID的方式可参考AtManager章节的描述。
let permissionFlags: number = 1;
atManager.revokeUserGrantedPermission(tokenID, 'ohos.permission.READ_AUDIO', permissionFlags, (err: BusinessError, data: void) => {
  if (err) {
    console.error(`revokeUserGrantedPermission fail, code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('revokeUserGrantedPermission success');
  }
});

```

## setPermissionRequestToggleStatus

```TypeScript
setPermissionRequestToggleStatus(permissionName: Permissions, status: PermissionRequestToggleStatus): Promise<void>
```

设置当前用户指定权限的弹窗开关状态。调用成功后，该权限的弹窗开关状态将被设置为指定值。当状态为CLOSED时，应用请求该权限时不会弹出权限弹窗；当状态为OPEN时，应用请求该权限时会正常弹出权限弹窗。使用Promise异步回调。

**起始版本：** 12

**需要权限：** ohos.permission.DISABLE_PERMISSION_DIALOG

<!--Device-AtManager-setPermissionRequestToggleStatus(permissionName: Permissions, status: PermissionRequestToggleStatus): Promise<void>--><!--Device-AtManager-setPermissionRequestToggleStatus(permissionName: Permissions, status: PermissionRequestToggleStatus): Promise<void>-End-->

**系统能力：** SystemCapability.Security.AccessToken

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| permissionName | Permissions | 是 | 待设置弹窗开关状态的权限名称。传入无效值时返回错误码12100001。<br>取值约束：权限名长度不能超过256个字符。 |
| status | [PermissionRequestToggleStatus](arkts-ability-abilityaccessctrl-permissionrequesttogglestatus-e-sys.md) | 是 | 指定权限的弹窗开关状态值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. Interface caller does not have permission specified below. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. Interface caller is not a system app. |
| [12100001](../errorcode-access-token.md#12100001-入参错误) | Invalid parameter. The permissionName exceeds 256 characters, the specified permission is not a user_grant permission, or the status value is invalid. |
| [12100003](../errorcode-access-token.md#12100003-权限名不存在) | The specified permission does not exist. |
| [12100007](../errorcode-access-token.md#12100007-系统服务工作异常) | Service exception. |
| [12100009](../errorcode-access-token.md#12100009-服务内部错误) | Common inner error. A database error occurs. |

**示例：**

```TypeScript
import { abilityAccessCtrl, Permissions } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let atManager: abilityAccessCtrl.AtManager = abilityAccessCtrl.createAtManager();
let permission: Permissions = 'ohos.permission.CAMERA';

atManager.setPermissionRequestToggleStatus(permission, abilityAccessCtrl.PermissionRequestToggleStatus.CLOSED).then(() => {
  console.info('setPermissionRequestToggleStatus: set closed successful');
}).catch((err: BusinessError): void => {
  console.error(`setPermissionRequestToggleStatus fail, code: ${err.code}, message: ${err.message}`);
});

```

