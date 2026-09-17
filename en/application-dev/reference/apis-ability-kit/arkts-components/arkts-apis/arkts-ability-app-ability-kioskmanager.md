# @ohos.app.ability.kioskManager

The KioskManager module provides APIs to manage kiosk mode, including entering/exiting kiosk mode and querying the kiosk mode status.

Kiosk mode is a dedicated device lockdown mode that ensures the device UI serves only specific interaction scenarios. In this mode, device usage is confined to predetermined applications. A typical example is a bank ATM, where users can only interact with the ATM software and cannot exit it or access any other functions.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import

```TypeScript
import { kioskManager } from '@kit.AbilityKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [enterKioskMode](arkts-ability-kioskmanager-enterkioskmode-f.md) | Enters kiosk mode. This API uses a promise to return the result. This API can be properly called only on phones, PC/2-in-1 devices, and tablets. On other devices, it returns the error code 801. |
| [exitKioskMode](arkts-ability-kioskmanager-exitkioskmode-f.md) | Exits kiosk mode. This API uses a promise to return the result. This API takes effect only for applications that have entered kiosk mode. This API can be properly called only on phones, PC/2-in-1 devices, and tablets. On other devices, it returns the error code 801. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [getKioskStatus](arkts-ability-kioskmanager-getkioskstatus-f-sys.md) | Obtains the Kiosk mode status information, including whether the system is in kiosk mode, and the name and UID of the application that has entered Kiosk mode. This API uses a promise to return the result. |
<!--DelEnd-->

### Types

| Name | Description |
| --- | --- |
| [KioskStatus](arkts-ability-kioskmanager-kioskstatus-t.md) | Defines the kiosk status information, including whether the system is in kiosk mode and the information about the application in kiosk mode. |
