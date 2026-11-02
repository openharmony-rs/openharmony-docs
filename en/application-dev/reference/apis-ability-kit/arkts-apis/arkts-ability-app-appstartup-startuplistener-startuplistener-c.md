# StartupListener

```TypeScript
declare class StartupListener
```

The module defines the task listener used in [App Startup](../../../application-models/app-startup.md).

**Since:** 12

<!--Device-unnamed-declare class StartupListener--><!--Device-unnamed-declare class StartupListener-End-->

**System capability:** SystemCapability.Ability.AppStartup

## Modules to Import

```TypeScript
import { StartupListener } from '@kit.AbilityKit';
```

## onCompleted

```TypeScript
onCompleted?(error: BusinessError<void>): void
```

Called when all startup tasks complete.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-StartupListener-onCompleted?(error: BusinessError<void>): void--><!--Device-StartupListener-onCompleted?(error: BusinessError<void>): void-End-->

**System capability:** SystemCapability.Ability.AppStartup

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| error | [BusinessError](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-businesserror-i.md)&lt;void&gt; | Yes | Error information of the startup task execution. On success, error is null. On failure, it contains an error code and an error description. You can obtain the error code through error.code and the error description through error.message. Possible error codes include 28800001, 28800002, 28800003, and 28800004. For details about the error causes and handling measures, see Ability Subsystem Error Codes. |

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
