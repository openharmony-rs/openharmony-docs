# @ohos.app.ability.autoStartupManager (Auto-Startup Management)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @zhu-feimo; @Luobniz21-->
<!--Designer: @ccllee1-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->

The autoStartupManager module provides APIs for an application to query whether it is configured to start automatically at boot time.

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
