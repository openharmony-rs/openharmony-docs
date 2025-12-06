# @ohos.app.ability.kioskManager (Kiosk Mode Management) (System APIs)
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @zhu-feimo-->
<!--Designer: @ccllee1-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->

The KioskManager module provides APIs to manage kiosk mode, including entering/exiting kiosk mode and querying the kiosk mode status.

Kiosk mode is a dedicated device lockdown mode that ensures the device UI serves only specific interaction scenarios. In this mode, device usage is confined to predetermined applications. A typical example is a bank ATM, where users can only interact with the ATM software and cannot exit it or access any other functions.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 20. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - The APIs of this module can be used only in the stage model.
> - This topic describes only system APIs provided by the module. For details about its public APIs, see [@ohos.app.ability.kioskManager (Kiosk Mode Management)](js-apis-app-ability-kioskManager.md).

## Modules to Import

```ts
import { kioskManager } from '@kit.AbilityKit';
```

## kioskManager.getKioskStatus

getKioskStatus(): Promise&lt;KioskStatus&gt;

Obtains the Kiosk mode status information, including whether the system is in kiosk mode, and the name and UID of the application that has entered Kiosk mode. This API uses a promise to return the result.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**System API**: This is a system API.

**Device behavior differences**: This API can be properly called only on 2-in-1 devices and tablets. If it is called on other device types, error code 801 is returned.

**Return value**

| Type| Description|
|------|------|
| Promise&lt;[KioskStatus](./js-apis-app-ability-kioskManager.md#kioskstatus)&gt; | Promise used to return the kiosk mode status information.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
|---------|---------|
| 202 | Not system application. |
| 801 | Capability not supported. |
| 16000050 | Failed to connect to the system service. |

**Example**

```ts
import { kioskManager } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    Column() {
      Button('getKioskInfo').margin({ top: 10 })
        .onClick(() => {
          kioskManager.getKioskStatus()
            .then((data: kioskManager.KioskStatus) => {
              hilog.info(0x0000, 'testTag', '%{public}s', `getKioskinfo success: ${JSON.stringify(data)}`);
            })
            .catch((error: BusinessError) => {
              hilog.error(0x0000, 'testTag', '%{public}s', `getKioskinfo failed:${JSON.stringify(error)}`);
            });
        })
    }
    .height('100%')
    .width('100%')
  }
}
```
