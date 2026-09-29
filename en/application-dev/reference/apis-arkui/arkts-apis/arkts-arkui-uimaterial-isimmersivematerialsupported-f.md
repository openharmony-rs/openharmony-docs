# isImmersiveMaterialSupported

## Modules to Import

```TypeScript
import { uiMaterial } from '@kit.ArkUI';
```

## isImmersiveMaterialSupported

```TypeScript
function isImmersiveMaterialSupported(): boolean
```

Checks whether the current device supports immersive system materials ([ImmersiveMaterial](arkts-arkui-uimaterial-immersivematerial-c.md)). This configuration item is defined by the device and cannot be modified.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-uiMaterial-function isImmersiveMaterialSupported(): boolean--><!--Device-uiMaterial-function isImmersiveMaterialSupported(): boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the current device supports immersive materials. The value **true** indicates that the current device supports immersive materials, and **false** indicates the opposite. |
