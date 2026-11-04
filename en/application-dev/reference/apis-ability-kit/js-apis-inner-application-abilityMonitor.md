# AbilityMonitor

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @zexin_c-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=38b85f5f27a8079e0d38315ecf6afa70985c4501 translatedAt=2026-11-04T09:53:27.511Z pushedAt=2026-11-04T09:59:24.253Z nl=1 -->

This module provides the capability to monitor the lifecycle state changes of a specified [UIAbility](js-apis-app-ability-uiAbility.md). You can use AbilityMonitor as an input parameter of [abilityDelegator.addAbilityMonitor](../apis-test-kit/js-apis-inner-application-abilityDelegator.md#addabilitymonitor) to register the listener.

> **NOTE**
> 
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.  

## Modules to Import

```ts
import { abilityDelegatorRegistry } from '@kit.TestKit';
```

## Usage

It can be used as an input parameter of [addAbilityMonitor](../apis-test-kit/js-apis-inner-application-abilityDelegator.md#addabilitymonitor) in abilityDelegator to monitor the lifecycle state changes of a specified UIAbility.

## AbilityMonitor

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

| Name                                                        | Type    | Read Only| Optional| Description                                                        |
| ------------------------------------------------------------ | -------- | ---- | ---- | ------------------------------------------------------------ |
| abilityName                                                  | string   | No  | No  |  Name of the UIAbility object to be listened.|
| moduleName                                                  | string   | No  | Yes  | Module name of the UIAbility object.|
| onAbilityCreate | (ability: [UIAbility](js-apis-app-ability-uiAbility.md)) => void | No  | Yes  | Callback invoked when the UIAbility object is created.|
| onAbilityForeground | (ability: [UIAbility](js-apis-app-ability-uiAbility.md)) => void | No  | Yes  | Callback invoked when the UIAbility object transitions to the foreground.|
| onAbilityBackground | (ability: [UIAbility](js-apis-app-ability-uiAbility.md)) => void | No  | Yes  | Callback invoked when the UIAbility object transitions to the background.|
| onAbilityDestroy | (ability: [UIAbility](js-apis-app-ability-uiAbility.md)) => void | No  | Yes  | Callback invoked when the UIAbility object is destroyed.|
| onWindowStageCreate | (ability: [UIAbility](js-apis-app-ability-uiAbility.md)) => void | No  | Yes  | Callback invoked when a WindowStage instance is created.|
| onWindowStageRestore | (ability: [UIAbility](js-apis-app-ability-uiAbility.md)) => void | No  | Yes  | Callback invoked when the page stack is restored for the target UIAbility during cross-device migration.|
| onWindowStageDestroy | (ability: [UIAbility](js-apis-app-ability-uiAbility.md)) => void | No  | Yes  | Callback invoked when the WindowStage instance is destroyed.|

**Example**

```ts
import { abilityDelegatorRegistry } from '@kit.TestKit';
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

function onAbilityCreateCallback(data: UIAbility) {
  console.info(`onAbilityCreateCallback, data: ${JSON.stringify(data)}`);
}

let monitor: abilityDelegatorRegistry.AbilityMonitor = {
  abilityName: 'abilityname',
  moduleName: "moduleName",
  onAbilityCreate: onAbilityCreateCallback
}

let abilityDelegator: abilityDelegatorRegistry.AbilityDelegator = abilityDelegatorRegistry.getAbilityDelegator();
abilityDelegator.addAbilityMonitor(monitor, (error: BusinessError) => {
  if (error) {
    console.error(`addAbilityMonitor fail, error: ${JSON.stringify(error)}`);
  }
});
```
