# Querying and Requesting Permissions to Control a Target Application

<!--Kit: Ability Kit-->
<!--Subsystem: Security-->
<!--Owner: @gcw_3MIoLA9y-->
<!--Designer: @wkr321_ent-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=ee3646b2ac8dc8dfc90ec5c9facb07df160a93db translatedAt=2026-11-20T03:32:09.892Z pushedAt=2026-11-20T06:10:27.011Z nl=1 -->

Starting from API version 26.1.0, the Secure Access Fence Service provides the capability to query and request the control permission of a target application.

The system control agent manipulates the behavior of a target application through methods such as simulated clicks, and provides a mechanism for querying and requesting the control permission. The agent can first query the control permission state of the target application. If the state is DENY, it then requests control authorization from the user, ensuring that only applications authorized by the user can control the target application.

## Basic Concepts

- **Application control permission:** The authorization that allows an external tool to perform control operations on a specified application. The state is ALLOW or DENY, and is decided by the user.
- **Cloned app:** A multi-instance of an application, distinguished by the `index` field of [AppInfo](../../reference/apis-ability-kit/js-apis-abilityToolAccessCtrl.md#appinfo). A value of 0 indicates the main application, and a value greater than 0 indicates a cloned app.

## Implementation Principle

1. Call [queryControlAppStatus()](../../reference/apis-ability-kit/js-apis-abilityToolAccessCtrl.md#abilitytoolaccessctrlquerycontrolappstatus) and pass in the application information list. The API returns the control permission state (ALLOW or DENY) of each application.
2. If the state is ALLOW, subsequent control operations can be performed directly. If the state is DENY, call [requestControlAppPermissionFromUser()](../../reference/apis-ability-kit/js-apis-abilityToolAccessCtrl.md#abilitytoolaccessctrlrequestcontrolapppermissionfromuser) and pass in the context and the application information list to display a dialog box for requesting authorization.
3. After the user makes a decision, the API returns the final control permission state of each application.

## How to Develop

To call the APIs, request the `ohos.permission.CONTROL_DEVICE` permission. For details about how to request it, see [Declaring Permissions](../AccessToken/declare-permissions.md).

1. Import the module.

   ```typescript
   import { abilityToolAccessCtrl, common } from '@kit.AbilityKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   ```

2. Construct the application information list. For details about the parameters, see [AppInfo](../../reference/apis-ability-kit/js-apis-abilityToolAccessCtrl.md#appinfo).

   ```typescript
   let appInfo: abilityToolAccessCtrl.AppInfo[] = [{
     bundleName: 'com.example.demo',
     index: 0
   }];
   ```

3. Query the control permission state.

   ```typescript
   abilityToolAccessCtrl.queryControlAppStatus(appInfo).then((data: abilityToolAccessCtrl.ControlAppStatusResult[]) => {
     console.info('queryControlAppStatus success, data: ' + JSON.stringify(data));
     for (let i = 0; i < data.length; i++) {
       let bundleName = data[i].appInfo.bundleName;
       let status = data[i].status;
       console.info(`bundleName: ${bundleName}, status: ${status}`);
       if (status === abilityToolAccessCtrl.ControlAppStatus.DENY) {
         // The control permission is denied. In step 4, call requestControlAppPermissionFromUser() to request control authorization from the user.
       } else {
         // The state is ALLOW. Subsequent control operations can be performed directly.
       }
     }
   }).catch((err: BusinessError): void => {
     console.error(`queryControlAppStatus fail, code: ${err.code}, message: ${err.message}`);
   });
   ```

   The API returns an array of [ControlAppStatusResult](../../reference/apis-ability-kit/js-apis-abilityToolAccessCtrl.md#controlappstatusresult), where `status` is [ControlAppStatus](../../reference/apis-ability-kit/js-apis-abilityToolAccessCtrl.md#controlappstatus).ALLOW or .DENY.

4. If the state is DENY, request control authorization.

   `context` is the application context. For the FA model, see [Context](../../reference/apis-ability-kit/js-apis-inner-app-context.md). For the Stage model, see [Context](../../reference/apis-ability-kit/js-apis-inner-application-context.md). It can be obtained through `this.getUIContext().getHostContext() as common.UIAbilityContext`.

   ```typescript
   let context: Context = this.getUIContext().getHostContext() as common.UIAbilityContext;
   abilityToolAccessCtrl.requestControlAppPermissionFromUser(context, appInfo)
     .then((data: abilityToolAccessCtrl.ControlAppStatusResult[]) => {
       console.info('requestControlAppPermissionFromUser success, data: ' + JSON.stringify(data));
       for (let i = 0; i < data.length; i++) {
         let bundleName = data[i].appInfo.bundleName;
         let status = data[i].status;
         console.info(`bundleName: ${bundleName}, status: ${status}`);
       }
     })
     .catch((err: BusinessError): void => {
       console.error(`requestControlAppPermissionFromUser fail, code: ${err.code}, message: ${err.message}`);
     });
   ```

   > **NOTE**
   >
   > - 24010000: Invalid input parameter. Check whether `appInfo` is empty, whether `bundleName` is valid, and whether `context` is valid.
   > - 24010001: System service exception. Retry later.
   > - 24010002: Internal service error. Retry at intervals.
   > - For the complete list of error codes, see [Secure Access Fence Service Error Codes](../../reference/apis-ability-kit/errorcode-abilityToolAccessCtrl.md).

   <!--no_check-->
