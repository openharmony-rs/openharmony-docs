# isImmersiveMaterialSupported

## Modules to Import

```TypeScript
import { uiMaterial } from '@kit.ArkUI';
```

## isImmersiveMaterialSupported

```TypeScript
function isImmersiveMaterialSupported(): boolean
```

Check whether [ImmersiveMaterial](arkts-arkui-uimaterial-immersivematerial-c.md) is supported on the current device. If it is true, the ImmersiveMaterial object can be used in the systemMaterial attribute. If it is false, setting the ImmersiveMaterial object in the systemMaterial attribute will not take effect. It is defined by the device and cannot be modified.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the current device supports ImmersiveMaterial. The value true indicates that the current device supports ImmersiveMaterial, and false indicates the opposite. |
