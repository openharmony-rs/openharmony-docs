# TimePickerDialogOptions

时间选择器弹窗选项。 继承自[TimePickerOptions](arkts-arkui-timepickeroptions-i.md#TimePickerOptions)。

**继承/实现关系：** TimePickerDialogOptions extends [TimePickerOptions](arkts-arkui-timepickeroptions-i.md#TimePickerOptions)

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** -1

<!--Device-unnamed-declare interface TimePickerDialogOptions--><!--Device-unnamed-declare interface TimePickerDialogOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## distortionMode

```TypeScript
distortionMode?: DistortionMode
```

设置系统材质下弹窗的非线性动画模式。 > **默认值：** DistortionMode.DISTORTION_AUTO > **系统接口：** 此接口为系统接口。 > **说明：** 当取值为 DISTORTION_AUTO 时，需设置 > [ImmersiveMaterial](../../apis-na/arkts-apis/arkts-na-uimaterial-immersivematerial-c.md#ImmersiveMaterial) 类型材质方可生效，并依据设备算力档位自动生效非线性效果（高中档算力设备生效， > 低档算力设备不生效）。非线性动画会增加渲染开销，建议在低端设备上谨慎使用。 > 各枚举取值含义请参见DistortionMode。

**类型：** DistortionMode

**默认值：** DistortionMode.DISTORTION_AUTO

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TimePickerDialogOptions-distortionMode?: DistortionMode--><!--Device-TimePickerDialogOptions-distortionMode?: DistortionMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## edgeLightMode

```TypeScript
edgeLightMode?: EdgeLightMode
```

设置系统材质下弹窗的流光动画模式。 > **默认值：** EdgeLightMode.EDGELIGHT_AUTO > **系统接口：** 此接口为系统接口。 > **说明：** 当取值为 EDGELIGHT_AUTO 时，需设置 > [ImmersiveMaterial](../../apis-na/arkts-apis/arkts-na-uimaterial-immersivematerial-c.md#ImmersiveMaterial) 类型材质方可生效，并依据设备算力档位自动生效流光效果（高档算力设备生效， > 中低档算力设备不生效）。流光动画会增加渲染开销，建议在低端设备上谨慎使用。各枚举取值含义请参见EdgeLightMode。

**类型：** EdgeLightMode

**默认值：** EdgeLightMode.EDGELIGHT_AUTO

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TimePickerDialogOptions-edgeLightMode?: EdgeLightMode--><!--Device-TimePickerDialogOptions-edgeLightMode?: EdgeLightMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

