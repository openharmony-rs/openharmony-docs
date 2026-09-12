# @ohos.abilityToolAccessCtrl (Tool Access Control) (System API)

<!--Kit: Ability Kit-->
<!--Subsystem: Security-->
<!--Owner: @gcw_3MIoLA9y-->
<!--Designer: @wkr321_ent-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=fd2c51ad9f9cfbb14956dbd56f60235b5bdc1444 translatedAt=2026-09-03T09:32:36.363Z pushedAt=2026-09-05T10:47:30.183Z -->

The Tool Access Control module provides permission management capabilities for tools (CLI commands and API interfaces), including permission query, user authorization, and remote authorization. Permission query is used to check the permission status of tools, user authorization is used to grant tool permissions based on user decisions, and remote authorization implements cross-device permission management through the ticket mechanism. The module supports the ticket verification mechanism and cross-device collaborative authorization, which can improve permission management security and simplify the authorization process.

Use the APIs of this module when you need to query the permission status of CLI commands or API interfaces, authorize tool permissions, or manage authorization of remote devices.

**Since:** 26.0.0

> **NOTE**
>
> The APIs of this module are system APIs.

## Modules to Import

```ts
import { abilityToolAccessCtrl } from '@kit.AbilityKit';
```

## abilityToolAccessCtrl.requestToolPermissions

requestToolPermissions(permissionQuery: PermissionQuery): Promise&lt;PermissionQueryResult&gt;

