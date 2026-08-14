# CanvasGradient

渐变对象。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare class CanvasGradient--><!--Device-unnamed-export declare class CanvasGradient-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## addColorStop

```TypeScript
addColorStop(offset: double, color: string | ColorMetrics): void
```

设置渐变断点值，包括偏移和颜色。支持设置rgb或者argb格式颜色。支持通过传入 ColorMetrics 类型设置P3色域颜色值，可在支持高色域的设备上获得更丰富的色彩表现。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CanvasGradient-addColorStop(offset: double, color: string | ColorMetrics): void--><!--Device-CanvasGradient-addColorStop(offset: double, color: string | ColorMetrics): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | double | 是 | 设置渐变点距离起点的位置占总体长度的比例，范围为[0, 1]。 设置offset&lt;0或offset&gt;1无渐变效果。&lt;br&gt;异常值undefined和null按无效值处理， 不设置本次断点值，NaN会导致CanvasGradient异常，Infinity会导致整个CanvasGradient不生效。 |
| color | string \| [ColorMetrics](../../apis-arkui/arkts-apis/arkts-arkui-colormetrics-t.md) | 是 | 设置渐变填充的颜色。&lt;br&gt;可以使用 colorWithSpace 方法构造指定色域属性 [ColorSpace](../../../reference/apis-arkui/arkui-ts/ts-appendix-enums.md#colorspace20) 为SRGB或DISPLAY_P3的颜色。每个渐变ColorMetrics的色域属性应当统一， 设置不同色域的属性时将抛出异常，错误码：103701。&lt;br&gt; 设置null和undefined无效，忽略本次断点值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [103701](../../apis-arkui/errorcode-canvas.md#103701-参数错误) | The color's ColorSpace is not the same as the last color's. |

