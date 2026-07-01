# PermissionRequestResult

<!--Kit: Ability Kit-->
<!--Subsystem: Security-->
<!--Owner: @xia-bubai-->
<!--Designer: @linshuqing; @hehehe-li-->
<!--Tester: @leiyuqian-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=279f58a08395cb7d60f140e1aaa1ae4b3733282e translatedAt=2026-06-11T08:16:21.253Z pushedAt=2026-06-11T12:37:24.979Z -->

## Module Overview

The **PermissionRequestResult** module defines the permission request result returned by [requestPermissionsFromUser](js-apis-abilityAccessCtrl.md#requestpermissionsfromuser9).

> **NOTE**
>
> - The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - The APIs of this module can be used only in the stage model.

## Modules to Import

```ts
import { PermissionRequestResult } from '@kit.AbilityKit';
```

## Properties

**System capability**: The system capability of the following items is SystemCapability.Security.AccessToken.

| Name| Type| Read Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| permissions | Array&lt;string&gt; | No | No | Array of permissions to be requested this time. **Atomic service API:** Starting from API version 11, this API supports use in atomic services. |
| authResults | Array&lt;number&gt; | No | No | Authorization result corresponding to each requested permission.<br>- -1: Not authorized. Starting from API version 12, you can combine this with dialogShownResults to further determine the reason: if dialogShownResults is true, it means the user explicitly denied the request this time; if false, it means the current state does not require a dialog to be shown, and the user usually needs to go to system settings to make changes.<br>- 0: Authorized, the application can continue to access protected resources associated with this permission.<br>- 2: Invalid request, usually indicating that the permission is not declared, the permission name is invalid, or the special request conditions for this permission are not met. Developers should check the permission name, the permission declaration in module.json, and the request conditions for the corresponding permission.<br> **Atomic service API:** Starting from API version 11, this API supports use in atomic services. |
| dialogShownResults<sup>12+</sup> | Array&lt;boolean&gt; | No | Yes | Indicates whether an authorization dialog was actually shown for each permission during this request process.<br>- true: The system has shown the authorization dialog.<br>- false: The system did not show a dialog, usually because the current permission state, permission type, or system policy does not allow proceeding with the dialog authorization path.<br>When authResults is -1, combining it with this field can further distinguish between "rejected by the user this time" and "dialog is no longer shown currently". If this field is not returned, it means this result does not include the authorization dialog display status.<br> **Atomic service API:** Starting from API version 12, this API supports use in atomic services. |
| errorReasons<sup>18+</sup> | Array&lt;number&gt; | No | Yes | Reason code corresponding to each permission request. Mainly used to explain the specific reasons for authorization failure, invalid request, or inability to show a dialog. If this field is not returned, it means this result does not include reason codes.<br>- 0: This request is valid.<br>- 1: Invalid permission name, please check the permission name format and value.<br>- 2: Permission not declared, please declare this permission in module.json.<br>- 3: The request conditions for the corresponding permission are not met, for example, some location permissions require additional prerequisites. Currently only applies to location permissions, including [ohos.permission.LOCATION](../../security/AccessToken/permissions-for-all-user.md#ohospermissionlocation) and [ohos.permission.APPROXIMATELY_LOCATION](../../security/AccessToken/permissions-for-all-user.md#ohospermissionapproximately_location).<br>- 4: The user has not agreed to the privacy statement, please guide the user to agree to the privacy statement before requesting permissions.<br>- 5: This permission does not support requesting via permission dialog; the request method may be restricted or controlled by system policy. Please use the authorization method supported by this permission.<br>- 6: This permission is of the [manual_settings](../../security/AccessToken/app-permission-mgmt-overview.md#manual_settings-manual-authorization) type and can only be authorized through the settings page. This reason code is supported starting from API version 21.<br>- 12: Service exception, please try again later.<br> **Atomic service API:** Starting from API version 18, this API supports use in atomic services. |

## Usage

PermissionRequestResult is the result object of a permission request. Developers need to first create an atManager instance, and then call the requestPermissionsFromUser method to request permissions. This method returns a PermissionRequestResult object, through which developers can determine the permission request result based on its properties. For details about the overall permission request process and atManager, see [@ohos.abilityAccessCtrl (Application Access Control)](js-apis-abilityAccessCtrl.md).

**Example**
For details about how to obtain the context in the example, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).
<!--code_no_check-->

```ts
import { abilityAccessCtrl, Context, common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Create a permission manager instance
let atManager = abilityAccessCtrl.createAtManager();
try {
  // Obtain the context within the component
  let context: Context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  // Request the camera permission
  atManager.requestPermissionsFromUser(context, ["ohos.permission.CAMERA"]).then((data) => {
      // Print the permission request result
      console.info("data permissions:" + data.permissions);
      console.info("data authResults:" + data.authResults);
      console.info("data dialogShownResults:" + data.dialogShownResults);
      // errorReasons is supported since API version 18
      if (data.errorReasons) {
          console.info("data errorReasons:" + data.errorReasons);
      }
  }).catch((err: BusinessError) => {
      console.error(`code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`catch errcode: ${error.code}, message: ${error.message}`);
}
```