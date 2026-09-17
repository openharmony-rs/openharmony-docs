# AbilityFirstFrameStateObserver (System API)

The module defines the observer used to listen for the first frame rendering completion event of a given ability. It is used as an input parameter of [on](arkts-ability-appmanager-on-f-sys.md#onabilityfirstframestate) to listen for the completion event.

**Since:** 12

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## onAbilityFirstFrameDrawn

```TypeScript
onAbilityFirstFrameDrawn(data: AbilityFirstFrameStateData): void
```

Called when the first frame of the ability is rendered.

**Since:** 12

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | [AbilityFirstFrameStateData](arkts-ability-abilityfirstframestatedata-i-sys.md) | Yes | Data returned after the first frame is rendered. |

**Examples**

```TypeScript
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
