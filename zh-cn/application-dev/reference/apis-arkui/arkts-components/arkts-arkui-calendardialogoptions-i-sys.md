# CalendarDialogOptions

日历选择器弹窗选项。 继承自[CalendarOptions]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_。 > **说明：** > > 在应用窗口缩小过程中，弹窗的宽度会被不断压缩，当缩小到一定程度时会导致其内容无法完整显示，保证CalendarPickerDialog内容能够完整显示的最小 > 窗口宽度为386vp。

**继承/实现关系：** CalendarDialogOptions extends [CalendarOptions](../arkts-apis/arkts-arkui-component/calendarpicker-calendaroptions-i.md)

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

<!--Device-unnamed-declare interface CalendarDialogOptions extends CalendarOptions--><!--Device-unnamed-declare interface CalendarDialogOptions extends CalendarOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## distortionMode

```TypeScript
distortionMode?: DistortionMode
```

设置系统材质下弹窗的非线性动画模式。当需要自定义弹窗的非线性动画效果时传入此参数。 > **默认值：** DistortionMode.DISTORTION\_AUTO > **系统接口：** 此接口为系统接口。 > **说明：** 当取值为 DISTORTION\_AUTO 时，需设置 > [ImmersiveMaterial]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_类型材质方可生效，并依据设备算力档位自动生效非线性效果（高中档算力设备生效， > 低档算力设备不生效）。非线性动画会增加渲染开销，建议在低端设备上谨慎使用。 > 各枚举取值含义请参见[DistortionMode]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_。

**类型：** DistortionMode

**默认值：** DistortionMode.DISTORTION_AUTO

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CalendarDialogOptions-distortionMode?: DistortionMode--><!--Device-CalendarDialogOptions-distortionMode?: DistortionMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## edgeLightMode

```TypeScript
edgeLightMode?: EdgeLightMode
```

设置系统材质下弹窗的流光动画模式。当需要自定义弹窗的流光动画效果时传入此参数。 > **默认值：** EdgeLightMode.EDGELIGHT\_AUTO > > **系统接口：** 此接口为系统接口。 > > **说明：** 当取值为 EDGELIGHT\_AUTO 时，需设置 > [ImmersiveMaterial]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_类型材质方可生效，并依据设备算力档位自动生效流光效果（高档算力设备生效， > 中低档算力设备不生效）。流光动画会增加渲染开销，建议在低端设备上谨慎使用。各枚举取值含义请参见[EdgeLightMode]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_。

**类型：** EdgeLightMode

**默认值：** EdgeLightMode.EDGELIGHT_AUTO

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CalendarDialogOptions-edgeLightMode?: EdgeLightMode--><!--Device-CalendarDialogOptions-edgeLightMode?: EdgeLightMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

