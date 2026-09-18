# @ohos.arkui.uiMaterial(System Material)

This module provides APIs for system materials. Different system materials correspond to different UI effects, including the background color (backgroundColor), border color (borderColor), border width (borderWidth), and shadow (shadow).

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { uiMaterial } from '@kit.ArkUI';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getGlobalMaterialLevel](arkts-arkui-uimaterial-getglobalmateriallevel-f.md) | Obtains the global material level, which is related to the device computing power. This configuration item is defined by the device and cannot be modified. |
| [getMaterialInfo](arkts-arkui-uimaterial-getmaterialinfo-f.md) | Obtains the material configuration information of this application. The returned configuration information comes from the metadata configured in the [module.json5](../../../quick-start/module-configuration-file.md) file of the application. |
| [isImmersiveMaterialSupported](arkts-arkui-uimaterial-isimmersivematerialsupported-f.md) | Check whether [ImmersiveMaterial](arkts-arkui-uimaterial-immersivematerial-c.md) is supported on the current device. If it is true, the ImmersiveMaterial object can be used in the systemMaterial attribute. If it is false, setting the ImmersiveMaterial object in the systemMaterial attribute will not take effect. It is defined by the device and cannot be modified. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [convertToECMaterial](arkts-arkui-uimaterial-converttoecmaterial-f-sys.md) | Convert from ImmersiveMaterial to another ImmersiveMaterial set on EffectComponent. |
| [convertToECSubMaterial](arkts-arkui-uimaterial-converttoecsubmaterial-f-sys.md) | Convert from ImmersiveMaterial to another ImmersiveMaterial set on sub component of EffectComponent. |
<!--DelEnd-->

### Classes

| Name | Description |
| --- | --- |
| [ImmersiveMaterial](arkts-arkui-uimaterial-immersivematerial-c.md) | Immersive material class, which inherits from [Material](arkts-arkui-uimaterial-materialtype-e.md). |
| [Material](arkts-arkui-uimaterial-material-c.md) | System material object on the UI. |

<!--Del-->
### Classes(System API)

| Name | Description |
| --- | --- |
| [Material](arkts-arkui-uimaterial-material-c-sys.md) | System material object on the UI. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [ImmersiveOptions](arkts-arkui-uimaterial-immersiveoptions-i.md) | Immersive material parameters. |
| [LightEffectOptions](arkts-arkui-uimaterial-lighteffectoptions-i.md) | Provides the light sensing interaction feedback configuration for immersive materials. The configuration is used to customize the color of the light sensing feedback. |
| [MaterialInfo](arkts-arkui-uimaterial-materialinfo-i.md) | Provides material configuration information, including the material enabling state and material type. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [MaterialOptions](arkts-arkui-uimaterial-materialoptions-i-sys.md) | System material options. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [ImmersiveStyle](arkts-arkui-uimaterial-immersivestyle-e.md) | Enumerates immersive material styles. Different material styles correspond to different material parameters, including the blur degree and brightness. |
| [MaterialLevel](arkts-arkui-uimaterial-materiallevel-e.md) | Enumerates the material levels, which indicate the computing power level of the device. Use [getGlobalMaterialLevel](arkts-arkui-uimaterial-getglobalmateriallevel-f.md) to obtain the material level of the current device. |
| [MaterialState](arkts-arkui-uimaterial-materialstate-e.md) | Enumerates the material enabling states, indicating the states of the application-level immersive system material configuration. |
| [MaterialType](arkts-arkui-uimaterial-materialtype-e.md) | Enumerates system material types. |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [ImmersiveStyle](arkts-arkui-uimaterial-immersivestyle-e-sys.md) | Enumerates immersive material styles. Different material styles correspond to different material parameters, including the blur degree and brightness. |
| [MaterialType](arkts-arkui-uimaterial-materialtype-e-sys.md) | Enumerates system material types. |
<!--DelEnd-->

## Examples

```TypeScript
### Example 1: Setting the System Material

This example shows how to apply the Material object of a semi-transparent material to a component using the [systemMaterial](../arkui-ts/ts-universal-attributes-image-effect-sys.md#systemmaterial23) attribute.


```

```TypeScript
### Example 2 (Setting the System Material Using EffectComponent)

This example shows how to set [uiMaterial.ImmersiveMaterial](arkts-arkui-uimaterial-immersivematerial-c.md) on [EffectComponent](../arkui-ts/ts-container-effectcomponent-sys.md) and its child components, including directly using EC-style materials and applying the materials after conversion through [uiMaterial.convertToECMaterial](arkts-arkui-uimaterial-converttoecmaterial-f-sys.md) and [uiMaterial.convertToECSubMaterial](arkts-arkui-uimaterial-converttoecsubmaterial-f-sys.md).

Since API version 26.0.0, the uiMaterial.convertToECMaterial and uiMaterial.convertToECSubMaterial APIs are added.
```

```TypeScript
### Example 1: Configuring the Immersive System Material

This example shows how to set the [ImmersiveMaterial](arkts-arkui-uimaterial-immersivematerial-c.md) object to a component through [systemMaterial](../arkui-ts/ts-universal-attributes-image-effect.md#systemmaterial).

Since API version 26.0.0, the ImmersiveMaterial object and systemMaterial attribute are added.

Performance on devices with low-level computing power that support immersive materials



Performance on devices with medium-level computing power that support immersive materials



Performance on devices with high-level computing power that support immersive materials


```

```TypeScript
### Example 2: Obtaining Material Configuration Information and Using an Empty Material to Disable the Immersive System Material

This example shows how to use [uiMaterial.getMaterialInfo](arkts-arkui-uimaterial-getmaterialinfo-f.md) to obtain the material configuration information of this application and use empty to disable the immersive system material effect for a specific component based on the set state.

Since API version 26.0.0, the uiMaterial.getMaterialInfo and empty APIs are added.

Configure the toggle information in the [module.json5](../../../quick-start/module-configuration-file.md) file. Note that the configuration takes effect only in the module of the entry type.
```

```TypeScript
Write the sample code as follows:

Performance on devices with high-level computing power that support immersive materials



Performance on devices with medium-level computing power that support immersive materials



Performance on devices with low-level computing power that support immersive materials


```

```TypeScript
### Example 3: Setting an Interactive Deformation Effect for the Component Material

This example shows how to use the interactive API in [ImmersiveOptions](arkts-arkui-uimaterial-immersiveoptions-i.md) to implement an interactive deformation effect for a component.

Since API version 26.0.0, the interactive API is added.


```

```TypeScript
### Example 4: Setting a Light Sensing Interaction Feedback Effect for the Component Material

This example shows how to use the lightEffect API in [ImmersiveOptions](arkts-arkui-uimaterial-immersiveoptions-i.md) to implement a light sensing interaction feedback effect for a component.

Since API version 26.0.0, the lightEffect API is added.


```

```TypeScript
### Example 5: Querying the Material Level and Whether Immersive Materials Are Supported

This example describes how to use [getGlobalMaterialLevel](arkts-arkui-uimaterial-getglobalmateriallevel-f.md) to obtain the material level of a device and use [isImmersiveMaterialSupported](arkts-arkui-uimaterial-isimmersivematerialsupported-f.md) to check whether the device supports immersive materials. Based on the result, you can determine whether to set immersive materials for components. With this adaptation method, the application can reuse the same set of code on devices that support immersive materials and those that do not. On devices that do not support immersive materials, the application falls back to the common style, eliminating the need to write different code for different devices.

getGlobalMaterialLevel and isImmersiveMaterialSupported are added since API version 26.0.0.
```
