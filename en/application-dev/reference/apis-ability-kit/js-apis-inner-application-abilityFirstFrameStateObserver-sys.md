# AbilityFirstFrameStateObserver (System API)
<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @zhu-feimo-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=e2c3267fc728379ed661f6395560cc18d085c54a translatedAt=2026-09-03T11:34:11.113Z pushedAt=2026-09-05T10:47:30.647Z -->

The module defines the observer used to listen for the first frame rendering completion event of a given ability. It is used as an input parameter of [on](js-apis-app-ability-appManager-sys.md#appmanageronabilityfirstframestate12) to listen for the completion event.

> **NOTE**
>
> The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> The APIs provided by this module are system APIs.

## Modules to Import

```ts
import { appManager } from '@kit.AbilityKit';
```

## AbilityFirstFrameStateObserver

### onAbilityFirstFrameDrawn

onAbilityFirstFrameDrawn(data: AbilityFirstFrameStateData): void

Called when the first frame of the ability is rendered.

**System API**: This is a system API.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| data | [AbilityFirstFrameStateData](js-apis-inner-application-abilityFirstFrameStateData-sys.md) | Yes| Data returned after the first frame is rendered.|

**Example**

```ts
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Create an Ability first frame drawing state listener object.
let observer: appManager.AbilityFirstFrameStateObserver = {
  onAbilityFirstFrameDrawn(data: appManager.AbilityFirstFrameStateData) {
    console.info(`onAbilityFirstFrameDrawn success, abilityFirstFrameStateData: ${data}.`);
  }
};

try {
  // Register the listener for the Ability first frame drawing completion event.
  appManager.on('abilityFirstFrameState', observer);
} catch (e) {
  let code = (e as BusinessError).code;
  let msg = (e as BusinessError).message;
  console.error(`appmanager.on failed, err code: ${code}, err msg: ${msg}.`);
}
```
