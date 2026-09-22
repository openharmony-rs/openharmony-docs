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

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## distortionMode

```TypeScript
distortionMode?: DistortionMode
```

Sets the distortion animation mode for the dialog.

Default Value: DistortionMode.DISTORTION_AUTO

**Type:** [DistortionMode](arkts-arkui-common-comp-distortionmode-e-sys.md)

**Default:** DistortionMode.DISTORTION_AUTO

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## edgeLightMode

```TypeScript
edgeLightMode?: EdgeLightMode
```

Sets the edge light animation mode for the dialog.

Default value: EdgeLightMode.EDGELIGHT_AUTO

**Type:** [EdgeLightMode](arkts-arkui-common-comp-edgelightmode-e-sys.md)

**Default:** EdgeLightMode.EDGELIGHT_AUTO

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