Queries tool permissions based on the specified operation. Checks the permission status of the CLI command or API specified in the [operationInfo](#operationinfo) property of the input parameter [permissionQuery](#permissionquery), and returns the permission status, authorization status, and whether a user dialog box is required for each operation. When [permissionQuery.needTicket](#permissionquery) is set to true, a ticket for remote authorization is generated. This API uses a promise to return the result.

**Since:** 26.0.0

**System API**: This is a system API.

**Required permissions:** ohos.permission.QUERY_TOOL_PERMISSIONS

**System capability**: SystemCapability.Security.Asset

**Parameters**

| Name | Type | Required | Description |
| -------- | -------- | -------- | -------- |
| permissionQuery | [PermissionQuery](#permissionquery) | Yes | Permission query information, including the operation information list, whether to generate a ticket, remote device information, and so on. |

**Return value**

| Type | Description |
| -------- | -------- |
| Promise&lt;[PermissionQueryResult](#permissionqueryresult)&gt; | Promise object. Returns the permission query result, including whether a dialog box is required, the permission status information, and the ticket information. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Tool Access Control Error Codes](errorcode-abilityToolAccessCtrl-sys.md).


| ID | Error Message |
| -------- | -------- |
| 201 | Permission denial. The interface caller does not have permission "ohos.permission.QUERY_TOOL_PERMISSIONS". |
| 202 | The caller is not a system application. |
| 24010000 | Invalid parameter. OperationType and operationInfo do not match, specified callerTokenId does not exist, ticketExpireTime exceeds 24h, etc. |
| 24010001 | Service is abnormal. Possible cause: IPC failed. |
| 24010002 | Common internal error. Possible cause: dependent service unavailable, resource access failed, etc. |
| 24010003 | The account is not logged in, network is unavailable, timeout, etc. |
| 24010006 | The requested operation is not allowed to be executed while the device is locked. |

**Example**

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

Grants tool permissions based on the user authorization result. Grants permissions to a tool (CLI command or API) based on the user's authorization decision. After the authorization succeeds, generates a ticket that can be used for permission verification. This API uses a promise to return the result.

**Since:** 26.0.0

**System API**: This is a system API.

**Required permissions:** ohos.permission.MANAGE_TOOL_RUNTIME_PERMISSIONS

**System capability**: SystemCapability.Security.Asset

**Parameters**

| Name | Type | Required | Description |
| -------- | -------- | -------- | -------- |
| userAuthResult | [UserAuthResult](#userauthresult)[] | Yes | List of user authorization results, including permission information and permission query information. |

**Return value**

| Type | Description |
| -------- | -------- |
| Promise&lt;[TicketInfo](#ticketinfo)[]&gt; | Promise object. List of ticket information generated after successful authorization. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Tool Access Control Error Codes](errorcode-abilityToolAccessCtrl-sys.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permission denial. The interface caller does not have permission "ohos.permission.MANAGE_TOOL_RUNTIME_PERMISSIONS". |
| 202 | The caller is not a system application. |
| 24010000 | Invalid parameter. OperationType and operationInfo do not match, specified callerTokenId does not exist, ticketExpireTime exceeds 24h, etc. |
| 24010001 | Service is abnormal. Possible cause: IPC failed. |
| 24010002 | Common internal error. Possible cause: dependent service unavailable, resource access failed, etc. |
| 24010003 | The account is not logged in, network is unavailable, timeout, etc. |
| 24010004 | Invalid permission. A permission in permissionInfo does not exist. |
| 24010005 | Grant permission failed. The application specified by the tokenID is not allowed to be granted with the specified permission, the specified permission cannot be granted by user, etc. |


**Example**

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

Generates a remote authorization result package on the controller device based on the user remote authorization result. The generated package can be sent to the controlled device to perform permission authorization after integrity verification. This API uses a promise to return the result asynchronously.

**Since:** 26.1.0

**System API**: This is a system API.

**Required permissions:** ohos.permission.QUERY_TOOL_PERMISSIONS

**System capability**: SystemCapability.Security.Asset

**Parameters**

| Name | Type | Required | Description |
| -------- | -------- | -------- | -------- |
| remoteUserAuthResult | [RemoteUserAuthResults](#remoteuserauthresults)[] | Yes | List of user remote authorization results, including the authorization result and permission information. |

**Return value**

| Type | Description |
| -------- | -------- |
| Promise&lt;[RemoteAuthPackage](#remoteauthpackage)[]&gt; | Promise used to return the list of remote authorization result packages. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Tool Access Control Error Codes](errorcode-abilityToolAccessCtrl-sys.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permission denial. The interface caller does not have permission "ohos.permission.QUERY_TOOL_PERMISSIONS". |
| 202 | The caller is not a system application. |
| 24010000 | Invalid parameter. OperationType and operationInfo do not match, specified callerTokenId does not exist, etc. |
| 24010001 | Service is abnormal. Possible cause: IPC failed. |
| 24010002 | Common internal error. Possible cause: dependent service unavailable, resource access failed, etc. |
| 24010003 | The account is not logged in, network is unavailable, timeout, etc. |

**Example**

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

Generates a remote authorization request package on the controlled device based on the permission query list. The generated package can be sent to the controller device, where integrity verification is completed before user authorization confirmation is initiated. This API uses a promise to return the result asynchronously.

**Since:** 26.1.0

**System API**: This is a system API.

**Required permissions:** ohos.permission.QUERY_TOOL_PERMISSIONS

**System capability**: SystemCapability.Security.Asset

**Parameters**

| Name | Type | Required | Description |
| -------- | -------- | -------- | -------- |
| permissionQuery | [PermissionQuery](#permissionquery)[] | Yes | Permission query list, which contains CLI and API operation information, remote authorization interaction information, and so on. |

**Return value**

| Type | Description |
| -------- | -------- |
| Promise&lt;[RemoteAuthPackage](#remoteauthpackage)[]&gt; | Promise object used to return the list of remote authorization request packages. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Tool Access Control Error Codes](errorcode-abilityToolAccessCtrl-sys.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permission denial. The interface caller does not have permission "ohos.permission.QUERY_TOOL_PERMISSIONS". |
| 202 | The caller is not a system application. |
| 24010000 | Invalid parameter. Permission exceeds 256 characters, specified tokenId is invalid, etc. |
| 24010001 | Service is abnormal. Possible cause: IPC failed. |
| 24010002 | Common internal error. Possible cause: dependent service unavailable, resource access failed, etc. |
| 24010003 | The account is not logged in, network is unavailable, timeout, etc. |

**Example**

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

Verifies the remote authorization result package sent by the controller device, and checks the message credential and remote device information to ensure that the authorization result is valid. This API uses a promise to return the result asynchronously.

**Since:** 26.1.0

**System API**: This is a system API.

**Required permissions:** ohos.permission.QUERY_TOOL_PERMISSIONS

**System capability**: SystemCapability.Security.Asset

**Parameters**

| Name | Type | Required | Description |
| -------- | -------- | -------- | -------- |
| ticketInfo | [RemoteAuthPackage](#remoteauthpackage)[] | Yes | List of remote authorization packages, including the remote message, anti-replay challenge value, and message integrity credential. |
| remoteInfo | [RemoteInfo](#remoteinfo) | Yes | Remote device information, including the device role, device ID, and Huawei account ID. |

**Return value**

| Type | Description |
| -------- | -------- |
| Promise&lt;boolean[]&gt; | Promise object. The value **true** indicates that the verification is passed; the value **false** indicates that the verification fails. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Tool Access Control Error Codes](errorcode-abilityToolAccessCtrl-sys.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permission denial. The interface caller does not have permission "ohos.permission.QUERY_TOOL_PERMISSIONS". |
| 202 | The caller is not a system application. |
| 24010000 | Invalid parameter. Format of ticketInfo or remoteInfo is invalid. |
| 24010001 | Service is abnormal. Possible cause: IPC failed. |
| 24010002 | Common internal error. Possible cause: dependent service unavailable, resource access failed, etc. |
| 24010003 | The account is not logged in, network is unavailable, timeout, etc. |

**Example**

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

Verifies the authorization package sent by the controlled device and checks the message credentials to ensure that the authorization request is valid. This API uses a promise to return the result asynchronously.

**Since:** 26.1.0

**System API**: This is a system API.

**Required permissions:** ohos.permission.QUERY_TOOL_PERMISSIONS

**System capability**: SystemCapability.Security.Asset

**Parameters**

| Name | Type | Required | Description |
| -------- | -------- | -------- | -------- |
| ticketInfo | [RemoteAuthPackage](#remoteauthpackage)[] | Yes | List of remote authorization packages, including the remote message, anti-replay challenge value, and message integrity credential. |

**Return value**

| Type | Description |
| -------- | -------- |
| Promise&lt;boolean[]&gt; | Promise object. The value **true** indicates that the verification is successful, and **false** indicates that the verification fails. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Tool Access Control Error Codes](errorcode-abilityToolAccessCtrl-sys.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permission denial. The interface caller does not have permission "ohos.permission.QUERY_TOOL_PERMISSIONS". |
| 202 | The caller is not a system application. |
| 24010000 | Invalid parameter. Format of ticketInfo is invalid. |
| 24010001 | Service is abnormal. Possible cause: IPC failed. |
| 24010002 | Common internal error. Possible cause: dependent service unavailable, resource access failed, etc. |
| 24010003 | The account is not logged in, network is unavailable, timeout, etc. |

**Example**

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

Queries the enable status of the remote authorization switch. When enabled, the device can initiate remote authorization to a remote device; when disabled, remote authorization is not allowed. This API uses a promise to return the result asynchronously.

**Since:** 26.1.0

**System API**: This is a system API.

**Required permissions:** ohos.permission.QUERY_TOOL_PERMISSIONS

**System capability**: SystemCapability.Security.Asset

**Return value**

| Type | Description |
| -------- | -------- |
| Promise&lt;[RemoteGrantStatus](#remotegrantstatus)&gt; | Promise object used to return the remote authorization switch status. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Tool Access Control Error Codes](errorcode-abilityToolAccessCtrl-sys.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permission denial. The interface caller does not have permission "ohos.permission.QUERY_TOOL_PERMISSIONS". |
| 202 | The caller is not a system application. |
| 24010001 | Service is abnormal. Possible cause: IPC failed. |
| 24010002 | Common internal error. Possible cause: dependent service unavailable, resource access failed, etc. |

**Example**

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

Updates the remote authorization status to enable or disable the remote authorization switch. When enabled, the device can initiate remote authorization to a remote device; when disabled, remote authorization is not allowed. This API uses a promise to return the result.

**Since:** 26.1.0

**System API**: This is a system API.

**Required permissions:** ohos.permission.MANAGE_TOOL_RUNTIME_PERMISSIONS

**System capability**: SystemCapability.Security.Asset

**Parameters**

| Name | Type | Required | Description |
| -------- | -------- | -------- | -------- |
| remoteGrantStatus | [RemoteGrantStatus](#remotegrantstatus) | Yes | Remote authorization status to set. |

**Return value**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Tool Access Control Error Codes](errorcode-abilityToolAccessCtrl-sys.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permission denial. The interface caller does not have permission "ohos.permission.MANAGE_TOOL_RUNTIME_PERMISSIONS". |
| 202 | The caller is not a system application. |
| 24010000 | Invalid parameter. RemoteGrantStatus is invalid. |
| 24010001 | Service is abnormal. Possible cause: IPC failed. |
| 24010002 | Common internal error. Possible cause: dependent service unavailable, resource access failed, etc. |

**Example**

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

Represents the parameters for remote control interaction.

**Since:** 26.1.0

**System API**: This is a system API.

**System capability**: SystemCapability.Security.Asset

| Name | Type | Read-only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| challenge | string | No | Yes | Anti-replay challenge used to prevent replay attacks. A valid challenge is obtained from the [generateControlledDevicePackage](#abilitytoolaccessctrlgeneratecontrolleddevicepackage) API.<br>Default value: empty string. |
| remoteControlTicket | string | No | Yes | Remote control ticket of the trusted device, used for identity verification of trusted devices under the same account in remote control scenarios.<br>Default value: empty string. |
| controlledDeviceName | string | No | Yes | Device name of the controlled device.<br>Default value: empty string. |
| controllerDeviceName | string | No | Yes | Device name of the controller device.<br>Default value: empty string. |
| signVerifyMsg | string | No | Yes | Additional information required for signature verification, such as the caller package name and module name.<br>Default value: empty string. |

## CliCmdInfo

Represents the CLI (Command Line Interface) command information.

**Since:** 26.0.0

**System API**: This is a system API.

**System capability**: SystemCapability.Security.Asset

| Name | Type | Read-only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| cliCmdName | string | No | No | CLI command name, used to specify the CLI command to be queried or authorized. A CLI command name supported by the system must be passed in, for example, 'ohos-displayManager'. |
| subCliCmdName | string | No | No | CLI subcommand name, used to specify the CLI subcommand to be queried or authorized. A subcommand name supported by the specified CLI command must be passed in, for example, 'set-brightness'. |

## PermissionQuery

Represents the permission query information.

**Since:** 26.0.0

**System API**: This is a system API.

**System capability**: SystemCapability.Security.Asset

| Name | Type | Read-only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| operationInfo | [OperationInfo](#operationinfo)[] | No | No | List of operation information, specifying the CLI commands or APIs to be queried. |
| needTicket | boolean | No | Yes | Whether to generate a ticket for local or remote authorization. The value **true** means to generate a ticket, and **false** means the opposite. When set to **true**, the ticket information is returned only if the query result passes.<br>Default value: **false** |
| ticketExpireTimeMs | number | No | Yes | Expiration time of the ticket, in milliseconds. This parameter must be used together with **needTicket** and takes effect only when **needTicket** is **true**. Value range for the regular authorization scenario: 1 to 60000 (60 seconds). Value range for the long-time remote authorization scenario: 1 to 86400000 (24 hours). If the value exceeds the maximum, error code 24010000 is returned.<br>Default value: **10000** |
| remoteInfo | [RemoteInfo](#remoteinfo) | No | Yes | Remote device information. Used in the remote authorization scenario, including the device role, device ID, Huawei account ID, and other remote device related information.<br>**Since:** 26.1.0 |
| callerTokenId | number | No | Yes | Token ID of the caller process. When querying or authorizing for another process, specify the token ID of the target process.<br>If this parameter is not passed in, the token ID of the caller process is obtained by default. |
| domainId | string | No | Yes | Domain ID.<br>If this parameter is not passed in, the current domain ID of the caller is obtained by default. |

## RemoteInfo

Describes the remote device information.

**Since:** 26.1.0

**System API**: This is a system API.

**System capability**: SystemCapability.Security.Asset

| Name | Type | Read-only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| role | [Role](#role) | No | No | Device role, indicating whether the device is a controller or a controlled device. |
| remoteId | string | No | No | Remote device ID, used to uniquely identify the remote device. |
| domainId | string | No | No | Huawei account ID, used to identify the Huawei account that the device is logged in with. |
| remoteControlParams | [RemoteControlParams](#remotecontrolparams) | No | Yes | Interaction parameters in remote control, including the anti-replay challenge value, remote control credential, and other information. |

## OperationInfo

Describes the operation information.

**Since:** 26.0.0

**System API**: This is a system API.

**System capability**: SystemCapability.Security.Asset

| Name | Type | Read-only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| operationType | [OperationType](#operationtype) | No | No | Operation type, indicating whether the operation is a CLI command or an API. |
| info | [CliCmdInfo](#clicmdinfo) \| [Permissions](../../security/AccessToken/app-permissions.md) | No | No | Specific information about the operation. When operationType is CLI, info is CliCmdInfo; when operationType is API, info is the permission name. If the types of operationType and info do not match, a parameter error occurs. |

## PermissionInfo

Represents permission information.

**Since:** 26.0.0

**System API**: This is a system API.

**System capability**: SystemCapability.Security.Asset

| Name | Type | Read-only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| permission | string | No | No | Permission name. For valid permission names, see [Application Permission List](../../security/AccessToken/app-permissions.md). |
| permissionStatus | [PermissionStatus](js-apis-abilityAccessCtrl.md#permissionstatus20) | No | No | Permission status. |
| authStatusInfo | [AuthStatusInfo](#authstatusinfo) | No | Yes | Authorization status information.<br>This item is used as an output parameter. When PermissionInfo is used as an input parameter, this item does not require a value and will be ignored if passed in. The default value is undefined.|

## AuthStatusInfo

Represents the authorization status information.

**Since:** 26.0.0

**System API**: This is a system API.

**System capability**: SystemCapability.Security.Asset

| Name | Type | Read-only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| authStatus | [AuthStatus](#authstatus) | No | Yes | Authorization status. As an input parameter, this item does not require a value, and if passed in, it will be ignored. As an output parameter, this item returns the actual authorization status, which indicates the authorization result of the permission. |
| flag | number | No | Yes | Authorization flag, used to identify the attributes related to permission authorization (such as authorization type and authorization persistence).<br>As an input parameter, this item does not require a value, and if passed in, it will be ignored, with the default value 0. As an output parameter, this item returns the actual authorization flag.|

## PermissionQueryResult

Represents the permission query result.

**Since:** 26.0.0

**System API**: This is a system API.

**System capability**: SystemCapability.Security.Asset

| Name | Type | Readable | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| needDialog | boolean | No | No | Whether to display a dialog box. The value **true** means a dialog box is required to request user authorization, and **false** means the opposite. |
| permissionResults | [PermissionInfo](#permissioninfo)[] | No | No | List of permission status results. |
| ticket | [TicketInfo](#ticketinfo) | No | Yes | Ticket information.<br>When the input parameter [permissionQuery.needTicket](#permissionquery) is **true** and the query result passes, the ticket information is returned. |

## TicketInfo

Represents ticket information.

**Since:** 26.0.0

**System API**: This is a system API.

**System capability**: SystemCapability.Security.Asset

| Name | Type | Read-only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| message | string | No | No | Ticket message, used to convey authorization information, prompt information, and status description related to authorization. |
| challenge | string | No | No | Challenge value, used to verify the validity of the ticket. |
| ticket | string | No | No | Ticket string, used for permission verification. |

## RemoteAuthPackage

Indicates a remote authorization package.

**Since:** 26.1.0

**System API**: This is a system API.

**System capability**: SystemCapability.Security.Asset

| Name | Type | Readable | Writable | Description |
| -------- | -------- | -------- | -------- | -------- |
| remoteMessage | string | No | No | Remote message used to transfer remote authorization-related information. |
| challenge | string | No | No | Anti-replay challenge used to protect the security of the authorization package. |
| ticket | string | No | No | Integrity signature information of the remote message, used for remote permission verification. |

## UserAuthResult

Represents the user authorization result.

**Since:** 26.0.0

**System API**: This is a system API.

**System capability**: SystemCapability.Security.Asset

| Name | Type | Read-only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| permissionInfo | [PermissionInfo](#permissioninfo)[] | No | No | List of permission information, including permission names and authorization statuses. |
| permissionQuery | [PermissionQuery](#permissionquery) | No | No | Corresponding permission query information. |

## RemoteUserAuthResults

Represents the remote user authorization result.

**Since:** 26.1.0

**System API**: This is a system API.

**System capability**: SystemCapability.Security.Asset

| Name | Type | Readable | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| results | [RemoteUserAuthItem](#remoteuserauthitem)[] | No | No | List of authorization results, including permission names and authorization results. |
| permissionQuery | [PermissionQuery](#permissionquery) | No | No | Permission query information, used to associate authorization results with query requests. |

## RemoteUserAuthItem

Represents a remote user authorization item.

**Since:** 26.1.0

**System API**: This is a system API.

**System capability**: SystemCapability.Security.Asset

| Name | Type | Read-only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| permission | string | No | No | Permission name. For valid permission names, see [Application Permission List](../../security/AccessToken/app-permissions.md). |
| authResult | string | No | No | Authorization result, indicating the authorization status of the permission. Supported values include DENIED (not authorized by the user), GRANTED (authorized), NOT_DETERMINED (authorization not operated), INVALID (invalid permission), and RESTRICTED (restricted authorization). |

## AuthStatus

Enumerates the authorization statuses.

**Since:** 26.0.0

**System API**: This is a system API.

**System capability**: SystemCapability.Security.Asset

| Name | Value | Description |
| -------- | -------- | -------- |
| REQUIRE_AUTH | 0 | Authorization required. |
| FORBIDDEN | 1 | Authorization forbidden. |
| AUTHORIZED | 2 | Authorized. |
| RESTRICTED | 3 | Restricted. The permission is restricted by the system or policy. |
| REMOTE_RESTRICTED | 4 | Remotely restricted. The permission of the remote device is restricted. |


## Role

Enumerates the device roles.

**Since:** 26.1.0

**System API**: This is a system API.

**System capability**: SystemCapability.Security.Asset

| Name | Value | Description |
| -------- | -------- | -------- |
| CONTROLLER | 0x01 | Controller device, which initiates remote control. |
| CONTROLLED | 0x02 | Controlled device, which accepts remote control commands. |


## OperationType

Enumerates the operation types.

**Since:** 26.0.0

**System API**: This is a system API.

**System capability**: SystemCapability.Security.Asset

| Name | Value | Description |
| -------- | -------- | -------- |
| CLI | 0x01 | CLI command operation. |
| API | 0x02 | API operation. |

## RemoteGrantStatus

Enumerates the remote authorization statuses.

**Since:** 26.1.0

**System API**: This is a system API.

**System capability**: SystemCapability.Security.Asset

| Name | Value | Description |
| -------- | -------- | -------- |
| ENABLE | 0x01 | Enables remote authorization, allowing the device to grant permissions to remote devices. |
| DISABLE | 0x02 | Disables remote authorization, which does not allow remote authorization. |
