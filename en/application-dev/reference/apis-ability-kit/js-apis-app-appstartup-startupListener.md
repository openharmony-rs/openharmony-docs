# @ohos.app.appstartup.StartupListener (AppStartup Task Listener)
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @yzkp-->
<!--Designer: @yzkp-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=a914ec5c20531defc3768aa8242b62bbe2d1d08f translatedAt=2026-09-03T10:45:58.875Z pushedAt=2026-09-05T10:47:30.479Z -->


StartupListener is used to listen for the execution status of startup tasks in the [application startup framework](../../application-models/app-startup.md). It supports obtaining the startup task completion notification and exception information through the onCompleted callback.

> **NOTE**
>
> The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs of this module can be used only in the stage model.

## Modules to Import

```ts
import { StartupListener } from '@kit.AbilityKit';
```

## StartupListener.onCompleted

onCompleted?(error: BusinessError\<void\>): void

Called when all startup tasks are executed.

**System capability**: SystemCapability.Ability.AppStartup

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| error | [BusinessError\<void>](../apis-basic-services-kit/js-apis-base.md#businesserror) | Yes | Error information of the startup task execution. On success, error is null. On failure, it contains an error code and an error description. You can obtain the error code through error.code and the error description through error.message. Possible error codes include 28800001, 28800002, 28800003, and 28800004. For details about the error causes and handling measures, see [Ability Subsystem Error Codes](errorcode-ability.md). |

**Example**

```ts
import { StartupConfig, StartupConfigEntry, StartupListener } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

export default class MyStartupConfigEntry extends StartupConfigEntry {
  onConfig() {
    hilog.info(0x0000, 'testTag', `onConfig`);
    let onCompletedCallback = (error: BusinessError<void>) => {
      hilog.info(0x0000, 'testTag', `onCompletedCallback`);
      if (error) {
        hilog.error(0x0000, 'testTag', 'onCompletedCallback: %{public}d, message: %{public}s', error.code,
          error.message);
      } else {
        hilog.info(0x0000, 'testTag', `onCompletedCallback: success.`);
      }
    };
    let startupListener: StartupListener = {
      'onCompleted': onCompletedCallback
    };
    let config: StartupConfig = {
      'timeoutMs': 10000,
      'startupListener': startupListener
    };
    return config;
  }
}
```
