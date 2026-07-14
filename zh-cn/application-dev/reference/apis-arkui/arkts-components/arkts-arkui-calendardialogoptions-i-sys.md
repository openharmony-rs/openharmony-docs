# CalendarDialogOptions

日历选择器弹窗选项。

继承自[CalendarOptions](arkts-arkui-calendaroptions-i.md)。

> **说明：**
>
> 在应用窗口缩小过程中，弹窗的宽度会被不断压缩，当缩小到一定程度时会导致其内容无法完整显示，
保证CalendarPickerDialog内容能够完整显示的最小窗口宽度为386vp。

**继承/实现关系：** CalendarDialogOptions extends [CalendarOptions](arkts-arkui-calendaroptions-i.md)

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## distortionMode

```TypeScript
distortionMode?: DistortionMode
```

设置对话框的形变动画模式。

默认值：DistortionMode.DISTORTION_AUTO

**类型：** DistortionMode

**默认值：** DistortionMode.DISTORTION_AUTO

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## edgeLightMode

```TypeScript
edgeLightMode?: EdgeLightMode
```

设置对话框的边缘光动画模式。

默认值：EdgeLightMode.EDGELIGHT_AUTO

**类型：** EdgeLightMode

**默认值：** EdgeLightMode.EDGELIGHT_AUTO

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

