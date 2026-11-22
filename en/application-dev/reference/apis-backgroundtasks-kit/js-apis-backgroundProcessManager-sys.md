# @ohos.resourceschedule.backgroundProcessManager (Background Child Process Management) (System API)

<!--Kit: Background Tasks Kit-->
<!--Subsystem: Resourceschedule-->
<!--Owner: @xufu7-->
<!--Designer: @zhouben25-->
<!--Tester: @leetestnady-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=55df9c11d6d7c450cc6d9d1ac7b0b998394459f6 translatedAt=2026-11-03T03:25:30.231Z pushedAt=2026-11-03T06:02:48.946Z nl=1 -->

This module provides APIs for background child process management. You can use these APIs to suppress and unsuppress child processes to prevent child processes from occupying too many system resources and causing freezes. The APIs take effect only for the child processes created through [OH_Ability_StartNativeChildProcess](../apis-ability-kit/capi-native-child-process-h.md#oh_ability_startnativechildprocess).

> **NOTE**
>
> This page contains only the system APIs of this module. For other public APIs, see [@ohos.resourceschedule.backgroundProcessManager (Background Child Process Management)](js-apis-backgroundProcessManager.md).

**Since:** 26.0.1

## Modules to Import

```ts
import { backgroundProcessManager } from '@kit.BackgroundTasksKit';
```

## backgroundProcessManager.clearBackgroundApps

clearBackgroundApps(clearType: ClearType): Promise\<void>;

Clears background resources proactively. This API uses a promise to return the result.

**Since:** 26.0.1

**Required permissions:** ohos.permission.CLEAR_BACKGROUND_APPS

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Resourceschedule.BackgroundProcessManager

**System API**: This is a system API.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| clearType | [ClearType](#cleartype) | Yes | Type of the resources to clear. |

**Return value**

| Type           | Description                     |
| -------------- | ------------------------ |
| Promise\<void> | Promise that returns no value. |

**Error codes**

For details about the error codes, see [backgroundProcessManager Error Codes](errorcode-backgroundProcessManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                     |
| -------- | ---------------------------- |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 202      | Permission verification failed. A non-system application calls a system API. |
| 31800002 | Parameter error. |

**Example**

``` ts
import { backgroundProcessManager } from '@kit.BackgroundTasksKit';
import { BusinessError } from '@kit.BasicServicesKit';

backgroundProcessManager.clearBackgroundApps(backgroundProcessManager.ClearType.CLEAR_RECENT_CARDS).then(() => {
  console.info('clearBackgroundApps succeed');
}).catch((err: BusinessError) => {
  console.error('promise err code:' + err.code + ' message:' + err.message);
});
```


## ClearType

Enumerates the resource cleanup types.

**Since:** 26.0.1

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Resourceschedule.BackgroundProcessManager

**System API**: This is a system API.

| Name | Value | Description |
| -------- | -------- | -------- |
| CLEAR_RECENT_CARDS  | 1 | Clears the recent task cards. |
