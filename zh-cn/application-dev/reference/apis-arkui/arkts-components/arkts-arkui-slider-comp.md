# Slider

滑动条组件，通常用于快速调节设置值，如音量调节、亮度调节等应用场景。支持样式定制、方向配置、交互方式和无障碍功能，能解决UI一致性问题，提升开发效率，从而改善用户体验并降低开发成本。

> **说明：**

## 子组件

无

## Slider

```TypeScript
Slider(options?: SliderOptions)
```

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

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
| [SliderConfiguration](arkts-arkui-sliderconfiguration-i.md) | 开发者需要自定义class实现ContentModifier接口。继承自[CommonConfiguration](arkts-arkui-commonconfiguration-i.md)。 |
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
| [SliderBlockType](arkts-arkui-sliderblocktype-e.md) | Slider组件滑块形状枚举。 |
| [SliderChangeMode](arkts-arkui-sliderchangemode-e.md) | 滑块状态值，包括按下、拖动、离开、点击滑动条使滑块移动时。 |
| [SliderInteraction](arkts-arkui-sliderinteraction-e.md) | 用户与滑动条组件交互方式。 |
| [SliderStyle](arkts-arkui-sliderstyle-e.md) | 滑动条滑块在滑轨上显示的样式，样式说明请参考[Slider组件滑块与滑轨是如何对齐的](../../../ui/arkts-select-component-faq.md#slider组件滑块与滑轨是如何对齐的)。 |

## 示例

```TypeScript
### 示例1（滑动条基础样式）

该示例通过配置style、showTips、showSteps控制气泡、刻度值、滑块和滑轨的显示。


```

```TypeScript
### 示例2（设置滑动条样式）

该示例通过blockBorderColor、blockSize、blockBorderWidth、blockStyle设置滑块的样式，通过stepSize、stepColor设置刻度值的样式，通过trackBorderRadius设置底板的圆角，通过selectedBorderRadius设置已滑动部分的圆角。


```

```TypeScript
### 示例3（自定义滑动条）

通过样式Builder定制Slider组件内容区。点击增加按钮，进度条会按照原Slider设置的步长增加，反之点击减少按钮进度条会减少，并触发原组件的onChange事件。


```

```TypeScript
### 示例4（设置滑动条渐变色）

该示例通过selectedColor设置滑动条渐变色，通过focusable、defaultFocus和focusOnTouch设置滑动条支持表冠操作。


```

```TypeScript
### 示例5（滑动条设置前后缀内容）

通过prefix、suffix属性设置滑动条的前后缀内容，定制其内容区以及无障碍属性。设置无障碍属性后，屏幕阅读器将以设置的无障碍内容进行朗读。


```

```TypeScript
### 示例6（滑动条设置刻度点无障碍文本）

通过[showSteps](arkts-arkui-slider-comp-attribute.md#showsteps)属性设置刻度点的无障碍文本信息。设置后，屏幕阅读器将以设置的无障碍内容进行朗读。从API version 20开始，[showSteps](arkts-arkui-slider-comp-attribute.md#showsteps)方法新增可选参数options。


```

```TypeScript
### 示例7（设置滑动条的双向绑定）

从API version 11开始，将[SliderOptions](#slideroptions对象说明)的value属性设置为[$$](../../../ui/state-management/arkts-two-way-sync.md)绑定的变量，实现数据同步。


```

```TypeScript
### 示例8（滑块设置渐变色）

通过blockColor属性设置滑块渐变色。


```

```TypeScript
### 示例9（设置滑轨的背景颜色）

通过[trackColorMetrics](arkts-arkui-slider-comp-attribute.md#trackcolormetrics)设置指定色域的渐变断点值。示例中的colorSpace使用了ColorSpace.DISPLAY_P3类型，需要对应窗口调用setWindowColorSpace接口，将当前窗口设置为广色域模式，设置窗口色域模式为广色域参照方法[setWindowColorSpace](../arkts-apis-window-Window.md#setwindowcolorspace)。

从API version 23开始，新增trackColorMetrics接口。


```

```TypeScript
### 示例10（设置滑动条的沉浸光感效果）

该示例通过通用属性[systemMaterial](ts-universal-attributes-image-effect.md#systemmaterial)设置滑动条的系统材质，实现沉浸光感效果。设置系统材质后，Slider滑动过程中会产生粒子动画效果。

该示例配图为高算力设备强档效果，组件沉浸光感效果会根据设备算力与用户在系统中设置的沉浸光感效果自适应调整，开发者无需额外适配。

从API版本26.0.0开始，新增systemMaterial接口。
```
