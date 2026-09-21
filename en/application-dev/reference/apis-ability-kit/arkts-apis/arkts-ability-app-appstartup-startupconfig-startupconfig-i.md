# StartupConfig

```TypeScript
export default interface StartupConfig
```

The module defines the configuration of [AppStartup](../../../application-models/app-startup.md).

**Since:** 12

**System capability:** SystemCapability.Ability.AppStartup

## Modules to Import

```TypeScript
import { StartupConfig } from '@kit.AbilityKit';
```

## startupListener

```TypeScript
startupListener?: StartupListener
```

AppStartup listener, which is called when all the startup tasks are complete.

**Type:** [StartupListener](arkts-ability-app-appstartup-startuplistener-startuplistener-c.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AppStartup

## timeoutMs

```TypeScript
timeoutMs?: number
```

Timeout for executing all startup tasks, measured in ms. The default value is 10000 ms.

**Type:** number

**Default:** 10000

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AppStartup

**Examples**

```TypeScript
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
