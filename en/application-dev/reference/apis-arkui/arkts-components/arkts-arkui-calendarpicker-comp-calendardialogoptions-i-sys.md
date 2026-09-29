# CalendarDialogOptions

```TypeScript
declare interface CalendarDialogOptions extends CalendarOptions
```

Defines the configuration options of the calendar picker dialog box.

Inherits from [CalendarOptions](arkts-arkui-calendarpicker-comp-calendaroptions-i.md).

> **NOTE:** 
> 
> When the application window is resized, the width of the dialog box is continuously compressed. If the window width
> is reduced below a certain threshold, the content of the dialog box may not be fully visible. To ensure that the
> content of the **CalendarPickerDialog** component is fully displayed, the minimum window width required is 386 vp.

**Inheritance/Implementation:** CalendarDialogOptions extends [CalendarOptions](arkts-arkui-calendarpicker-comp-calendaroptions-i.md)

**Since:** 10

<!--Device-unnamed-declare interface CalendarDialogOptions extends CalendarOptions--><!--Device-unnamed-declare interface CalendarDialogOptions extends CalendarOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## distortionMode

```TypeScript
distortionMode?: DistortionMode
```

Distortion animation mode of the dialog box under system materials. This parameter is passed when a custom distortion animation effect is needed for the dialog box.

**Default value:** **DistortionMode.DISTORTION_AUTO**

**System API:** This is a system API.

Note: When the value is **DISTORTION_AUTO**, the [ImmersiveMaterial](../arkts-apis/arkts-arkui-uimaterial-immersivematerial-c.md) material type must be set for the effect to take effect, and the distortion effect is automatically applied based on the device performance tier (effective on high- and mid-tier devices, not effective on low-tier devices). Distortion animation increases rendering overhead, so use it with caution on low-end devices. For the meaning of each enum value, see [DistortionMode](arkts-arkui-common-comp-distortionmode-e-sys.md).

**Type:** [DistortionMode](arkts-arkui-common-comp-distortionmode-e-sys.md)

**Default:** DistortionMode.DISTORTION_AUTO

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-CalendarDialogOptions-distortionMode?: DistortionMode--><!--Device-CalendarDialogOptions-distortionMode?: DistortionMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## edgeLightMode

```TypeScript
edgeLightMode?: EdgeLightMode
```

Edge light animation mode of the dialog box under system materials. This parameter is passed when a custom edge light animation effect is needed for the dialog box.

**Default value:** **EdgeLightMode.EDGELIGHT_AUTO**

**System API:** This is a system API.

Note: When the value is **EDGELIGHT_AUTO**, the [ImmersiveMaterial](../arkts-apis/arkts-arkui-uimaterial-immersivematerial-c.md) material type must be set for the effect to take effect, and the edge light effect is automatically applied based on the device performance tier (effective on high-tier devices, not effective on mid- and low-tier devices). Edge light animation increases rendering overhead, so use it with caution on low-end devices. For the meaning of each enum value, see [EdgeLightMode](arkts-arkui-common-comp-edgelightmode-e-sys.md).

**Type:** [EdgeLightMode](arkts-arkui-common-comp-edgelightmode-e-sys.md)

**Default:** EdgeLightMode.EDGELIGHT_AUTO

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-CalendarDialogOptions-edgeLightMode?: EdgeLightMode--><!--Device-CalendarDialogOptions-edgeLightMode?: EdgeLightMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
