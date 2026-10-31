# @ohos.app.ability.autoStartupManager (Auto-Startup Management)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @zhu-feimo; @Luobniz21-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=1e2bfcc9b4f85d9126c23f626a7a73b4bb891227 translatedAt=2026-09-03T10:02:37.805Z pushedAt=2026-09-05T10:47:30.249Z -->

The autoStartupManager module provides the capabilities to obtain the auto-start on boot status of the current application and check whether the device supports auto-start on boot.

> **NOTE**
>
> The initial APIs of this module are supported since API version 21. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs of this module can be used only in the stage model.

## Modules to Import

```ts
import { autoStartupManager } from '@kit.AbilityKit';
```

## autoStartupManager.getAutoStartupStatusForSelf

getAutoStartupStatusForSelf(): Promise\<boolean\>

Checks whether the current application is enabled for automatic startup at boot time. This API uses a promise to return the result.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Device behavior differences**: This API can be properly called only on phones, PC/2-in-1 devices, tablets, and wearables. On other devices, it returns the error code 801.

**Return value**

| Type                                         | Description                                 |
| -------- | -------------------------------------------- |
| Promise\<boolean\> | Promise used to return the auto-startup status. **true** if enabled for automatic startup at boot time, **false** otherwise.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 801      | Capability not supported.|
| 16000050 | Internal error. Possible causes: 1. Connect to system service failed; 2.System service failed to communicate with dependency module.|

**Example**

```ts
import { autoStartupManager, UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  onForeground() {
    try {
      // Obtains the auto-start on boot status of the current application.
      autoStartupManager.getAutoStartupStatusForSelf().then((isAutoStartup: boolean) => {
        console.info(`getAutoStartupStatusForSelf success, isAutoStartup: ${JSON.stringify(isAutoStartup)}.`);
      }).catch((err: BusinessError) => {
        console.error(`getAutoStartupStatusForSelf failed, err code: ${err.code}, err msg: ${err.message}.`);
      });
    } catch (err) {
      let code = (err as BusinessError).code;
      let msg = (err as BusinessError).message;
      console.error(`getAutoStartupStatusForSelf failed, err code: ${code}, err msg: ${msg}.`);
    }
  }
}
```

## autoStartupManager.isAutoStartupSupported

isAutoStartupSupported(): boolean

Checks whether the current device supports auto-start on boot.

> **NOTE**
>
> It is recommended that you call this API to check the device capability before calling [autoStartupManager.getAutoStartupStatusForSelf](#autostartupmanagergetautostartupstatusforself). If false is returned, the current device does not support auto-start on boot.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since:** 26.0.0

**Return value**

| Type | Description |
| -------- | -------------------------------------------- |
| boolean | Whether the current device supports auto-start on boot. The value true means that auto-start on boot is supported, and false means the opposite. |

**Example**

```ts
import { autoStartupManager, UIAbility } from '@kit.AbilityKit';

export default class EntryAbility extends UIAbility {
  onCreate() {
    // Check whether the current device supports auto-start on boot.
    const isSupported: boolean = autoStartupManager.isAutoStartupSupported();
    console.info(`isAutoStartupSupported: ${isSupported}.`);
  }
}
```