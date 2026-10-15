# ImmersiveMaterial

```TypeScript
class ImmersiveMaterial extends Material
```

Immersive material class, which inherits from [Material](arkts-arkui-uimaterial-material-c.md).

The immersive material has tiered performance based on whether the device supports immersive material and the device's computing power. You can use [isImmersiveMaterialSupported](arkts-arkui-uimaterial-isimmersivematerialsupported-f.md) to determine whether the device supports immersive material, and use [getGlobalMaterialLevel](arkts-arkui-uimaterial-getglobalmateriallevel-f.md) to obtain the material level of the device. On devices that do not support immersive material, immersive material can be set but will have no effect. On high and medium computing power devices that support immersive material, the material effect is implemented through the material layer filter attribute [materialFilter](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#materialfilter) and the shadow attribute [shadow](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#shadow1). When the [systemMaterial](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#systemmaterial) attribute takes effect, the previously set background color attribute [backgroundColor](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#backgroundcolor1) is restored to transparent, and the previously set border width attribute [borderWidth](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#borderwidth) is restored to no border effect. On low computing power devices that support immersive material, the material effect is implemented through the background color attribute [backgroundColor](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#backgroundcolor1), border color attribute [borderColor](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#bordercolor), border width attribute [borderWidth](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#borderwidth), and shadow attribute [shadow](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#shadow1). The effect of the same material is influenced by the immersive light sensation configuration item in the system settings app. Under different intensity levels of immersive light sensation configuration, the material parameters and effects may vary.

**Inheritance/Implementation:** ImmersiveMaterial extends [Material](arkts-arkui-uimaterial-material-c.md)

**Since:** 26.0.0

<!--Device-uiMaterial-class ImmersiveMaterial extends Material--><!--Device-uiMaterial-class ImmersiveMaterial extends Material-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { uiMaterial } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(options?: ImmersiveOptions)
```

Constructs **ImmersiveMaterial**.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ImmersiveMaterial-constructor(options?: ImmersiveOptions)--><!--Device-ImmersiveMaterial-constructor(options?: ImmersiveOptions)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ImmersiveOptions](arkts-arkui-uimaterial-immersiveoptions-i.md) | No | System material configuration options, including the material style and material layer coloring.<br>For details about the default values, see the default values of the parameters in the **ImmersiveOptions** API, that is, **{style:uiMaterial.ImmersiveStyle.REGULAR, materialColor:undefined, colorInvert:false, applyShadow:true, interactive:false, lightEffect:undefined}**. |
