# DatePickerDialogOptions

```TypeScript
declare interface DatePickerDialogOptions extends DatePickerOptions
```

Defines the configuration options of the date picker dialog box.

Inherited from [DatePickerOptions](arkts-arkui-datepicker-comp-datepickeroptions-i.md).

**Inheritance/Implementation:** DatePickerDialogOptions extends [DatePickerOptions](arkts-arkui-datepicker-comp-datepickeroptions-i.md)

**Since:** 8

<!--Device-unnamed-declare interface DatePickerDialogOptions extends DatePickerOptions--><!--Device-unnamed-declare interface DatePickerDialogOptions extends DatePickerOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## distortionMode

```TypeScript
distortionMode?: DistortionMode
```

Distortion animation mode of the dialog box under the system material. This parameter is passed when a custom distortion animation effect for the dialog box is needed.

**Default value:** **DistortionMode.DISTORTION_AUTO**

**System API:** This is a system API.

**Note:** When the value is **DISTORTION_AUTO**, the [ImmersiveMaterial](../arkts-apis/arkts-arkui-uimaterial-immersivematerial-c.md) material type must be set for it to take effect, and the distortion effect is automatically applied based on the device computing power tier (effective on high- and mid-tier devices, not effective on low-tier devices). Distortion animation increases rendering overhead, so use it with caution on low-end devices. For the meaning of each enum value, see [DistortionMode](arkts-arkui-common-comp-distortionmode-e-sys.md).

**Type:** [DistortionMode](arkts-arkui-common-comp-distortionmode-e-sys.md)

**Default:** DistortionMode.DISTORTION_AUTO

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-DatePickerDialogOptions-distortionMode?: DistortionMode--><!--Device-DatePickerDialogOptions-distortionMode?: DistortionMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## edgeLightMode

```TypeScript
edgeLightMode?: EdgeLightMode
```

Edge light animation mode of the dialog box under the system material. This parameter is passed when a custom edge light animation effect for the dialog box is needed.

**Default value:** **EdgeLightMode.EDGELIGHT_AUTO**

**System API:** This is a system API.

**Note:** When the value is **EDGELIGHT_AUTO**, the [ImmersiveMaterial](../arkts-apis/arkts-arkui-uimaterial-immersivematerial-c.md) material type must be set for it to take effect, and the edge light effect is automatically applied based on the device computing power tier (effective on high-tier devices, not effective on mid- and low-tier devices). Edge light animation increases rendering overhead, so use it with caution on low-end devices. For the meaning of each enum value, see [EdgeLightMode](arkts-arkui-common-comp-edgelightmode-e-sys.md).

**Type:** [EdgeLightMode](arkts-arkui-common-comp-edgelightmode-e-sys.md)

**Default:** EdgeLightMode.EDGELIGHT_AUTO

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-DatePickerDialogOptions-edgeLightMode?: EdgeLightMode--><!--Device-DatePickerDialogOptions-edgeLightMode?: EdgeLightMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
