# restartApp

## Modules to Import

```TypeScript
import { appRecovery } from '@kit.AbilityKit';
```

## restartApp

```TypeScript
function restartApp(): void
```

Restarts the current process and starts the first ability that is displayed when the application is started. If the state of this ability is saved, the saved state data is passed into the **wantParam** property in the **want** parameter of the **onCreate** lifecycle callback of the ability.

In API version 10, the ability specified by [setRestartWant](arkts-ability-apprecovery-setrestartwant-f.md) is started. If no ability is specified, the following rules are used:

If the ability of the current application running in the foreground supports recovery, that ability is started.

If multiple abilities that support recovery is running in the foreground, only the last ability is started.

If no ability is running in the foreground, none of them is started.

This API can be used together with the APIs of [errorManager](arkts-ability-app-ability-errormanager.md). The interval between two restarts must be greater than one minute. If this API is called repeatedly within one minute, the application exits but does not restart. The behavior of automatic restart is the same as that of proactive restart.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Examples**

```TypeScript
import { appRecovery, errorManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let observer: errorManager.ErrorObserver = {
  onUnhandledException(errorMsg) {
    console.error('onUnhandledException, errorMsg: ', errorMsg);
    appRecovery.restartApp();
  }
};

try {
  errorManager.on('error', observer);
} catch (paramError) {
  console.error(`error: ${(paramError as BusinessError).code}, ${(paramError as BusinessError).message}`);
}
```
