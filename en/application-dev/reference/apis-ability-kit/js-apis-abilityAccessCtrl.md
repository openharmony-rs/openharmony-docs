# @ohos.abilityAccessCtrl (Application Access Control)

<!--Kit: Ability Kit-->
<!--Subsystem: Security-->
<!--Owner: @xia-bubai-->
<!--Designer: @linshuqing; @hehehe-li-->
<!--Tester: @leiyuqian-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=7fb5bd7ccfe62b909963659269cc03a975018baf translatedAt=2026-06-17T03:27:46.065Z pushedAt=2026-06-18T12:56:34.955Z -->

## Module Overview

Program access control provides permission verification and management capabilities for apps, supporting permission status checks before accessing protected resources, runtime authorization requests, settings page authorization guidance, and permission status change monitoring. Permissions are divided into three categories: system_grant (automatically granted by the system), user_grant (requires manual user authorization), and [manual_settings](../../security/AccessToken/app-permission-mgmt-overview.md#manual_settings-manual-authorization) (manual setting authorization). Apps must declare the required permissions in the configuration file. For details about the permission management mechanism, see [Application Permission Management Overview](../../security/AccessToken/app-permission-mgmt-overview.md).

This module is mainly used in the following scenarios:

- Before executing a service, verify whether the current app has the permissions required to access protected resources.

- When a permission is not granted, bring up the runtime permission dialog box or the permission settings page to request user authorization.

- Subscribe to permission status change events of the current app, and adjust the service process in a timely manner after the permission status changes.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Key Classes/Interfaces

### Core Enum Types

- **[GrantStatus](#grantstatus):** Enum for permission authorization status, used to indicate the authorization status of the current permission.

- **[SwitchType](#switchtype12):** Enum for global switch types, used to indicate the type of system global switch to request.

- **[PermissionStateChangeType](#permissionstatechangetype18):** Enum for permission state change types, used to indicate changes such as authorization and deauthorization.

- **[PermissionStatus](#permissionstatus20):** Enum for permission status, used to indicate the current permission status.

- **[SelectedResult](#selectedresult22):** Enum for the selection result on the settings page authorization, used to indicate the user's selection result in the permission settings dialog box.

### Core Interface Types

- **[PermissionStateChangeInfo](#permissionstatechangeinfo18):** Permission state change event object, used to return the change type, app identity, and permission name.

- **[PermissionRequestResult](#permissionrequestresult10):** Permission request result object, used to return the list of requested permission names, authorization results, and dialog box display results.

- **[Context](#context10):** Context object, used to initiate a permission request or open the permission settings dialog box.

### Core Classes

- **[AtManager](#atmanager):** Program access control management class, providing capabilities such as permission verification, permission dialog box request, settings page authorization guidance, and permission status monitoring.

![](figures/abilityAccessCtrl.png)

### API Combination Usage Description

Scenario 1: Request authorization before accessing protected resources.

Scenario description: Before an app accesses protected resources such as the camera, microphone, or location, it can verify the permission status through [AtManager](#atmanager), wait for the authorization status to be returned, and then determine whether to request user authorization.

The typical usage process is as follows:

```ts
import { abilityAccessCtrl, Context, Permissions, bundleManager, common } from '@kit.AbilityKit';

// 1. Create a permission management instance
let atManager: abilityAccessCtrl.AtManager = abilityAccessCtrl.createAtManager();
let bundleInfo: bundleManager.BundleInfo =
  bundleManager.getBundleInfoForSelfSync(bundleManager.BundleFlag.GET_BUNDLE_INFO_WITH_APPLICATION);
let tokenID: number = bundleInfo.appInfo.accessTokenId;
let permissionName: Permissions = 'ohos.permission.CAMERA';
let context: Context = this.getUIContext().getHostContext() as common.UIAbilityContext;

// 2. Check whether the target permission has been granted
await atManager.checkAccessToken(tokenID, permissionName);

// 3. If not granted, request the permission from the user
await atManager.requestPermissionsFromUser(context, [permissionName]);

// 4. After the request is complete, confirm the current permission status again
atManager.getSelfPermissionStatus(permissionName);

// 5. Call the protected service capability after the permission is satisfied
// call protected API
```

Scenario 2: Guide the user to authorize through the settings page.

Scenario description: When the user has denied authorization, or the current permission only allows authorization through the settings page, you can first query the current permission status, and then call [openPermissionOnSetting](#openpermissiononsetting22) or [requestPermissionOnSetting](#requestpermissiononsetting12) to guide the user to continue completing the authorization.

The typical usage process is as follows:

```ts
import { abilityAccessCtrl, Context, Permissions, common } from '@kit.AbilityKit';

// 1. Create a permission management instance
let atManager: abilityAccessCtrl.AtManager = abilityAccessCtrl.createAtManager();
let permissionName: Permissions = 'ohos.permission.CAMERA';
let context: Context = this.getUIContext().getHostContext() as common.UIAbilityContext;

// 2. Query the current permission status
atManager.getSelfPermissionStatus(permissionName);

// 3. Guide the user to the Settings page based on the status
await atManager.openPermissionOnSetting(context, permissionName);

// 4. Or request the permission through the Settings authorization process
await atManager.requestPermissionOnSetting(context, [permissionName]);
```

Scenario 3: Monitor changes in your own permission status.

Scenario description: When an app needs to adjust the UI or service logic in real time based on authorization changes, it can use [on](#on18) to subscribe to its own permission status changes. When monitoring is no longer needed, use [off](#off18) to unsubscribe.

The typical usage process is as follows:

```ts
import { abilityAccessCtrl, Permissions } from '@kit.AbilityKit';

// 1. Create a permission management instance
let atManager: abilityAccessCtrl.AtManager = abilityAccessCtrl.createAtManager();
let permissionList: Array<Permissions> = ['ohos.permission.APPROXIMATELY_LOCATION'];
let callback: (data: abilityAccessCtrl.PermissionStateChangeInfo) => void =
  (data: abilityAccessCtrl.PermissionStateChangeInfo): void => {
    console.info('receive permission state change');
    console.info(`data change: ${data.change}, tokenID: ${data.tokenID}, permission name: ${data.permissionName}`);
  };

// 2. Subscribe to the status change of the specified permission
atManager.on('selfPermissionStateChange', permissionList, callback);

// 3. Unsubscribe when no longer needed
atManager.off('selfPermissionStateChange', permissionList, callback);
```

## Modules to Import

```ts
import { abilityAccessCtrl } from '@kit.AbilityKit';
```

## abilityAccessCtrl.createAtManager

createAtManager(): AtManager

Creates a program access control management instance for scenarios such as permission verification, runtime permission request, settings page authorization guidance, and permission status change monitoring. After the call is successful, an AtManager instance is returned, which can be used for subsequent permission management operations.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Security.AccessToken

**Return value**

| Type| Description|
| -------- | -------- |
| [AtManager](#atmanager) | **AtManager** instance obtained.|

**Example**

```ts
// Create a permission management instance
let atManager: abilityAccessCtrl.AtManager = abilityAccessCtrl.createAtManager();
```

## AtManager

Program access control management class, providing capabilities such as permission verification, runtime permission dialog box request, settings page authorization guidance, global switch request, and permission status monitoring. Obtain an instance through [createAtManager](#abilityaccessctrlcreateatmanager).

### checkAccessToken<sup>9+</sup>

checkAccessToken(tokenID: number, permissionName: Permissions): Promise&lt;GrantStatus&gt;

Verifies whether an app has been granted the specified permission. After the call is successful, the authorization status of the current permission is returned. The developer can decide accordingly whether to directly execute subsequent services, continue to initiate a permission request, or guide the user to go to system settings to modify the authorization status. This API uses a promise to return the result.

Applicable to scenarios where a pre-permission check is performed before an app accesses protected resources such as the camera, microphone, or location.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Security.AccessToken

**Parameters**

| Name  | Type                | Mandatory| Description                                      |
| -------- | -------------------  | ---- | ------------------------------------------ |
| tokenID   |  number   | Yes   | Identity identifier of the target app to be verified. It can be obtained through [bundleManager.getBundleInfoSync](js-apis-bundleManager.md#bundlemanagergetbundleinfosync14). If verifying the current app, it can also be obtained through [bundleManager.getBundleInfoForSelfSync](js-apis-bundleManager.md#bundlemanagergetbundleinfoforselfsync10). This parameter must be an integer greater than 0. Passing in 0 returns error code 12100001. |
| permissionName | [Permissions](../../security/AccessToken/app-permissions.md) | Yes   | Name of the permission to be verified. The permission name cannot exceed 256 characters. Passing in an invalid value returns error code 12100001. |

**Return value**

| Type         | Description                               |
| :------------ | :---------------------------------- |
| Promise&lt;[GrantStatus](#grantstatus)&gt; | Promise used to return the authorization status result. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Access Control Error Codes](errorcode-access-token.md).

| ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 12100001 | Invalid parameter. The tokenID is 0, or the permissionName exceeds 256 characters. |

**Example**

```ts
import { abilityAccessCtrl, Permissions, bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Create a permission manager instance
let atManager: abilityAccessCtrl.AtManager = abilityAccessCtrl.createAtManager();
// Obtain the bundleInfo of the app
let bundleInfo = bundleManager.getBundleInfoForSelfSync(bundleManager.BundleFlag.GET_BUNDLE_INFO_WITH_APPLICATION);
// Obtain the TokenID of the app
let tokenID: number = bundleInfo.appInfo.accessTokenId;
// Set the permission name to be verified
let permissionName: Permissions = 'ohos.permission.GRANT_SENSITIVE_PERMISSIONS';
// Verify whether the app has been granted the permission
atManager.checkAccessToken(tokenID, permissionName).then((data: abilityAccessCtrl.GrantStatus) => {
  console.info(`checkAccessToken success, result: ${data}`);
}).catch((err: BusinessError): void => {
  console.error(`checkAccessToken fail, code: ${err.code}, message: ${err.message}`);
});
```

### checkAccessTokenSync<sup>10+</sup>

checkAccessTokenSync(tokenID: number, permissionName: Permissions): GrantStatus

Verifies whether an app has been granted the specified permission, and synchronously returns the authorization status of the permission. The developer can decide accordingly whether to directly execute subsequent service processes, continue to initiate a permission request, or guide the user to go to the settings page to modify the authorization status.

Compared with [checkAccessToken](#checkaccesstoken9), this API returns the authorization status synchronously, making it suitable for permission verification scenarios that do not require asynchronous processing.

Applicable to scenarios where a pre-permission check is performed before an app accesses protected resources such as the camera, microphone, or location.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Security.AccessToken

**Parameters**

| Name  | Type                | Mandatory| Description                                      |
| -------- | -------------------  | ---- | ------------------------------------------ |
| tokenID   |  number   | Yes   | Identity identifier of the target app to be verified. It can be obtained through [bundleManager.getBundleInfoSync](js-apis-bundleManager.md#bundlemanagergetbundleinfosync14). If verifying the current app, it can also be obtained through [bundleManager.getBundleInfoForSelfSync](js-apis-bundleManager.md#bundlemanagergetbundleinfoforselfsync10). This parameter must be an integer greater than 0. If 0 is passed in, error code 12100001 is returned. |
| permissionName | [Permissions](../../security/AccessToken/app-permissions.md) | Yes   | Name of the permission to be verified. The permission name cannot exceed 256 characters. If an invalid value is passed in, error code 12100001 is returned. |

**Return value**

| Type         | Description                               |
| :------------ | :---------------------------------- |
| [GrantStatus](#grantstatus) | Permission grant state.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Access Control Error Codes](errorcode-access-token.md).

| ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 12100001 | Invalid parameter. The tokenID is 0, or the permissionName exceeds 256 characters. |

**Example**

```ts
import { abilityAccessCtrl, Permissions, bundleManager } from '@kit.AbilityKit';

// Create a permission manager instance
let atManager: abilityAccessCtrl.AtManager = abilityAccessCtrl.createAtManager();
// Obtain the bundleInfo of the app
let bundleInfo = bundleManager.getBundleInfoForSelfSync(bundleManager.BundleFlag.GET_BUNDLE_INFO_WITH_APPLICATION);
// Obtain the TokenID of the app
let tokenID: number = bundleInfo.appInfo.accessTokenId;
// Set the permission name to be verified
let permissionName: Permissions = 'ohos.permission.GRANT_SENSITIVE_PERMISSIONS';
// Synchronously verify whether the app has been granted the permission
let data: abilityAccessCtrl.GrantStatus = atManager.checkAccessTokenSync(tokenID, permissionName);
console.info(`Result: ${data}`);
```

### on<sup>18+</sup>

on(type: 'selfPermissionStateChange', permissionList: Array&lt;Permissions&gt;, callback: Callback&lt;PermissionStateChangeInfo&gt;): void

Subscribes to permission authorization status change events for a specified permission list of this app, using an asynchronous callback. It can be used in scenarios such as updating the UI or service logic in real time based on permission status, and monitoring user authorization behavior. When monitoring is no longer needed, call [off](#off18) to unsubscribe.

- When this subscription API is called for multiple times, if the subscribed permission lists are the same but the callbacks are different, the subscription is successful.

- When this subscription API is called for multiple times, if the subscribed permission lists contain the same subset and the callbacks are the same, the subscription fails.

There are two possible scenarios when the permission status changes from "authorized" to "unauthorized":

- User actively revokes: The system will terminate the corresponding app process.

- System actively reclaims: The app process will not be terminated. A typical scenario is the one-time authorization of a security component, which is automatically reclaimed by the system after the authorization period ends.

This API is usually used in conjunction with [off](#off18). When monitoring is no longer needed, call off to unsubscribe.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Security.AccessToken

**Parameters**

| Name            | Type                  | Mandatory| Description                                                         |
| ------------------ | --------------------- | ---- | ------------------------------------------------------------ |
| type               | string                | Yes  | Event type. The value is **'selfPermissionStateChange'**, which indicates the changes in the permission states specific to this application alone. |
| permissionList | Array&lt;[Permissions](../../security/AccessToken/app-permissions.md)&gt;   | Yes   | List of permission names to subscribe to. If empty, it indicates subscription to status changes of all permissions.<br/>The length of each permission name in the list cannot exceed 256 characters. If all permission names in the list are invalid, error code 12100001 is returned.<br/>The array length cannot exceed 1024. If the limit is exceeded, error code 12100001 is returned. |
| callback | Callback&lt;[PermissionStateChangeInfo](#permissionstatechangeinfo18)&gt; | Yes| Callback used to return the result. Callback for subscribing to status change events of the specified permission name.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Access Control Error Codes](errorcode-access-token.md).

| ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 12100001 | Invalid parameter. Possible causes: 1. The permissionList exceeds the size limit; 2. The permissionNames in the list are all invalid. |
| 12100004 | The API is used repeatedly with the same input. |
| 12100005 | The registration time has exceeded the limit. |
| 12100007 | The service is abnormal. |

**Example**

```ts
import { abilityAccessCtrl, Permissions } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // Create a permission management instance
  let atManager: abilityAccessCtrl.AtManager = abilityAccessCtrl.createAtManager();
  // Set the list of permissions to subscribe to
  let permissionList: Array<Permissions> = ['ohos.permission.APPROXIMATELY_LOCATION'];
  // Subscribe to permission status changes
  atManager.on('selfPermissionStateChange', permissionList, (data: abilityAccessCtrl.PermissionStateChangeInfo) => {
    console.info('receive permission state change');
    console.info(`data change: ${data.change}, tokenID: ${data.tokenID}, permission name: ${data.permissionName}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Code: ${error.code}, message: ${error.message}`);
}
```

### off<sup>18+</sup>

off(type: 'selfPermissionStateChange', permissionList: Array&lt;Permissions&gt;, callback?: Callback&lt;PermissionStateChangeInfo&gt;): void

Unsubscribes from permission status change events for the specified permission list of itself. After the unsubscription is successful, status change notifications for the specified permission list will no longer be received.

This API can be called to unsubscribe in scenarios such as when there is no need to continue monitoring permission changes, when the app exits, or when switching pages.

When the callback parameter is not passed in, all callback functions associated with the permissionList will be deleted in batch.

This API is usually used in conjunction with [on](#on18) to cancel the monitoring relationship created through on.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Security.AccessToken

**Parameters**

| Name            | Type                  | Mandatory| Description                                                         |
| ------------------ | --------------------- | ---- | ------------------------------------------------------------ |
| type               | string         | Yes   | Type of the unsubscription event, which is fixed as 'selfPermissionStateChange', indicating a permission status change event.  |
| permissionList | Array&lt;[Permissions](../../security/AccessToken/app-permissions.md)&gt;   | Yes   | List of permission names to unsubscribe from. If empty, it indicates unsubscribing from all permission status changes, and must match the permission list used during [on](#on18) subscription (order insensitive). |
| callback | Callback&lt;[PermissionStateChangeInfo](#permissionstatechangeinfo18)&gt; | No | Callback function. Callback for unsubscribing from the status change event of the specified permission names. If this parameter is not passed, all callback functions associated with permissionList will be deleted in batch.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Access Control Error Codes](errorcode-access-token.md).

| ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 12100004 | The API is not used in pair with "on". |
| 12100007 | The service is abnormal. |

**Example**

```ts
import { abilityAccessCtrl, Permissions } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // Create a permission management instance
  let atManager: abilityAccessCtrl.AtManager = abilityAccessCtrl.createAtManager();
  // Set the permission list to unsubscribe from
  let permissionList: Array<Permissions> = ['ohos.permission.APPROXIMATELY_LOCATION'];
  // Unsubscribe from permission status changes
  atManager.off('selfPermissionStateChange', permissionList);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Code: ${error.code}, message: ${error.message}`);
}
```

### requestPermissionsFromUser<sup>9+</sup>

requestPermissionsFromUser(context: Context, permissionList: Array&lt;Permissions&gt;, requestCallback: AsyncCallback&lt;PermissionRequestResult&gt;): void

Used by <!--RP1-->[UIAbility](js-apis-app-ability-uiAbility.md#uiability)<!--RP1End--> to bring up a dialog box to request [user authorization](../../security/AccessToken/request-user-authorization.md), and returns the authorization result of the permissions requested this time. This API uses an asynchronous callback to return the result.

Applicable to scenarios where an app proactively applies for [user_grant](../../security/AccessToken/app-permission-mgmt-overview.md#user_grant-user-authorization) permissions from the user before accessing protected resources for the first time.

If the user denies authorization, the authorization dialog box cannot be brought up again through this API. The developer can guide the user to go to the system settings interface for manual authorization, or call [requestPermissionOnSetting](#requestpermissiononsetting12) to bring up the permission settings dialog box to guide the user to complete authorization.

<!--RP3-->
![requestPermissionsFromUser](figures/requestPermissionsFromUser.png)
<!--RP3End-->

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Security.AccessToken

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| context | [Context](js-apis-inner-application-context.md) | Yes | Context of the <!--RP1-->UIAbility<!--RP1End--> requesting the permission. If the context of another app, an invalid page, or a non-stage model is passed in, the API may report an error or fail to display the dialog box. |
| permissionList | Array&lt;[Permissions](../../security/AccessToken/app-permissions.md)&gt; | Yes | List of permission names. This array cannot be empty. It is recommended to pass in only the sensitive permissions necessary for the current business scenario, avoiding requesting too many permissions at once. The length of a permission name cannot exceed 256 characters. |
| requestCallback | AsyncCallback&lt;[PermissionRequestResult](js-apis-permissionrequestresult.md)&gt; | Yes | Callback function. After the call is complete, error information is returned through **err**, and the permission request result object is returned through **data**. The developer can determine whether the user has authorized, whether a dialog box has been displayed, and the reason for failure based on the permission request result. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Access Control Error Codes](errorcode-access-token.md).

| ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 12100001 | (Deprecated in 12) Invalid parameter. The context is invalid when it does not belong to the application itself. |
| 12100009 | Common inner error. An error occurs when creating the pop-up window or obtaining user operation results. |

**Example**

For details about how to obtain the context in the example, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

For details about the process and example of applying for user authorization, see [Requesting User Authorization](../../security/AccessToken/request-user-authorization.md).
<!--code_no_check-->

```ts
import { abilityAccessCtrl, Context, PermissionRequestResult, common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Create a permission manager instance
let atManager: abilityAccessCtrl.AtManager = abilityAccessCtrl.createAtManager();
// Obtain the context within the component.
let context: Context = this.getUIContext().getHostContext() as common.UIAbilityContext;
// Request user authorization
atManager.requestPermissionsFromUser(context, ['ohos.permission.CAMERA'], (err: BusinessError, data: PermissionRequestResult) => {
  if (err) {
    console.error(`requestPermissionsFromUser fail, code: ${err.code}, message: ${err.message}`);
  } else {
    console.info(`requestPermissionsFromUser success, result: ${data}`);
    console.info('requestPermissionsFromUser data permissions:' + data.permissions);
    console.info('requestPermissionsFromUser data authResults:' + data.authResults);
    console.info('requestPermissionsFromUser data dialogShownResults:' + data.dialogShownResults);
    console.info('requestPermissionsFromUser data errorReasons:' + data.errorReasons);
  }
});
```

### requestPermissionsFromUser<sup>9+</sup>

requestPermissionsFromUser(context: Context, permissionList: Array&lt;Permissions&gt;): Promise&lt;PermissionRequestResult&gt;

Used by <!--RP1-->[UIAbility](js-apis-app-ability-uiAbility.md#uiability)<!--RP1End--> to bring up a dialog box to request [user authorization](../../security/AccessToken/request-user-authorization.md), and returns the authorization result of the permissions requested this time. This API uses a promise to return the result.

Applicable to scenarios where an app proactively applies for user_grant permissions from the user before accessing protected resources for the first time.

If the user denies authorization, the authorization dialog box cannot be brought up again through this API. The developer can guide the user to go to the system settings interface for manual authorization, or call [requestPermissionOnSetting](#requestpermissiononsetting12) to bring up the permission settings dialog box to guide the user to complete authorization.

**Atomic service API**: This API can be used in atomic services since API version 11.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Security.AccessToken

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| context | [Context](js-apis-inner-application-context.md) | Yes | Context of the <!--RP1-->UIAbility<!--RP1End--> requesting the permission. If the context of another app, an invalid page, or a non-stage model is passed in, the API may report an error or fail to display the dialog box. |
| permissionList | Array&lt;[Permissions](../../security/AccessToken/app-permissions.md)&gt; | Yes | List of permission names. This array cannot be empty. It is recommended to pass in only the sensitive permissions necessary for the current business scenario and avoid requesting too many permissions at once. The length of a permission name cannot exceed 256 characters. |

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;[PermissionRequestResult](js-apis-permissionrequestresult.md)&gt; | Promise used to return the permission request result object, which contains information such as the permission array, the authorization result of each permission, whether to show a dialog box, and the failure reason. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Access Control Error Codes](errorcode-access-token.md).

| ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 12100001 | (Deprecated in 12) Invalid parameter. The context is invalid when it does not belong to the application itself. |
| 12100009 | Common inner error. An error occurs when creating the pop-up window or obtaining user operation results. |

**Example**

For details about how to obtain the context in the example, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

For details about the process and example of applying for user authorization, see [Requesting User Authorization](../../security/AccessToken/request-user-authorization.md).
<!--code_no_check-->

```ts
import { abilityAccessCtrl, Context, PermissionRequestResult, common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Create a permission manager instance
let atManager: abilityAccessCtrl.AtManager = abilityAccessCtrl.createAtManager();
// Obtain the context within the component.
let context: Context = this.getUIContext().getHostContext() as common.UIAbilityContext;
// Request user authorization
atManager.requestPermissionsFromUser(context, ['ohos.permission.CAMERA']).then((data: PermissionRequestResult) => {
  console.info(`requestPermissionsFromUser success, result: ${data}`);
  console.info('requestPermissionsFromUser data permissions:' + data.permissions);
  console.info('requestPermissionsFromUser data authResults:' + data.authResults);
  console.info('requestPermissionsFromUser data dialogShownResults:' + data.dialogShownResults);
  console.info('requestPermissionsFromUser data errorReasons:' + data.errorReasons);
}).catch((err: BusinessError): void => {
  console.error(`requestPermissionsFromUser fail, code: ${err.code}, message: ${err.message}`);
});
```

### requestPermissionOnSetting<sup>12+</sup>

requestPermissionOnSetting(context: Context, permissionList: Array&lt;Permissions&gt;): Promise&lt;Array&lt;GrantStatus&gt;&gt;

Used by [UIAbility](js-apis-app-ability-uiAbility.md#uiability)/[UIExtensionAbility](js-apis-app-ability-uiExtensionAbility.md#uiextensionability) to bring up the permission settings dialog box for a second time, and returns an array of authorization statuses. This API uses a promise to return the result.

Applicable to scenarios where the user has already denied the permission grant in the first dialog box and needs to continue applying for the permission through the settings page.

Before calling this API, the app needs to call [requestPermissionsFromUser](#requestpermissionsfromuser9) first. If the user has already authorized in the first dialog box, calling this API will not bring up the authorization dialog box.

<!--RP4-->
![requestPermissionOnSetting](figures/requestPermissionOnSetting.png)
<!--RP4End-->

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Security.AccessToken

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| context | [Context](js-apis-inner-application-context.md) | Yes | Context of the UIAbility or UIExtensionAbility requesting the permission. If the context of another app, an invalid page, or a non-stage model is passed in, the API may report an error or fail to display the pop-up window. |
| permissionList | Array&lt;[Permissions](../../security/AccessToken/app-permissions.md)&gt; | Yes | List of permission names. This array cannot be empty. Only user_grant permissions that have been declared and for which the user has revoked authorization can be passed in, and the permissions passed in must belong to the same [permission group](../../security/AccessToken/app-permission-group-list.md). The length of a permission name cannot exceed 256 characters. |

**Return value**

| Type         | Description                               |
| :------------ | :---------------------------------- |
| Promise&lt;Array&lt;[GrantStatus](#grantstatus)&gt;&gt; | Promise used to return an array of authorization statuses. Each element in the array corresponds to the authorization result of the respective permission in permissionList.|

**Error codes**

For details about the error codes, see [Access Control Error Codes](errorcode-access-token.md).

| ID| Error Message|
| -------- | -------- |
| 12100001 | Invalid parameter. Possible causes:<br>1. The context is invalid because it does not belong to the application itself;<br>2. The permission list contains the permission that is not declared in the module.json file;<br>3. The permission list is invalid because the permissions in it do not belong to the same permission group;<br>4. The permission list contains one or more system_grant permissions. |
| 12100009 | Common inner error. An error occurs when creating the pop-up window or obtaining user operation result. |
| 12100011 | All permissions in the permission list have been granted. |
| 12100012 | The permission list contains the permission that has not been revoked by the user. |
| 12100014 | Unexpected permission. You cannot request this type of permission from users via a pop-up window. |

**Example**
For details about how to obtain the context in the example, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).
<!--code_no_check-->

```ts
import { abilityAccessCtrl, Context, common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Create a permission manager instance
let atManager: abilityAccessCtrl.AtManager = abilityAccessCtrl.createAtManager();
// Obtain the context within the component.
let context: Context = this.getUIContext().getHostContext() as common.UIAbilityContext;
// Open the permission settings dialog box
atManager.requestPermissionOnSetting(context, ['ohos.permission.CAMERA']).then((data: Array<abilityAccessCtrl.GrantStatus>) => {
  console.info(`requestPermissionOnSetting success, result: ${data}`);
}).catch((err: BusinessError): void => {
  console.error(`requestPermissionOnSetting fail, code: ${err.code}, message: ${err.message}`);
});
```

### requestGlobalSwitch<sup>12+</sup>

requestGlobalSwitch(context: Context, type: SwitchType): Promise&lt;boolean&gt;

Used by UIAbility/UIExtensionAbility to bring up the global switch settings dialog box. After the call is successful, if the global switch is off, the global switch settings interface will pop up for the user to operate. If the global switch is already on, the dialog box will not be brought up and **true** will be returned. This API uses a promise to return the result.

Applicable to scenarios that depend on system-level global switches (such as camera, microphone, and location) being turned on.

When an app needs to use functions such as the camera, microphone, or location that require global switch control, if the corresponding global switch is turned off, the app can bring up this dialog box to request the user to turn on the corresponding function. If the current global switch status is on, the dialog box will not be brought up.

<!--RP5-->
![requestGlobalSwitch](figures/requestGlobalSwitch.png)
<!--RP5End-->

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Security.AccessToken

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| context | [Context](js-apis-inner-application-context.md) | Yes | Context of the UIAbility or UIExtensionAbility that requests the global switch. If the context of another app, an invalid page, or a non-stage model is passed in, the API may report an error or fail to display the dialog box. |
| type | [SwitchType](#switchtype12) | Yes | Specifies the type of global switch to request to enable. |

**Return value**

| Type         | Description                               |
| :------------ | :---------------------------------- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** indicates the current global switch is enabled, and **false** indicates the current global switch is still disabled. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Access Control Error Codes](errorcode-access-token.md).

| ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 12100001 | Invalid parameter. Possible causes: 1. The context is invalid because it does not belong to the application itself; 2. The type of global switch is not support. |
| 12100009 | Common inner error. An error occurs when creating the pop-up window or obtaining user operation result. |
| 12100013 | The specific global switch is already open. |

**Example**
For details about how to obtain the context in the example, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).
<!--code_no_check-->

```ts
import { abilityAccessCtrl, Context, common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Create a permission manager instance
let atManager: abilityAccessCtrl.AtManager = abilityAccessCtrl.createAtManager();
// Obtain the context within the component.
let context: Context = this.getUIContext().getHostContext() as common.UIAbilityContext;
// Open the global switch settings dialog box
atManager.requestGlobalSwitch(context, abilityAccessCtrl.SwitchType.CAMERA).then((data: boolean) => {
  console.info(`requestGlobalSwitch success, result: ${data}`);
}).catch((err: BusinessError): void => {
  console.error(`requestGlobalSwitch fail, code: ${err.code}, message: ${err.message}`);
});
```

### getSelfPermissionStatus<sup>20+</sup>

getSelfPermissionStatus(permissionName: Permissions): PermissionStatus

Queries the permission status of the current app and returns the result synchronously. After the call is successful, the status of the current permission is returned. Unlike [checkAccessToken](#checkaccesstoken9), this API does not require passing in the app identity and is only used to query the permission status of the current app itself.

Applicable to scenarios such as before determining whether to request a permission, confirming the authorization result after a permission request, or re-querying after monitoring a permission status change.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Security.AccessToken

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| permissionName | [Permissions](../../security/AccessToken/app-permissions.md) | Yes | Name of the permission whose status is to be queried. The permission name cannot be empty and its length cannot exceed 256 characters. If an invalid value is passed, error code 12100001 is returned. |

**Return value**

| Type         | Description                               |
| :------------ | :---------------------------------- |
| [PermissionStatus](#permissionstatus20) | Permission status.|

**Error codes**

For details about the error codes, see [Access Control Error Codes](errorcode-access-token.md).

| ID| Error Message|
| -------- | -------- |
| 12100001 | Invalid parameter. The permissionName is empty or exceeds 256 characters. |
| 12100007 | The service is abnormal. |

**Example**

```ts
import { abilityAccessCtrl } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Create a permission management instance
let atManager: abilityAccessCtrl.AtManager = abilityAccessCtrl.createAtManager();
try {
  // Query the permission status of the current app
  let data: abilityAccessCtrl.PermissionStatus = atManager.getSelfPermissionStatus('ohos.permission.CAMERA');
  console.info(`getSelfPermissionStatus success, result: ${data}`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`getSelfPermissionStatus fail, code: ${error.code}, message: ${error.message}`);
}
```

### openPermissionOnSetting<sup>22+</sup>

openPermissionOnSetting(context: Context, permission: Permissions): Promise&lt;SelectedResult&gt;

Used by [UIAbility](js-apis-app-ability-uiAbility.md#uiability)/[UIExtensionAbility](js-apis-app-ability-uiExtensionAbility.md#uiextensionability) to bring up the permission settings page. After the call is successful, the permission settings page will be opened. After the user operates on the page, the user's selection result on the settings page will be returned. This API uses a promise to return the result.

Applicable to scenarios where [manual_settings](../../security/AccessToken/app-permission-mgmt-overview.md#manual_settings-manual-authorization) type permissions cannot be applied for through the normal authorization dialog box and the user must be guided to enter system settings to complete authorization. manual_settings type permissions are permissions that can only be manually enabled by the user in system settings and cannot be directly applied for through the normal authorization dialog box.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Security.AccessToken

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| context | [Context](js-apis-inner-application-context.md) | Yes | Context of the UIAbility or UIExtensionAbility requesting the permission. If the context of another app, an invalid page, or a non-stage model is passed in, the API may report an error or fail to open the settings page. |
| permission | [Permissions](../../security/AccessToken/app-permissions.md) | Yes | Name of the permission for which the settings page needs to be opened. The permission name cannot exceed 256 characters. If an invalid permission or a permission not declared in module.json is passed in, error code 12100001 is returned. Only permissions of the [manual_settings](../../security/AccessToken/app-permission-mgmt-overview.md#manual_settings-manual-authorization) type are supported. If a permission of another type is passed in, error code 12100014 is returned. |

**Return value**

| Type         | Description                               |
| :------------ | :---------------------------------- |
| Promise&lt;[SelectedResult](#selectedresult22)&gt; | Promise used to return the user's selection result on the settings page. |

**Error codes**

For details about the error codes, see [Access Control Error Codes](errorcode-access-token.md).

| ID| Error Message|
| -------- | -------- |
| 12100001 | Invalid parameter. Possible causes:<br>1. The context is invalid because it does not belong to the application itself;<br>2. The permission is invalid or not declared in the module.json file. |
| 12100009 | Common inner error. An error occurs when creating the pop-up window or obtaining user operation result. |
| 12100014 | Unexpected permission. The permission is not a manual_settings permission. |

**Example**

For details about how to obtain the context in the example, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```ts
import { abilityAccessCtrl, Context, common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Create a permission manager instance
let atManager: abilityAccessCtrl.AtManager = abilityAccessCtrl.createAtManager();
// Obtain the context within the component.
let context: Context = this.getUIContext().getHostContext() as common.UIAbilityContext;
// Launch the pop-up window for redirecting to the settings page
atManager.openPermissionOnSetting(context, 'ohos.permission.HOOK_KEY_EVENT').then((data: abilityAccessCtrl.SelectedResult) => {
  console.info(`openPermissionOnSetting success, result: ${data}`);
}).catch((err: BusinessError): void => {
  console.error(`openPermissionOnSetting fail, code: ${err.code}, message: ${err.message}`);
});
```

### verifyAccessTokenSync<sup>9+</sup>

verifyAccessTokenSync(tokenID: number, permissionName: Permissions): GrantStatus

Verifies whether an app has been granted the specified permission, and synchronously returns the authorization status of the permission. The developer can decide accordingly whether to directly execute subsequent service processes, continue to initiate a permission request, or guide the user to go to system settings to modify the authorization status.

Applicable to scenarios where a pre-permission check is performed before an app accesses protected resources such as the camera, microphone, or location.

It is recommended to use [checkAccessTokenSync](#checkaccesstokensync10) instead.

**System capability**: SystemCapability.Security.AccessToken

**Parameters**

| Name  | Type                | Mandatory| Description                                      |
| -------- | -------------------  | ---- | ------------------------------------------ |
| tokenID   |  number   | Yes   | Identity identifier of the target app to be verified. It can be obtained through [bundleManager.getBundleInfoSync](js-apis-bundleManager.md#bundlemanagergetbundleinfosync14). If verifying the current app, it can also be obtained through [bundleManager.getBundleInfoForSelfSync](js-apis-bundleManager.md#bundlemanagergetbundleinfoforselfsync10). This parameter must be an integer greater than 0. If 0 is passed in, error code 12100001 is returned. |
| permissionName | [Permissions](../../security/AccessToken/app-permissions.md) | Yes   | Name of the permission to be verified. The permission name cannot exceed 256 characters. If an invalid value is passed in, error code 12100001 is returned. |

**Return value**

| Type         | Description                               |
| :------------ | :---------------------------------- |
| [GrantStatus](#grantstatus) | Permission grant state.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Access Control Error Codes](errorcode-access-token.md).

| ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 12100001 | Invalid parameter. The tokenID is 0, or the permissionName exceeds 256 characters. |

**Example**

```ts
import { abilityAccessCtrl, Permissions, bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Create a permission manager instance
let atManager: abilityAccessCtrl.AtManager = abilityAccessCtrl.createAtManager();
// Obtain the bundleInfo of the app
let bundleInfo = bundleManager.getBundleInfoForSelfSync(bundleManager.BundleFlag.GET_BUNDLE_INFO_WITH_APPLICATION);
// Obtain the TokenID of the app
let tokenID: number = bundleInfo.appInfo.accessTokenId;
try {
  // Set the permission name to be verified
  let permissionName: Permissions = 'ohos.permission.GRANT_SENSITIVE_PERMISSIONS';
  // Synchronously verify whether the app has been granted the permission
  let data: abilityAccessCtrl.GrantStatus = atManager.verifyAccessTokenSync(tokenID, permissionName);
  console.info(`verifyAccessTokenSync success, result: ${data}`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`verifyAccessTokenSync fail, code: ${error.code}, message: ${error.message}`);
}
```

### verifyAccessToken<sup>9+</sup>

verifyAccessToken(tokenID: number, permissionName: Permissions): Promise&lt;GrantStatus&gt;

Verifies whether an app has been granted the specified permission. After the call is successful, the authorization status of the current permission is returned. The developer can decide accordingly whether to directly execute subsequent services, continue to initiate a permission request, or guide the user to go to system settings to modify the authorization status. This API uses a promise to return the result.

Applicable to scenarios where a pre-permission check is performed before an app accesses protected resources.

> **NOTE**
>
> You are advised to use [checkAccessToken](#checkaccesstoken9).

**System capability**: SystemCapability.Security.AccessToken

**Parameters**

| Name  | Type                | Mandatory| Description                                      |
| -------- | -------------------  | ---- | ------------------------------------------ |
| tokenID   |  number   | Yes   | Identity identifier of the target app to be verified. It can be obtained through [bundleManager.getBundleInfoSync](js-apis-bundleManager.md#bundlemanagergetbundleinfosync14). If verifying the current app, it can also be obtained through [bundleManager.getBundleInfoForSelfSync](js-apis-bundleManager.md#bundlemanagergetbundleinfoforselfsync10). This parameter must be an integer greater than 0. If 0 is passed in, error code 12100001 is returned. |
| permissionName | [Permissions](../../security/AccessToken/app-permissions.md) | Yes   | Name of the permission to be verified. The permission name cannot exceed 256 characters. If an invalid value is passed in, error code 12100001 is returned. |

**Return value**

| Type         | Description                               |
| :------------ | :---------------------------------- |
| Promise&lt;[GrantStatus](#grantstatus)&gt; | Promise used to return the authorization status result. |

**Example**

```ts
import { abilityAccessCtrl, Permissions, bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Create a permission manager instance
let atManager: abilityAccessCtrl.AtManager = abilityAccessCtrl.createAtManager();
// Obtain the bundleInfo of the app
let bundleInfo = bundleManager.getBundleInfoForSelfSync(bundleManager.BundleFlag.GET_BUNDLE_INFO_WITH_APPLICATION);
// Obtain the TokenID of the app
let tokenID: number = bundleInfo.appInfo.accessTokenId;
// Set the permission name to be verified
let permissionName: Permissions = 'ohos.permission.GRANT_SENSITIVE_PERMISSIONS';
// Verify whether the app has been granted the permission
atManager.verifyAccessToken(tokenID, permissionName).then((data: abilityAccessCtrl.GrantStatus) => {
  console.info(`verifyAccessToken success, result: ${data}`);
}).catch((err: BusinessError): void => {
  console.error(`verifyAccessToken fail, code: ${err.code}, message: ${err.message}`);
});
```

### verifyAccessToken<sup>(deprecated)</sup>

verifyAccessToken(tokenID: number, permissionName: string): Promise&lt;GrantStatus&gt;

Verifies whether an app has been granted the specified permission. After the call is successful, the authorization status of the current permission is returned, and the developer can decide on subsequent operations accordingly. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. It is recommended to use [checkAccessToken](#checkaccesstoken9) instead.

**System capability**: SystemCapability.Security.AccessToken

**Parameters**

| Name  | Type                | Mandatory| Description                                      |
| -------- | -------------------  | ---- | ------------------------------------------ |
| tokenID   |  number   | Yes   | Identity identifier of the target app to be verified. It can be obtained through [bundleManager.getBundleInfoSync](js-apis-bundleManager.md#bundlemanagergetbundleinfosync14). If verifying the current app, it can also be obtained through [bundleManager.getBundleInfoForSelfSync](js-apis-bundleManager.md#bundlemanagergetbundleinfoforselfsync10). This parameter must be an integer greater than 0. Passing in 0 returns error code 12100001. |
| permissionName | string | Yes   | Name of the permission to be verified. The permission name cannot exceed 256 characters. Passing in an invalid value returns error code 12100001. |

**Return value**

| Type         | Description                               |
| :------------ | :---------------------------------- |
| Promise&lt;[GrantStatus](#grantstatus)&gt; | Promise used to return the authorization status result. |

**Example**

```ts
import { abilityAccessCtrl, Permissions, bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Create a permission manager instance
let atManager: abilityAccessCtrl.AtManager = abilityAccessCtrl.createAtManager();
// Obtain the bundleInfo of the app
let bundleInfo = bundleManager.getBundleInfoForSelfSync(bundleManager.BundleFlag.GET_BUNDLE_INFO_WITH_APPLICATION);
// Obtain the TokenID of the app
let tokenID: number = bundleInfo.appInfo.accessTokenId;
// Set the permission name to be verified
let permissionName: Permissions = 'ohos.permission.GRANT_SENSITIVE_PERMISSIONS';
// Verify whether the app has been granted the permission
atManager.verifyAccessToken(tokenID, permissionName).then((data: abilityAccessCtrl.GrantStatus) => {
  console.info(`verifyAccessToken success, result: ${data}`);
}).catch((err: BusinessError): void => {
  console.error(`verifyAccessToken fail, code: ${err.code}, message: ${err.message}`);
});
```

## GrantStatus

Enumerates the permission grant states.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Security.AccessToken

| Name              |    Value| Description       |
| ------------------ | ----- | ----------- |
| PERMISSION_DENIED  | -1    | The permission is not granted.|
| PERMISSION_GRANTED | 0     | The permission is granted.|

## SwitchType<sup>12+</sup>

Enumerates the global switch types.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Security.AccessToken

| Name              |    Value| Description       |
| ------------------ | ----- | ----------- |
| CAMERA  | 0    | Global switch of the camera.|
| MICROPHONE | 1     | Global switch of the microphone.|
| LOCATION | 2     | Global switch of the location service.|

## PermissionStateChangeType<sup>18+</sup>

Enumerates the operations that trigger permission state changes.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Security.AccessToken

| Name                    |    Value| Description             |
| ----------------------- | ------ | ----------------- |
| PERMISSION_REVOKED_OPER | 0      | Operation to revoke a permission.|
| PERMISSION_GRANTED_OPER | 1      | Operation to grant a permission.|

## PermissionStateChangeInfo<sup>18+</sup>

Represents the permission state change details.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.Security.AccessToken

| Name          | Type                      | Read Only| Optional| Description               |
| -------------- | ------------------------- | ---- | ---- | ------------------ |
| change         | [PermissionStateChangeType](#permissionstatechangetype18) | No  | No  | Operation that triggers the permission state change.       |
| tokenID        | number                    | No  | No  | ID of the subscribed application, which can be obtained from the accessTokenId field of [ApplicationInfo](js-apis-bundleManager-applicationInfo.md#applicationinfo-1) in [BundleInfo](js-apis-bundleManager-bundleInfo.md) of the application. The token ID of the current application can be obtained through [bundleManager.getBundleInfoForSelfSync](js-apis-bundleManager.md#bundlemanagergetbundleinfoforselfsync10).|
| permissionName | [Permissions](../../security/AccessToken/app-permissions.md)                    | No  | No  | Permissions whose authorization state changes. For details about the permissions, see [Application Permissions](../../security/AccessToken/app-permissions.md).|

## PermissionRequestResult<sup>10+</sup>

type PermissionRequestResult = _PermissionRequestResult

Permission request result object, containing information such as the list of requested permission names, the authorization result of each permission, the dialog box display result, and the failure reason.

**Atomic service API**: This API can be used in atomic services since API version 11.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Security.AccessToken

| Type| Description|
| -------- | -------- |
| [_PermissionRequestResult](js-apis-permissionrequestresult.md) | Permission request result object, which contains information such as the list of requested permission names, the authorization result of each permission, the pop-up display result, and the failure reason. |

## Context<sup>10+</sup>

type Context = _Context

Provides the context for the ability or application, which can be used to access application resources.

**Atomic service API**: This API can be used in atomic services since API version 11.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Security.AccessToken

| Type| Description|
| -------- | -------- |
| [_Context](js-apis-inner-application-context.md) | Provides the context of an ability or application, which can be used to access the resources of the app. |

## PermissionStatus<sup>20+</sup>

Enumerates the permission states.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.Security.AccessToken

| Name              |    Value| Description       |
| ------------------ | ----- | ----------- |
| DENIED  | -1    | The permission is not granted.|
| GRANTED | 0     | The permission is granted.|
| NOT_DETERMINED | 1     | Indicates not operated. The app declares a [user authorization permission](../../security/AccessToken/permissions-for-all-user.md) but has not yet called the [requestPermissionsFromUser](#requestpermissionsfromuser9) API to request authorization, or the user has changed the permission status to asking every time in settings, and this value is returned when querying the permission status. |
| INVALID | 2     | The permission is invalid. The application does not [declare permissions](../../security/AccessToken/declare-permissions.md) or cannot process the request. For example, if the status of the approximate location permission is **NOT_DETERMINED**, this value will be returned when the status of the precise location permission is queried.|
| RESTRICTED | 3     | Indicates restricted. <!--RP2-->The app is prohibited from requesting user authorization through the [requestPermissionsFromUser](#requestpermissionsfromuser9) API. <!--RP2End--> |

## SelectedResult<sup>22+</sup>

Enumerates the results of the dialog box for redirection to the settings page.

**System capability**: SystemCapability.Security.AccessToken

| Name              |    Value| Description       |
| ------------------ | ----- | ----------- |
| REJECTED | -1    | The user chooses not to go to the settings.|
| OPENED | 0     | The user chooses to go to the settings.|
| GRANTED | 1     | The permission has been granted and no dialog box is displayed.|