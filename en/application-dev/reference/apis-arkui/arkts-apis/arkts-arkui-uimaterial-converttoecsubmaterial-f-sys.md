# convertToECSubMaterial (System API)

## Modules to Import

```TypeScript
import { uiMaterial } from '@kit.ArkUI';
```

## convertToECSubMaterial

```TypeScript
function convertToECSubMaterial(material: uiMaterial.ImmersiveMaterial) : uiMaterial.ImmersiveMaterial
```

Converts an [ImmersiveMaterial](arkts-arkui-uimaterial-immersivematerial-c.md) material into an ImmersiveMaterial material applicable to the child components of [EffectComponent](../arkts-components/arkts-arkui-effectcomponent-comp-sys.md).

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-uiMaterial-function convertToECSubMaterial(material: uiMaterial.ImmersiveMaterial) : uiMaterial.ImmersiveMaterial--><!--Device-uiMaterial-function convertToECSubMaterial(material: uiMaterial.ImmersiveMaterial) : uiMaterial.ImmersiveMaterial-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| material | [uiMaterial.ImmersiveMaterial](arkts-arkui-uimaterial-immersivematerial-c.md) | Yes | Immersive material to convert. |

**Return value:**

| Type | Description |
| --- | --- |
| [uiMaterial.ImmersiveMaterial](arkts-arkui-uimaterial-immersivematerial-c.md) | Immersive material applicable to the child components of [EffectComponent](../arkts-components/arkts-arkui-effectcomponent-comp-sys.md) after conversion. |
