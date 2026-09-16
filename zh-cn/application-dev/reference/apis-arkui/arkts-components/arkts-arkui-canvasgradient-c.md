# CanvasGradient

OffscreenCanvas支持以下属性：

**起始版本：** 8

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## addColorStop

```TypeScript
addColorStop(offset: number, color: string): void
```

设置渐变断点值，包括偏移和颜色。调用多次addColorStop可设置多个断点，断点按offset值从小到大排序，渲染时在相邻断点间进行颜色插值。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number | 是 | 设置渐变断点距离起点的位置占总体长度的比例，范围为[0, 1]。<br>设置offset&lt;0或offset&gt;1无渐变效果。<br>异常值undefined和null按无效值处理，不添加该断点。NaN会导致CanvasGradient对象异常，无法正常生成渐变效果；Infinity会导致整个CanvasGradient不生效。 |
| color | string | 是 | 设置渐变的颜色。string类型支持'rgb(255, 255, 255)'、'rgba(255, 255, 255, 1.0)'、'#RGB'、'#ARGB'、'#RRGGBB'、'#AARRGGBB'格式，参考[ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)中string类型说明。<br>未按格式设置颜色无渐变效果。设置null和undefined时按无效值处理，不添加该断点。 |

**示例**

```TypeScript
通过addColorStop设置渐变断点值，包括偏移和颜色。
```

```TypeScript
通过addColorStop设置指定色域的渐变断点值，包括偏移和颜色。设置窗口色域模式为广色域参照方法[setWindowColorSpace](../arkts-apis-window-Window.md#setwindowcolorspace)。
```

```TypeScript


以下示例演示SDR与HDR渐变的亮度差异。通过ColorMetrics可以构造BT2020色域的HDR颜色，颜色分量值可以超过1.0，超过1.0的部分用于表现超出普通屏幕亮度范围的高亮效果。左侧使用sRGB色域的红->白->绿渐变，右侧使用BT2020色域的HDR颜色且高光白色亮度倍数达到1.5，在支持HDR的屏幕上右侧高光区域明显比左侧更亮。

> 说明：
> 
> 使用HDR颜色时，需要将Canvas组件所在窗口的色域模式通过[setWindowColorSpace](../arkts-apis-window-Window.md#setwindowcolorspace)方法设置为广色域模式（WIDE_GAMUT），否则HDR提亮效果不会生效。

从API版本26.0.0开始，[addColorStop](#addcolorstop)接口新增支持通过ColorMetrics类型入参进行HDR提亮。
```

## addColorStop

```TypeScript
addColorStop(offset: number, color: string | ColorMetrics): void
```

设置渐变断点值，包括偏移和颜色。支持设置rgb或argb格式颜色。支持通过传入[ColorMetrics](../arkts-apis/arkts-arkui-graphics-colormetrics-c.md)类型设置P3广色域颜色值，从API版本26.0.0开始，新增支持BT2020广色域和HDR提亮。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本20开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number | 是 | 设置渐变点距离起点的位置占总体长度的比例，范围为[0, 1]。<br>设置offset&lt;0或offset&gt;1无渐变效果。<br>异常值undefined和null按无效值处理，不添加该断点。NaN会导致CanvasGradient对象异常，无法正常生成渐变效果；Infinity会导致整个CanvasGradient不生效。 |
| color | string &#124; [ColorMetrics](../arkts-apis/arkts-arkui-colormetrics-t.md) | 是 | 设置渐变的颜色。string类型支持'rgb(255, 255, 255)'、'rgba(255, 255, 255, 1.0)'、'#RGB'、'#ARGB'、'#RRGGBB'、'#AARRGGBB'格式。<br>可以使用[colorWithSpace](../arkts-apis/arkts-arkui-graphics-colormetrics-c.md#colorwithspace)方法构造指定色域属性的颜色。ColorMetrics类型可以构造指定色域属性ColorSpace为sRGB或DISPLAY_P3的颜色。从API版本26.0.0开始，新增支持构造BT2020色域的颜色，并支持HDR提亮。同一CanvasGradient对象中的所有渐变断点必须使用相同的色域属性，设置不同色域时将抛出异常，错误码：103701，此时不会添加该断点，CanvasGradient对象保持之前的状态。<br>未按格式设置颜色无渐变效果。设置null和undefined时按无效值处理，不添加该断点。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [103701](../errorcode-canvas.md#103701-参数错误) | The color's ColorSpace is not the same as the last color's. |

**示例**

参见 [addColorStop](#addcolorstop)
