# StartupConfig

```TypeScript
export default interface StartupConfig
```

The module defines the configuration of [AppStartup](../../../application-models/app-startup.md).

**Since:** 12

<!--Device-unnamed-export default interface StartupConfig--><!--Device-unnamed-export default interface StartupConfig-End-->

**System capability:** SystemCapability.Ability.AppStartup

## Modules to Import

```TypeScript
import { StartupConfig } from '@kit.AbilityKit';
```

## startupListener

```TypeScript
startupListener?: StartupListener
```

Listener of the startup framework, which is invoked when all startup tasks are complete. If this parameter is not set, no callback notification is sent.

**Type:** [StartupListener](arkts-ability-app-appstartup-startuplistener-startuplistener-c.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-StartupConfig-startupListener?: StartupListener--><!--Device-StartupConfig-startupListener?: StartupListener-End-->

**System capability:** SystemCapability.Ability.AppStartup

## timeoutMs

```TypeScript
timeoutMs?: number
```

Timeout duration for executing all startup tasks, in ms. The default value is 10000. When the timeout expires, the startup framework stops waiting and returns a timeout error through the startupListener.onCompleted callback. The timeout does not interrupt the startup tasks being executed, but affects the execution of subsequent tasks.

**Type:** number

**Default:** 10000

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-StartupConfig-timeoutMs?: int--><!--Device-StartupConfig-timeoutMs?: int-End-->

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
