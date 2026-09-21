# @ohos.app.ability.appRecovery(Application Recovery)

The appRecovery module provides APIs for recovering faulty applications.

**Since:** 9

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import

```TypeScript
import { appRecovery } from '@kit.AbilityKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [enableAppRecovery](arkts-ability-apprecovery-enableapprecovery-f.md) | Enables application recovery. After this API is called, the first ability that is displayed when the application is started from the initiator can be restored. |
| [restartApp](arkts-ability-apprecovery-restartapp-f.md) | Restarts the current process and starts the first ability that is displayed when the application is started. If the state of this ability is saved, the saved state data is passed into the **wantParam** property in the **want** parameter of the **onCreate** lifecycle callback of the ability. |
| [saveAppState](arkts-ability-apprecovery-saveappstate-f.md#saveappstate) | Saves the application state. This API can be used together with the APIs of [errorManager](arkts-ability-app-ability-errormanager.md). |
| [saveAppState](arkts-ability-apprecovery-saveappstate-f.md#saveappstate-1) | Saves the ability state, which will be used for recovery. This API can be used together with the APIs of [errorManager](arkts-ability-app-ability-errormanager.md). |
| [setRestartWant](arkts-ability-apprecovery-setrestartwant-f.md) | Sets an ability that will be recovered. The ability must be a UIAbility in the current bundle. |

### Enums

| Name | Description |
| --- | --- |
| [RestartFlag](arkts-ability-apprecovery-restartflag-e.md) | Enumerates the application restart flags. This enum is used as an input parameter of [enableAppRecovery](arkts-ability-apprecovery-enableapprecovery-f.md). |
| [SaveModeFlag](arkts-ability-apprecovery-savemodeflag-e.md) | Enumerates the application state saving modes. This enum is used as an input parameter of [enableAppRecovery](arkts-ability-apprecovery-enableapprecovery-f.md). |
| [SaveOccasionFlag](arkts-ability-apprecovery-saveoccasionflag-e.md) | Enumerates the scenarios for saving the application state. This enum is used as an input parameter of [enableAppRecovery](arkts-ability-apprecovery-enableapprecovery-f.md). |
