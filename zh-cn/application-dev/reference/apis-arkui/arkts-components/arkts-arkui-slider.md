# Slider

滑动条组件，通常用于快速调节设置值，如音量调节、亮度调节等应用场景。支持样式定制、方向配置、交互方式和无障碍功能，能解决UI一致性问题，提升开发效率，从而改善用户体验并降低开发成本。 > **说明：**

## 子组件 无

## Slider

```TypeScript
Slider(options?: SliderOptions)
```

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-SliderInterface-(options?: SliderOptions): SliderAttribute--><!--Device-SliderInterface-(options?: SliderOptions): SliderAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [SliderOptions](arkts-arkui-slideroptions-i.md) | 否 | 配置滑动条的参数。若不传入，则使用SliderOptions中各属性的默认值。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [ColorMetricsStop](arkts-arkui-colormetricsstop-i.md) | 线性渐变颜色断点类型，用于描述渐进色颜色断点。 |
| [SlideRange](arkts-arkui-sliderange-i.md) | 定义有效滑动区间。 |
| [SliderBlockStyle](arkts-arkui-sliderblockstyle-i.md) | Slider组件滑块形状参数。 |
| [SliderConfiguration](arkts-arkui-sliderconfiguration-i.md) | 开发者需要自定义class实现ContentModifier接口。继承自CommonConfiguration。 |
| [SliderCustomContentOptions](arkts-arkui-slidercustomcontentoptions-i.md) | Slider前后缀组件无障碍信息参数。 |
| [SliderOptions](arkts-arkui-slideroptions-i.md) | 滑动条的信息。 |
| [SliderPrefixOptions](arkts-arkui-sliderprefixoptions-i.md) | Slider前缀组件无障碍信息参数。 |
| [SliderShowStepOptions](arkts-arkui-slidershowstepoptions-i.md) | Slider刻度点的无障碍文本信息映射集。 |
| [SliderStepItemAccessibility](arkts-arkui-sliderstepitemaccessibility-i.md) | Slider刻度点的无障碍文本信息。 |
| [SliderSuffixOptions](arkts-arkui-slidersuffixoptions-i.md) | Slider后缀组件无障碍信息参数。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [SliderTriggerChangeCallback](arkts-arkui-slidertriggerchangecallback-t.md) | 定义SliderConfiguration中使用的回调类型。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [SliderBlockType](arkts-arkui-sliderblocktype-e.md) | Slider组件滑块形状枚举。 | 名称 | 值 | 说明 | | ------- | -- | ---------------------- | | DEFAULT | 0 | 使用默认滑块（圆形）。 | | IMAGE | 1 | 使用图片资源作为滑块。 | | SHAPE | 2 | 使用自定义形状作为滑块。 | |
| [SliderChangeMode](arkts-arkui-sliderchangemode-e.md) | 滑块状态值，包括按下、拖动、离开、点击滑动条使滑块移动时。 |
| [SliderInteraction](arkts-arkui-sliderinteraction-e.md) | 用户与滑动条组件交互方式。 | 名称 | 值 |说明 | | ------ | -- | ----------------------------- | | SLIDE_AND_CLICK | 0 | 用户可拖拽滑块或者点击滑轨使滑块移动，鼠标或手指按下即发生移动。| | SLIDE_ONLY | 1 | 禁止用户通过点击滑轨使滑块移动。| | SLIDE_AND_CLICK_UP | 2 |用户可拖拽滑块或者点击滑轨使滑块移动，当鼠标或手指抬起时，若与屏幕按压位置一致，则触发移动。| |
| [SliderStyle](arkts-arkui-sliderstyle-e.md) | 滑动条滑块在滑轨上显示的样式，样式说明请参考[Slider组件滑块与滑轨是如何对齐的](../../../ui/arkts-select-component-faq.md#slider组件滑块与滑轨是如何对齐的)。 |

