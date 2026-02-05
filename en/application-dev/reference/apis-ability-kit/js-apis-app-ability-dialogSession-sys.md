# @ohos.app.ability.dialogSession (dialogSession) (System API)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @zhu-feimo; @Luobniz21-->
<!--Designer: @ccllee1-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->

The dialogSession module provides APIs related to the dialog box.

> **NOTE**
>
> The initial APIs of this module are supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs of this module can be used only in the stage model.
>
> The APIs provided by this module are system APIs.

## Modules to Import

```ts
import { dialogSession } from '@kit.AbilityKit';
```

## DialogAbilityInfo

Provides DialogAbility information, including the bundle name, module name, and ability name.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name| Type| Read-only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| bundleName | string | No| No| Bundle name.|
| moduleName | string | No| No| Module name.|
| abilityName | string | No| No| Ability name.|
| abilityIconId | number | No| No| ID of the ability icon.|
| abilityLabelId | number | No| No| ID of the ability label.|
| bundleIconId | number | No| No| ID of the bundle icon.|
| bundleLabelId | number | No| No| ID of the bundle label.|
| visible<sup>12+</sup> | boolean | No| No| Whether the ability is visible. **true** if visible, **false** otherwise.|
| appIndex<sup>12+</sup> | number | No| No| Index of the application clone.|
| multiAppMode<sup>12+</sup> | [MultiAppMode](./js-apis-bundleManager-applicationInfo.md#multiappmode12) | No| No| Multi-app mode.|
| codePath<sup>23+</sup> | string | No| Yes| Installation directory of the application.|
| installSource<sup>23+</sup> | string | No| Yes| Installation source of the application. The options are as follows:<br> - **pre-installed**: pre-installed application installed during the first boot.<br> - **ota**: pre-installed application added during system upgrade.<br> - **recovery**: pre-installed application manually restored by the user after uninstallation.<br> - **bundleName**: installation by the application corresponding to this bundle name. **bundleName** represents a variable, subject to the actual value.<br> - **unknown**: unknown application installation source.|

## DialogSessionInfo

Provides session information, including the requester information, target ability information list, and other parameters.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name| Type| Read-only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| callerAbilityInfo | [DialogAbilityInfo](#dialogabilityinfo)| No| No| Ability information of the requester.|
| targetAbilityInfos | Array\<[DialogAbilityInfo](#dialogabilityinfo)\> | No| No| List of target ability information.|
| parameters | Record<string, Object> | No| Yes| Other parameters.|

## getDialogSessionInfo

getDialogSessionInfo(dialogSessionId: string): [DialogSessionInfo](#dialogsessioninfo)

Obtains the session information based on the session ID.

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | dialogSessionId | string | Yes| Session ID.|

**Return value**

  | Type| Description|
  | -------- | -------- |
  | [DialogSessionInfo](#dialogsessioninfo) | Session information.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 202 | The application is not system-app, can not use system-api. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. 3. Parameter verification failed. |
| 16000005 | The specified process does not have the permission. |
| 16000006  | Cross-user operations are not allowed. |
| 16000050  | Internal error. |

**Example**
```ts
import { dialogSession, Want, UIExtensionAbility, UIExtensionContentSession } from '@kit.AbilityKit';

const TAG: string = '[testTag] UIExtAbility';

export default class UIExtAbility extends UIExtensionAbility {
  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    // want is specified by the system. dialogSessionId is a built-in parameter.
    let dialogSessionId = want?.parameters?.dialogSessionId.toString();

    // Obtain DialogSessionInfo.
    let dialogSessionInfo: dialogSession.DialogSessionInfo = dialogSession.getDialogSessionInfo(dialogSessionId);
    console.info(TAG, `onSessionCreate, want: ${JSON.stringify(want)}`);
  }
}
```

## sendDialogResult

sendDialogResult(dialogSessionId: string, targetWant: Want, isAllowed: boolean, callback: AsyncCallback\<void\>): void

Sends a request for a dialog box. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | dialogSessionId | string | Yes| Session ID.|
  | targetWant | Want | Yes| Target of the request.|
  | isAllowed | boolean | Yes| Whether the target ability can be started. **true** if allowed, **false** otherwise.|
  | callback | AsyncCallback\<void\> | Yes| Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 202 | The application is not system-app, can not use system-api. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. 3. Parameter verification failed. |
| 16000005 | The specified process does not have the permission. |
| 16000006  | Cross-user operations are not allowed. |
| 16000050  | Internal error. |

**Example**

```ts
import { dialogSession, Want, UIExtensionAbility, UIExtensionContentSession } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class UIExtAbility extends UIExtensionAbility {
  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    // want is specified by the system. dialogSessionId is a built-in parameter.
    let dialogSessionId = want?.parameters?.dialogSessionId.toString();

    // Obtain DialogSessionInfo.
    let dialogSessionInfo: dialogSession.DialogSessionInfo =
      dialogSession.getDialogSessionInfo(dialogSessionId);

    let isAllow: boolean = true;

    let targetWant: Want = {
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility'
    };

    try {
      dialogSession.sendDialogResult(dialogSessionId, targetWant, isAllow, (err, data) => {
        if (err) {
          console.error(`sendDialogResult error, errorCode: ${err.code}`);
        } else {
          console.info(`sendDialogResult success`);
        }
      });
    } catch (err) {
      console.error(`sendDialogResult error, errorCode: ${(err as BusinessError).code}`);
    }
  }
}
```

## sendDialogResult

sendDialogResult(dialogSessionId: string, targetWant: Want, isAllowed: boolean): Promise\<void\>

Sends a request for a dialog box. This API uses a promise to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

  | Name| Type| Mandatory| Description|
  | -------- | -------- | -------- | -------- |
  | dialogSessionId | string | Yes| Session ID.|
  | targetWant | Want | Yes| Target of the request.|
  | isAllowed | boolean | Yes| Whether the target ability can be started. **true** if allowed, **false** otherwise.|

**Return value**

| Type| Description|
| -------- | -------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
| ------- | -------- |
| 202 | The application is not system-app, can not use system-api. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. 3. Parameter verification failed. |
| 16000005 | The specified process does not have the permission. |
| 16000006  | Cross-user operations are not allowed. |
| 16000050  | Internal error. |

**Example**

```ts
import { dialogSession, Want, UIExtensionAbility, UIExtensionContentSession } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class UIExtAbility extends UIExtensionAbility {
  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    // want is specified by the system. dialogSessionId is a built-in parameter.
    let dialogSessionId = want?.parameters?.dialogSessionId.toString();

    // Obtain DialogSessionInfo.
    let dialogSessionInfo: dialogSession.DialogSessionInfo = dialogSession.getDialogSessionInfo(dialogSessionId);

    let isAllow: boolean = true;

    let targetWant: Want = {
      bundleName: 'com.example.myapplication',
      abilityName: 'EntryAbility'
    };

    try {
      dialogSession.sendDialogResult(dialogSessionId, targetWant, isAllow)
        .then((data) => {
          console.info(`sendDialogResult success, pid: ${data}`);
        }, (err: BusinessError) => {
          console.error(`sendDialogResult error, errorCode: ${err.code}`);
        });
    } catch (err) {
      console.error(`sendDialogResult error, errorCode: ${(err as BusinessError).code}`);
    }
  }
}
```
