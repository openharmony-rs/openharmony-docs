# @ohos.intelligentScene (Intelligent Scene)

<!--Kit: Basic Services Kit-->
<!--Subsystem: Applications-->
<!--Owner: @chenzhe123-->
<!--Designer: @wangchun-->
<!--Tester: @RayShih-->
<!--Adviser: @fang-jinxu -->

This module provides APIs for querying the DND mode status, including whether the system DND mode is enabled, whether the application is allowed to be disturbed, and so on. When a specific intelligent scene (DND mode, sleep mode, study mode, work mode, or custom mode) is enabled, the DND mode is enabled.

> **NOTE**
>
>  - The initial APIs of this module are supported since API version 23. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```js
import { intelligentScene } from '@kit.BasicServicesKit';
```

## intelligentScene.isDoNotDisturbEnabled

isDoNotDisturbEnabled(): Promise\<boolean>

Checks whether the system DND mode is enabled. This API uses a promise to return the result.

**Model constraint**: This API can be used only in the stage model.

**System capability**: SystemCapability.Applications.IntelligentScene

**Required permissions**: ohos.permission.GET_DONOTDISTURB_STATE

**Return value**

| Type            | Description                               |
| ---------------- | ----------------------------------- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** indicates that the DND mode is enabled, and **false** indicates the opposite.|

**Error codes**

For details about the error codes, see [Intelligent Scene Error Codes](errorcode-intelligentScene.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 201 | Permission denied.                              |
| 35200001 | Internal error.                            |

**Example**

```js
import { BusinessError, intelligentScene } from '@kit.BasicServicesKit';

let isDoNotDisturbEnabled: boolean | null = null;
intelligentScene.isDoNotDisturbEnabled().then((isEnabled: boolean) => {
  isDoNotDisturbEnabled = isEnabled;
  if (isEnabled) {
    console.info('DoNotDisturb state is open');
  } else {
    console.info('DoNotDisturb state is closed');
  }
}).catch((err: BusinessError) => {
  console.error(`Failed to get doNotDisturb state, code: ${err.code}, message: ${err.message}`);
});
```

## intelligentScene.isNotifyAllowedInDoNotDisturb

isNotifyAllowedInDoNotDisturb(): Promise\<boolean>

Checks whether this application is allowed to push notifications in DND mode. If the current application has been added to the allowlist, notifications will be properly pushed with ringtone and vibration in DND mode. This API uses a promise to return the result.

**Model constraint**: This API can be used only in the stage model.

**System capability**: SystemCapability.Applications.IntelligentScene

**Required permissions**: ohos.permission.GET_DONOTDISTURB_STATE

**Return value**

| Type            | Description                               |
| ---------------- | ----------------------------------- |
| Promise&lt;boolean&gt; | Promise used to return the result. If the DND mode is disabled, the value **false** is returned. If the DND mode is enabled, the check result is returned, where **true** indicates that this application is allowed to push notifications, and **false** indicates the opposite.|

**Error codes**

For details about the error codes, see [Intelligent Scene Error Codes](errorcode-intelligentScene.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 201 | Permission denied.                              |
| 35200001 | Internal error.                            |

**Example**

```js
import { BusinessError, intelligentScene } from '@kit.BasicServicesKit';

let isNotifyAllowedInDoNotDisturb: boolean | null = null;
intelligentScene.isNotifyAllowedInDoNotDisturb().then((isAllowed: boolean) => {
  isNotifyAllowedInDoNotDisturb = isAllowed;
  if (isAllowed) {
    console.info('Allowed to notify in doNotDisturb state');
  } else {
    console.info('Not allowed to notify in doNotDisturb state or doNotDisturb is closed');
  }
}).catch((err: BusinessError) => {
  console.error(`Failed to get allow state, Code:${err.code}, message:${err.message}`);
});
```
