# @ohos.account.osAccount.authorization (System Account Authorization Management)

<!--Kit: Basic Services Kit-->
<!--Subsystem: Account-->
<!--Owner: @steven-q-->
<!--Designer: @JiDong-CS1-->
<!--Tester: @pan9f-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=837809eb745c38fb219a272acb4b421de1551164 translatedAt=2026-11-09T10:22:17.248Z pushedAt=2026-11-09T11:08:25.232Z nl=1 -->

This module provides the authorization management capability for local accounts of the operating system. You can use the APIs in this namespace to request authorization for the specified [Privilege](#privilege). These privileges are granted based on the authorization policy and user consent.

**Since:** 26.0.1

## Modules to Import

```ts
import { authorization } from '@kit.BasicServicesKit';
```

## authorization.getAuthorizationManager

getAuthorizationManager(): AuthorizationManager

Obtains an [AuthorizationManager](#authorizationmanager) instance.

**Since:** 26.0.1

**System capability**: SystemCapability.Account.OsAccount

**Model restriction:** This API can be used only in the stage model.

**Return value**

| Type                                            | Description               |
| ----------------------------------------------- | ------------------ |
| [AuthorizationManager](#authorizationmanager) | Authorization manager instance. |

**Example**

```ts
import { authorization } from '@kit.BasicServicesKit';

let authorizationManager: authorization.AuthorizationManager = authorization.getAuthorizationManager();
```

## AuthorizationManager

Defines the authorization manager for requesting and checking authorization.

**Since:** 26.0.1

**System capability**: SystemCapability.Account.OsAccount

### requestAuthorization

requestAuthorization(privilege: Privilege, context: UIAbilityContext): Promise&lt;AuthorizationResult&gt;

Requests to grant the specified privilege to the current process. This API uses a promise to return the result.

When the app is in the foreground and no valid authorization exists, the authorization dialog box is displayed as a modal application dialog box. If a valid authorization already exists, it is reused directly.

**Since:** 26.0.1

**System capability**: SystemCapability.Account.OsAccount

**Model restriction:** This API can be used only in the stage model.

**Required permissions:** ohos.permission.REQUEST_LOCAL_ACCOUNT_AUTHORIZATION

**Parameters**

| Name | Type                                                | Mandatory | Description                                                             |
| -------------- | --------------------------------------------------- | --------- | ---------------------------------------------------------------------- |
| privilege      | [Privilege](#privilege)                             | Yes       | Target privilege.      |
| context        | [UIAbilityContext](../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md) | Yes       | Context of the UIAbility that hosts the authorization dialog box. |

**Return value**

| Type                                                  | Description                         |
| ----------------------------------------------------- | ----------------------------------- |
| Promise&lt;[AuthorizationResult](#authorizationresult)&gt; | Promise used to return the authorization result. |

**Error codes**

For details about the error codes, see [Account Management Error Codes](errorcode-account.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 201      | Permission denied.                                           |
| 12300001 | The system service works abnormally.                         |
| 12300302 | User interaction is required but not allowed.<br>Possible causes: 1. The specified UI context is invalid; 2. The application is not in the foreground.<br>Suggested solutions: Ensure the application is in the foreground and pass a valid UIAbilityContext.                |
| 12300304 | Authorization service is busy. <br>Possible cause: Another authorization is being processed.                               |

**Example**

```ts
import { authorization, BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// Obtain the UIAbilityContext.
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;

try {
  authorization.getAuthorizationManager().requestAuthorization(
    authorization.Privilege.PRIVILEGE_OPERATE_RAW_NET_PACKETS, context
  ).then((result: authorization.AuthorizationResult) => {
    console.info('requestAuthorization successfully, resultCode: ' + result.resultCode);
  }).catch((err: BusinessError) => {
    console.error(`requestAuthorization failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`requestAuthorization exception: code is ${err.code}, message is ${err.message}`);
}
```

### hasAuthorization

hasAuthorization(privilege: Privilege): Promise&lt;boolean&gt;

Checks whether the current process has the authorization for the specified privilege. This API uses a promise to return the result.

**Since:** 26.0.1

**System capability**: SystemCapability.Account.OsAccount

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name | Type                    | Mandatory | Description                                                   |
| -------------- | ----------------------- | --------- | ------------------------------------------------------------- |
| privilege      | [Privilege](#privilege) | Yes       | Target privilege.|

**Return value**

| Type                   | Description                                                               |
| ---------------------- | ------------------------------------------------------------------------- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** indicates that the current process has the authorization for the specified privilege, and **false** indicates the opposite. |

**Error codes**

For details about the error codes, see [Account Management Error Codes](errorcode-account.md).

| ID | Error Message                             |
| -------- | ------------------------------------ |
| 12300001 | The system service works abnormally. |

**Example**

```ts
import { authorization, BusinessError } from '@kit.BasicServicesKit';

try {
  authorization.getAuthorizationManager().hasAuthorization(
    authorization.Privilege.PRIVILEGE_OPERATE_RAW_NET_PACKETS
  ).then((isAuthorized: boolean) => {
    console.info('hasAuthorization successfully, isAuthorized: ' + isAuthorized);
  }).catch((err: BusinessError) => {
    console.error(`hasAuthorization failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`hasAuthorization exception: code is ${err.code}, message is ${err.message}`);
}
```

## Privilege

Enumerates all privileges that can be authorized.

Before requesting authorization for these privileges, ensure that the current app and running environment meet the authorization policy requirements. For the detailed definition of each privilege (including the authorization policy), see [OS Account Privilege List](appendix-osAccount-authorization-privileges.md).

**Since:** 26.0.1

**System capability**: SystemCapability.Account.OsAccount

**Model restriction:** This API can be used only in the stage model.

| Name                             | Value                                            | Description                 |
| -------------------------------- | --------------------------------------------- | -------------------- |
| PRIVILEGE_OPERATE_RAW_NET_PACKETS | 'ohos.privilege.operate_raw_net_packets' | Privilege to operate raw network packets. |
| PRIVILEGE_MONITOR_RAW_USB_PACKETS | 'ohos.privilege.monitor_raw_usb_packets' | Privilege to monitor USB packets. |

## AuthorizationResultCode

Enumerates the authorization result codes.

**Since:** 26.0.1

**System capability**: SystemCapability.Account.OsAccount

**Model restriction:** This API can be used only in the stage model.

| Name                       | Value    | Description                                                                                                                              |
| -------------------------- | -------- | --------------------------------------------------------------------------------------------------------------------------------- |
| AUTHORIZATION_GRANTED      | 0        | Authorization granted.                                                                                                                        |
| AUTHORIZATION_CANCELED     | 12300301 | Authorization canceled by the user.<br>Possible causes: The user closes the authorization control, or taps the **Cancel** button in the authorization control window.                        |
| AUTHORIZATION_DENIED       | 12300303 | Authorization denied by the system policy.<br>Possible causes: The authorization policy corresponding to the privilege is not met. For example, the privilege requires the caller to hold the specified application permission and run in an administrator-type system account session.|
| AUTHORIZATION_NOT_SUPPORTED | 12300305 | The authorization request is not supported.<br>Possible causes: The requested target privilege is not registered or is missing in the current system version, and its associated functions are usually not supported either.                                        |

## AuthorizationResult

Defines the authorization result. Currently, the authorization validity period of all [Privilege](#privilege) is bound to the lifecycle of the calling process (it becomes invalid when the process is destroyed).

**Since:** 26.0.1

**System capability**: SystemCapability.Account.OsAccount

**Model restriction:** This API can be used only in the stage model.

| Name         | Type                                              | Read-Only  | Optional | Description                                                                                             |
| ------------ | ------------------------------------------------- | ----- | ---- | ----------------------------------------------------------------------------------------------- |
| resultCode   | [AuthorizationResultCode](#authorizationresultcode) |  No | No  | Authorization result code. If the authorization is granted, **AUTHORIZATION_GRANTED** is returned; otherwise, the corresponding error code is returned. |
| privilege    | [Privilege](#privilege)                           |  No | No  | Privilege corresponding to the authorization. |
