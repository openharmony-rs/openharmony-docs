# TimePickerDialogOptions

```TypeScript
declare interface TimePickerDialogOptions extends TimePickerOptions
```

Defines the configuration options of the time picker dialog box.

Inherited from [TimePickerOptions](arkts-arkui-timepicker-comp-timepickeroptions-i.md).

**Inheritance/Implementation:** TimePickerDialogOptions extends [TimePickerOptions](arkts-arkui-timepicker-comp-timepickeroptions-i.md)

**Since:** 8

<!--Device-unnamed-declare interface TimePickerDialogOptions extends TimePickerOptions--><!--Device-unnamed-declare interface TimePickerDialogOptions extends TimePickerOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## distortionMode

```TypeScript
distortionMode?: DistortionMode
```

Distortion animation mode of the dialog box under system materials.

**Default value:** **DistortionMode.DISTORTION_AUTO**

**System API:** This is a system API.

**Note:** When the value is **DISTORTION_AUTO**, the [ImmersiveMaterial](../arkts-apis/arkts-arkui-uimaterial-immersivematerial-c.md) material type must be set for the effect to take effect, and the distortion effect is automatically applied based on the device computing power tier (effective on high- and mid-tier computing power devices, ineffective on low-tier computing power devices). Distortion animation increases rendering overhead, so exercise caution when using it on low-end devices. For the meaning of each enum value, see [DistortionMode](arkts-arkui-common-comp-distortionmode-e-sys.md).

**Type:** [DistortionMode](arkts-arkui-common-comp-distortionmode-e-sys.md)

**Default:** DistortionMode.DISTORTION_AUTO

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-TimePickerDialogOptions-distortionMode?: DistortionMode--><!--Device-TimePickerDialogOptions-distortionMode?: DistortionMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## edgeLightMode

```TypeScript
edgeLightMode?: EdgeLightMode
```

Edge light animation mode of the dialog box under system materials.

**Default value:** **EdgeLightMode.EDGELIGHT_AUTO**

**System API:** This is a system API.

**Note:** When the value is **EDGELIGHT_AUTO**, the [ImmersiveMaterial](../arkts-apis/arkts-arkui-uimaterial-immersivematerial-c.md) material type must be set for the effect to take effect, and the edge light effect is automatically applied based on the device computing power tier (effective on high-tier computing power devices, ineffective on mid- and low-tier computing power devices). Edge light animation increases rendering overhead, so exercise caution when using it on low-end devices. For the meaning of each enum value, see [EdgeLightMode](arkts-arkui-common-comp-edgelightmode-e-sys.md).

**Type:** [EdgeLightMode](arkts-arkui-common-comp-edgelightmode-e-sys.md)

**Default:** EdgeLightMode.EDGELIGHT_AUTO

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-TimePickerDialogOptions-edgeLightMode?: EdgeLightMode--><!--Device-TimePickerDialogOptions-edgeLightMode?: EdgeLightMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
