# DatePickerDialogOptions

日期选择器弹窗选项。继承自[DatePickerOptions](arkts-arkui-datepickeroptions-i.md)。

**继承/实现关系：** DatePickerDialogOptions extends [DatePickerOptions](arkts-arkui-datepickeroptions-i.md)

**起始版本：** 8

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## distortionMode

```TypeScript
distortionMode?: DistortionMode
```

设置系统材质下弹窗的非线性动画模式。当需要自定义弹窗的非线性动画效果时传入此参数。

> **默认值：** DistortionMode.DISTORTION_AUTO

> **系统接口：** 此接口为系统接口。

> **说明：** 当取值为 DISTORTION_AUTO 时，需设置[ImmersiveMaterial](../arkts-apis/arkts-arkui-uimaterial-immersivematerial-c.md) 类型材质方可生效，
> 并依据设备算力档位自动生效非线性效果（高中档算力设备生效，低档算力设备不生效）。非线性动画会增加渲染开销，建议在低端设备上谨慎使用。
> 各枚举取值含义请参见[DistortionMode](arkts-arkui-distortionmode-e-sys.md)。

**类型：** [DistortionMode](arkts-arkui-distortionmode-e-sys.md)

**默认值：** DistortionMode.DISTORTION_AUTO

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## edgeLightMode

```TypeScript
edgeLightMode?: EdgeLightMode
```

设置系统材质下弹窗的流光动画模式。当需要自定义弹窗的流光动画效果时传入此参数。

> **默认值：** EdgeLightMode.EDGELIGHT_AUTO

> **系统接口：** 此接口为系统接口。

> **说明：** 当取值为 EDGELIGHT_AUTO 时，需设置[ImmersiveMaterial](../arkts-apis/arkts-arkui-uimaterial-immersivematerial-c.md) 类型材质方可生效，
> 并依据设备算力档位自动生效流光效果（高档算力设备生效，中低档算力设备不生效）。流光动画会增加渲染开销，建议在低端设备上谨慎使用。
> 各枚举取值含义请参见[EdgeLightMode](arkts-arkui-edgelightmode-e-sys.md)。

**类型：** [EdgeLightMode](arkts-arkui-edgelightmode-e-sys.md)

**默认值：** EdgeLightMode.EDGELIGHT_AUTO

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。
