# @ohos.app.appstartup.StartupConfigEntry (AppStartup Configuration Entry)
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @yzkp-->
<!--Designer: @yzkp-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->


The module provides the capability to configure [AppStartup](../../application-models/app-startup.md).

> **NOTE**
>
> The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs of this module can be used only in the stage model.

## Modules to Import

```ts
import { StartupConfigEntry } from '@kit.AbilityKit';
```

## StartupConfigEntry

### onConfig

onConfig?(): StartupConfig

Called if the HAP of the AbilityStage has [defined the AppStartup configuration file](../../application-models/app-startup.md#defining-an-appstartup-configuration-file). This callback is triggered before [AbilityStage.onCreate](js-apis-app-ability-abilityStage.md#oncreate).

You can set the AppStartup configuration within this callback. For details, see [Setting Startup Parameters](../../application-models/app-startup.md#setting-startup-parameters).

**System capability**: SystemCapability.Ability.AppStartup

**Return value**

| Type| Description|
| -------- | -------- |
| [StartupConfig](js-apis-app-appstartup-startupConfig.md#startupconfig) | AppStartup configuration.|

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
        hilog.info(0x0000, 'testTag', 'onCompletedCallback: %{public}d, message: %{public}s', error.code,
          error.message);
      } else {
        hilog.info(0x0000, 'testTag', `onCompletedCallback: success.`);
      }
    }
    let startupListener: StartupListener = {
      'onCompleted': onCompletedCallback
    }
    let config: StartupConfig = {
      'timeoutMs': 10000,
      'startupListener': startupListener
    }
    return config;
  }
}
```
