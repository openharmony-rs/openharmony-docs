# enableAppRecovery

## Modules to Import

```TypeScript
import { appRecovery } from '@kit.AbilityKit';
```

## enableAppRecovery

```TypeScript
function enableAppRecovery(restart?: RestartFlag, saveOccasion?: SaveOccasionFlag, saveMode?: SaveModeFlag) : void
```

Enables application recovery. After this API is called, the first ability that is displayed when the application is started from the initiator can be restored.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| restart | [RestartFlag](arkts-ability-apprecovery-restartflag-e.md) | No | Whether the application is restarted upon a fault. By default, the application is restarted. |
| saveOccasion | [SaveOccasionFlag](arkts-ability-apprecovery-saveoccasionflag-e.md) | No | Scenario for saving the application state. By default, the state is saved when a fault occurs. |
| saveMode | [SaveModeFlag](arkts-ability-apprecovery-savemodeflag-e.md) | No | Application state saving mode. By default, the application state is written to the local file cache. |

**Examples**

```TypeScript
import { appRecovery, AbilityStage } from '@kit.AbilityKit';

export default class MyAbilityStage extends AbilityStage {
  onCreate() {
    appRecovery.enableAppRecovery(
      appRecovery.RestartFlag.ALWAYS_RESTART,
      appRecovery.SaveOccasionFlag.SAVE_WHEN_ERROR,
      appRecovery.SaveModeFlag.SAVE_WITH_FILE
    );
  }
}
```
