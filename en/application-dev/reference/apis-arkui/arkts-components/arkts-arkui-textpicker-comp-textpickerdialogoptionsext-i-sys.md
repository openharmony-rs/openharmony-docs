# TextPickerDialogOptionsExt

```TypeScript
declare interface TextPickerDialogOptionsExt extends TextPickerOptions
```

Inherits from [TextPickerOptions](arkts-arkui-textpicker-comp-textpickeroptions-i.md).

**Inheritance/Implementation:** TextPickerDialogOptionsExt extends [TextPickerOptions](arkts-arkui-textpicker-comp-textpickeroptions-i.md)

**Since:** 20

<!--Device-unnamed-declare interface TextPickerDialogOptionsExt extends TextPickerOptions--><!--Device-unnamed-declare interface TextPickerDialogOptionsExt extends TextPickerOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## distortionMode

```TypeScript
distortionMode?: DistortionMode
```

Distortion animation mode of the dialog box under system materials. This parameter is passed in when a custom distortion animation effect is required for the dialog box.

**Default value:** **DistortionMode.DISTORTION_AUTO**

**System API:** This is a system API.

**Note:** When the value is **DISTORTION_AUTO**, the [ImmersiveMaterial](../arkts-apis/arkts-arkui-uimaterial-immersivematerial-c.md) material type must be set for the effect to take effect, and the distortion effect is automatically enabled based on the device computing power level (enabled on high- and mid-range devices, disabled on low-end devices). Distortion animation increases rendering overhead, so it is recommended to use it with caution on low-end devices. For the meaning of each enum value, see [DistortionMode](arkts-arkui-common-comp-distortionmode-e-sys.md).

**Type:** [DistortionMode](arkts-arkui-common-comp-distortionmode-e-sys.md)

**Default:** DistortionMode.DISTORTION_AUTO

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-TextPickerDialogOptionsExt-distortionMode?: DistortionMode--><!--Device-TextPickerDialogOptionsExt-distortionMode?: DistortionMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## edgeLightMode

```TypeScript
edgeLightMode?: EdgeLightMode
```

Edge light animation mode of the dialog box under system materials. This parameter is passed in when a custom edge light animation effect is required for the dialog box.

**Default value:** **EdgeLightMode.EDGELIGHT_AUTO**

**System API:** This is a system API.

**Note:** When the value is **EDGELIGHT_AUTO**, the [ImmersiveMaterial](../arkts-apis/arkts-arkui-uimaterial-immersivematerial-c.md) material type must be set for the effect to take effect, and the edge light effect is automatically enabled based on the device computing power level (enabled on high-end devices, disabled on mid-range and low-end devices). Edge light animation increases rendering overhead, so it is recommended to use it with caution on low-end devices. For the meaning of each enum value, see [EdgeLightMode](arkts-arkui-common-comp-edgelightmode-e-sys.md).

**Type:** [EdgeLightMode](arkts-arkui-common-comp-edgelightmode-e-sys.md)

**Default:** EdgeLightMode.EDGELIGHT_AUTO

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-TextPickerDialogOptionsExt-edgeLightMode?: EdgeLightMode--><!--Device-TextPickerDialogOptionsExt-edgeLightMode?: EdgeLightMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
