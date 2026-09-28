# @ohos.app.ability.ApplicationStateChangeCallback (Application Process State Change Listener)
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @SKY2001-->
<!--Designer: @yzkp-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=83eb20b2da17b66d3089c14abb21986b856a3985 translatedAt=2026-09-03T09:55:40.817Z pushedAt=2026-09-05T10:47:30.223Z -->

The module is used to listen for state changes of the current application process. For ease of description, the term "application process" will be referred to as "process" in the following sections.

Developers can call [ApplicationContext.on('applicationStateChange')](js-apis-inner-application-applicationContext.md#applicationcontextonapplicationstatechange10) and pass in a custom ApplicationStateChangeCallback to listen for foreground/background state changes of the current process and perform corresponding operations. For example, you can count the foreground/background duration of a process, or clear the memory cache when the process moves to the background state.

> **NOTE**
>
> The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs of this module can be used only in the stage model.

## Constraints

This module allows you to listen for foreground/background state changes of the current process. If you need to listen for foreground/background state changes of the entire application, use [ApplicationStateObserver.onForegroundApplicationChanged](js-apis-inner-application-applicationStateObserver.md#applicationstateobserveronforegroundapplicationchanged).

> **NOTE**
>
> The foreground/background state of a process is different from that of an application. The differences are as follows:
> - Foreground/background state of a process: If a process contains any [UIAbility](js-apis-app-ability-uiAbility.md)/[UIExtensionAbility](js-apis-app-ability-uiExtensionAbility.md#uiextensionability) in the foreground state or a visible window, the process is considered to be in the foreground state; otherwise, it is in the background state.
> - Foreground/background state of an application: If any process under an application is in the foreground state, the application is considered to be in the foreground state; otherwise, it is in the background state.

## Modules to Import

```ts
import { ApplicationStateChangeCallback } from '@kit.AbilityKit';
```

## ApplicationStateChangeCallback.onApplicationForeground

onApplicationForeground(): void

Called when the current process switches from the background to the foreground. When this callback is triggered, it does not mean that the process is already fully in the foreground state, but rather that it is about to enter the foreground state. At this point, operations that depend on the foreground state (such as launching another UIAbility) cannot be performed.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.AbilityCore

**Example**

For details, see [onApplicationBackground](#applicationstatechangecallbackonapplicationbackground).

## ApplicationStateChangeCallback.onApplicationBackground

onApplicationBackground(): void

Called when the current process switches from the foreground to the background. When this callback is triggered, the process is fully in the background state, and you can perform operations suitable for the background state (for example, clearing memory caches).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.AbilityRuntime.AbilityCore

**Example**

```ts
import { UIAbility, ApplicationStateChangeCallback } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let applicationStateChangeCallback: ApplicationStateChangeCallback = {
  onApplicationForeground() {
    console.info('applicationStateChangeCallback onApplicationForeground');
  },
  onApplicationBackground() {
    console.info('applicationStateChangeCallback onApplicationBackground');
  }
};

export default class MyAbility extends UIAbility {
  onCreate() {
    console.info('MyAbility onCreate');
    // 1. Obtain an applicationContext object.
    let applicationContext = this.context.getApplicationContext();
    try {
      // 2. Register a listener for the current process state changes through applicationContext.
      if (applicationContext != undefined) {
        applicationContext.on('applicationStateChange', applicationStateChangeCallback);
      }
    } catch (paramError) {
      console.error(`error: ${(paramError as BusinessError).code}, ${(paramError as BusinessError).message}`);
    }
    console.info('Register applicationStateChangeCallback');
  }
  onDestroy() {
    let applicationContext = this.context.getApplicationContext();
    try {
      // 1. Unregister the listener for the current process state changes through applicationContext.
      if (applicationContext != undefined) {
        applicationContext.off('applicationStateChange', applicationStateChangeCallback);
      } 
    } catch (paramError) {
      console.error(`error: ${(paramError as BusinessError).code}, ${(paramError as BusinessError).message}`);
    }
  }
}
```
