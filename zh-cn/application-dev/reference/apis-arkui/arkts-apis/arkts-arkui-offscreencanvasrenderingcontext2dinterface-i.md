# OffscreenCanvasRenderingContext2DInterface

使用OffscreenCanvasRenderingContext2D在Canvas上进行离屏绘制，绘制对象可以是形状、文本、图片等。 离屏绘制是指将需要绘制的内容先绘制在缓存区，然后将其转换成图片，一次性绘制到Canvas上。 离屏绘制使用CPU进行绘制，绘制速度较慢，对绘制速度有要求的场景应避免使用离屏绘制。 > **说明：** > > OffscreenCanvasRenderingContext2D无法在ServiceExtensionAbility中使用， > ServiceExtensionAbility中建议使用 > \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_ > 进行离屏绘制。 > > beginPath、moveTo、lineTo、closePath、bezierCurveTo、quadraticCurveTo、arc、arcTo、ellipse、rect和 > roundRect接口只能对OffscreenCanvasRenderingContext2D中的路径生效，无法对 > \_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_ > 和\_\_\_MD\_LINK\_DESC\_USD\_2\_\_\_ > 对象中设置的路径生效。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

<!--Device-unnamed-declare interface OffscreenCanvasRenderingContext2DInterface--><!--Device-unnamed-declare interface OffscreenCanvasRenderingContext2DInterface-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
(width: number, height: number, settings?: RenderingContextSettings): OffscreenCanvasRenderingContext2D
```

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

<!--Device-OffscreenCanvasRenderingContext2DInterface-(width: number, height: number, settings?: RenderingContextSettings): OffscreenCanvasRenderingContext2D--><!--Device-OffscreenCanvasRenderingContext2DInterface-(width: number, height: number, settings?: RenderingContextSettings): OffscreenCanvasRenderingContext2D-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| width | number | 是 |  |
| height | number | 是 |  |
| settings | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ |  |

## constructor

```TypeScript
(width: number, height: number, settings?: RenderingContextSettings, unit?: LengthMetricsUnit): OffscreenCanvasRenderingContext2D
```

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

<!--Device-OffscreenCanvasRenderingContext2DInterface-(width: number, height: number, settings?: RenderingContextSettings, unit?: LengthMetricsUnit): OffscreenCanvasRenderingContext2D--><!--Device-OffscreenCanvasRenderingContext2DInterface-(width: number, height: number, settings?: RenderingContextSettings, unit?: LengthMetricsUnit): OffscreenCanvasRenderingContext2D-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| width | number | 是 |  |
| height | number | 是 |  |
| settings | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 |  |
| unit | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ |  |

