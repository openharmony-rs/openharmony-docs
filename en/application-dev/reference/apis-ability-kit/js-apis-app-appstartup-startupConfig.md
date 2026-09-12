# @ohos.app.appstartup.StartupConfig (AppStartup Configuration)
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @yzkp-->
<!--Designer: @yzkp-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=83eb20b2da17b66d3089c14abb21986b856a3985 translatedAt=2026-09-03T10:45:08.120Z pushedAt=2026-09-05T10:47:30.475Z -->

This module provides the definition of configuration information for the [application startup framework](../../application-models/app-startup.md), which is used to configure the task timeout and the listener of the startup framework.

> **NOTE**
>
> The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs of this module can be used only in the stage model.

## Modules to Import

```js
import { StartupConfig } from '@kit.AbilityKit';
```

## StartupConfig

Describes the timeout duration and listener of startup tasks in AppStartup. For details, see [Setting Startup Parameters](../../application-models/app-startup.md#setting-startup-parameters).

**System capability**: SystemCapability.Ability.AppStartup

| Name| Type| Read Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| timeoutMs | number | No | Yes | Timeout duration for executing all startup tasks, in ms. The default value is **10000**. When the timeout expires, the startup framework stops waiting and returns a timeout error through the **startupListener.onCompleted** callback. The timeout does not interrupt the startup tasks being executed, but affects the execution of subsequent tasks. |
| startupListener | [StartupListener](./js-apis-app-appstartup-startupListener.md) | No | Yes | Listener of the startup framework, which is invoked when all startup tasks are complete. If this parameter is not set, no callback notification is sent. |

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
