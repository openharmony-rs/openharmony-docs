# CanvasGradient

渐变对象。

**起始版本：** 8

<!--Device-unnamed-declare class CanvasGradient--><!--Device-unnamed-declare class CanvasGradient-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## addColorStop

```TypeScript
addColorStop(offset: number, color: string): void
```

设置渐变断点值，包括偏移和颜色。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CanvasGradient-addColorStop(offset: number, color: string): void--><!--Device-CanvasGradient-addColorStop(offset: number, color: string): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number | 是 | 设置渐变点距离起点的位置占总体长度的比例，范围为[0, 1]。<br>设置offset小于0或offset大于1无渐变效果。<br>异常值undefined和null按无效值处理，忽略本次断点值。NaN会导致CanvasGradient异常，Infinity会导致整个CanvasGradient不生效。 |
| color | string | 是 | 设置渐变的颜色。颜色格式参考[ResourceColor](../../../../reference/apis-arkui/arkui-ts/ts-types.md#resourcecolor)中string类型说明。<br>未按格式设置颜色无渐变效果。 |

## addColorStop

```TypeScript
addColorStop(offset: number, color: string | ColorMetrics): void
```

设置渐变断点值，包括偏移和颜色。支持设置rgb或者argb格式颜色。支持通过传入[ColorMetrics](../../../../reference/apis-arkui/js-apis-arkui-graphics.md#colormetrics12)类型设置P3色域颜色值，可在支持高色域的设备上获得更丰富的色彩表现。

> **说明：**  
>  
> 仅[CanvasRenderingContext2D](../../../../reference/apis-arkui/arkui-ts/ts-canvasrenderingcontext2d.md)  
> 对象的[fillStyle](../../../../reference/apis-arkui/arkui-ts/ts-canvasrenderingcontext2d.md#fillstyle)  
> 和[strokeStyle](../../../../reference/apis-arkui/arkui-ts/ts-canvasrenderingcontext2d.md#strokestyle)  
> 属性支持设置P3广色域的CanvasGradient对象，且需要将Canvas组件所在窗口的色域模式通过  
> [setWindowColorSpace](../../../../reference/apis-arkui/arkts-apis-window-Window.md#setwindowcolorspace9)  
> 方法设置为广色域模式WIDE_GAMUT。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本20开始，该接口支持在ArkTS卡片中使用。

<!--Device-CanvasGradient-addColorStop(offset: number, color: string | ColorMetrics): void--><!--Device-CanvasGradient-addColorStop(offset: number, color: string | ColorMetrics): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number | 是 | 设置渐变点距离起点的位置占总体长度的比例，范围为[0, 1]。<br>设置offset小于0或offset大于1无渐变效果。<br>异常值undefined和null按无效值处理，不设置本次断点值。NaN会导致CanvasGradient异常，Infinity会导致整个CanvasGradient不生效。 |
| color | string \| ColorMetrics | 是 | 设置渐变填充的颜色。<br>可以使用[colorWithSpace](../../../../reference/apis-arkui/js-apis-arkui-graphics.md#colorwithspace20)方法构造指定色域属性[ColorSpace](../../../../reference/apis-arkui/arkui-ts/ts-appendix-enums.md#colorspace20)为SRGB或DISPLAY_P3的颜色。每个渐变ColorMetrics的色域属性应当统一，设置不同色域的属性时将抛出异常，错误码：103701。<br>设置null和undefined无效，忽略本次断点值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [103701](../errorcode-canvas.md#103701-参数错误) | The color's ColorSpace is not the same as the last color's. |

