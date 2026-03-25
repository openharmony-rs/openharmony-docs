# @ohos.app.ability.kioskManager (Kiosk Mode Management)
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @zhu-feimo-->
<!--Designer: @ccllee1-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->

The KioskManager module provides APIs to manage kiosk mode, including entering and exiting kiosk mode.

Kiosk mode is a dedicated device lockdown mode that ensures the device UI serves only specific interaction scenarios. In this mode, device usage is confined to predetermined applications. A typical example is a bank ATM, where users can only interact with the ATM software and cannot exit it or access any other functions.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 20. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - The APIs of this module can be used only in the stage model.
> - The APIs of this module are available only to applications that have been configured to support Kiosk mode via [setAllowedKioskApps](../apis-mdm-kit/js-apis-enterprise-applicationManager.md#applicationmanagersetallowedkioskapps20).

## Modules to Import

```ts
import { kioskManager } from '@kit.AbilityKit';
```

## kioskManager.enterKioskMode

enterKioskMode(context: UIAbilityContext): Promise&lt;void&gt;

Enters kiosk mode. This API uses a promise to return the result.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Device behavior differences**: This API can be properly called only on phones, PC/2-in-1 devices, and tablets. On other devices, it returns the error code 801.

**Parameters**

| Name| Type| Mandatory| Description|
|--------|------|------|------|
| context | [UIAbilityContext](../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md) | Yes| Context of the UIAbility that needs to enter kiosk mode.|

**Return value**

| Type| Description|
|------|------|
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
|---------|---------|
| 801 | Capability not supported. |
| 16000050 | Failed to connect to the system service. |
| 16000110 | The current application is not in Kiosk app list and cannot enter Kiosk mode. |
| 16000111 | The system is already in Kiosk mode and cannot enter Kiosk mode again. |
| 16000113 | Current ability is not in foreground. |

**Example**

```ts
import { common, kioskManager } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  private uiAbilityContext: common.UIAbilityContext | undefined =
    this.getUIContext().getHostContext() as common.UIAbilityContext;

  build() {
    Column() {
      Button('enterKioskMode').margin({ top: 30 })
        .onClick(() => {
          kioskManager.enterKioskMode(this.uiAbilityContext)
            .then(() => {
              hilog.info(0x0000, 'testTag', '%{public}s', 'enterKioskMode success');
            })
            .catch((error: BusinessError) => {
              hilog.error(0x0000, 'testTag', '%{public}s', `enterKioskMode failed:${JSON.stringify(error)}`);
            });
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

## kioskManager.exitKioskMode

exitKioskMode(context: UIAbilityContext): Promise&lt;void&gt;

Exits kiosk mode. This API uses a promise to return the result.

This API takes effect only for applications that have entered kiosk mode.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Device behavior differences**: This API can be properly called only on phones, PC/2-in-1 devices, and tablets. On other devices, it returns the error code 801.

**Parameters**

| Name| Type| Mandatory| Description|
|--------|------|------|------|
| context | [UIAbilityContext](../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md) | Yes| Context of the UIAbility that needs to exit kiosk mode.|

**Return value**

| Type| Description|
|------|------|
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ability Error Codes](errorcode-ability.md).

| ID| Error Message|
|---------|---------|
| 801 | Capability not supported. |
| 16000050 | Failed to connect to the system service. |
| 16000110 | The current application is not in Kiosk app list and cannot enter Kiosk mode. |
| 16000112 | The current application is not in Kiosk mode and cannot exit Kiosk mode. |

**Example**

```ts
import { common, kioskManager } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  private uiAbilityContext: common.UIAbilityContext | undefined =
    this.getUIContext().getHostContext() as common.UIAbilityContext;

  build() {
    Column() {
      Button('exitKioskMode').margin({ top: 10 })
        .onClick(() => {
          kioskManager.exitKioskMode(this.uiAbilityContext)
            .then(() => {
              hilog.info(0x0000, 'testTag', '%{public}s', 'exitKioskMode success');
            })
            .catch((error: BusinessError) => {
              hilog.error(0x0000, 'testTag', '%{public}s', `exitKioskMode failed:${JSON.stringify(error)}`);
            });
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

## KioskStatus

type KioskStatus = _KioskStatus

Defines the kiosk status information, including whether the system is in kiosk mode and the information about the application in kiosk mode.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Type| Description|
| --- | --- |
| [_KioskStatus](js-apis-application-KioskStatus.md#kioskstatus) | Kiosk status information, including whether the system is in kiosk mode and the information about the application in kiosk mode.|
