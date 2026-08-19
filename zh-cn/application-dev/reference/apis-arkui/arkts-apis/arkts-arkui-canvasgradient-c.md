# CanvasGradient

OffscreenCanvas支持以下属性：

**起始版本：** 8

<!--Device-unnamed-declare class CanvasGradient--><!--Device-unnamed-declare class CanvasGradient-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## addColorStop

```TypeScript
addColorStop(offset: number, color: string): void
```

设置渐变断点值，包括偏移和颜色。调用多次addColorStop可设置多个断点，断点按offset值从小到大排序，渲染时在相邻断点间进行颜色插值。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-CanvasGradient-addColorStop(offset: number, color: string): void--><!--Device-CanvasGradient-addColorStop(offset: number, color: string): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number | 是 | 设置渐变点距离起点的位置占总体长度的比例，范围为[0, 1]。 <br>设置offset&lt;0或offset&gt;1无渐变效果。 <br>异常值undefined和null按无效值处理，不添加该断点。NaN会导致CanvasGradient对象异常，无法正常生成渐变效果；Infinity会导致整个CanvasGradient不生效。 |
| color | string | 是 | 设置渐变的颜色。string类型支持'rgb(255, 255, 255)'、'rgba(255, 255, 255, 1.0)'、'#RGB'、'#ARGB'、'#RRGGBB '、'#AARRGGBB'格式，参考ResourceColor中string类型说明。 <br>未按格式设置颜色无渐变效果。设置null和undefined时按无效值处理，不添加该断点。 |

**示例**

通过addColorStop设置渐变断点值，包括偏移和颜色。支持设置rgb或者argb格式颜色。

```TypeScript
// xxx.ets
@Entry
@Component
struct AddColorStop {
  private settings: RenderingContextSettings = new RenderingContextSettings(true);
  private context: CanvasRenderingContext2D = new CanvasRenderingContext2D(this.settings);

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Canvas(this.context)
        .width('100%')
        .height('100%')
        .backgroundColor('rgb(213,213,213)')
        .onReady(() => {
          let grad = this.context.createLinearGradient(50, 0, 300, 100)
          grad.addColorStop(0.0, 'rgb(39,135,217)')
          grad.addColorStop(0.5, 'rgb(255,238,240)')
          grad.addColorStop(1.0, 'rgb(23,169,141)')
          this.context.fillStyle = grad
          this.context.fillRect(0, 0, 400, 400)
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

## addColorStop

```TypeScript
addColorStop(offset: number, color: string | ColorMetrics): void
```

设置渐变断点值，包括偏移和颜色。支持设置rgb或argb格式颜色。支持通过传入[ColorMetrics](arkts-arkui-graphics-colormetrics-c.md)类型设置P3广色域颜色值，从API版 本26.0.0开始，新增支持BT2020广色域和HDR提亮。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本20开始，该接口支持在ArkTS卡片中使用。

<!--Device-CanvasGradient-addColorStop(offset: number, color: string | ColorMetrics): void--><!--Device-CanvasGradient-addColorStop(offset: number, color: string | ColorMetrics): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number | 是 | 设置渐变点距离起点的位置占总体长度的比例，范围为[0, 1]。 <br>设置offset&lt;0或offset&gt;1无渐变效果。 <br>异常值undefined和null按无效值处理，不添加该断点。NaN会导致CanvasGradient对象异常，无法正常生成渐变效果；Infinity会导致整个CanvasGradient不生效。 |
| color | string \| ColorMetrics | 是 | 设置渐变的颜色。string类型支持'rgb(255, 255, 255)'、'rgba(255, 255, 255, 1.0)'、'#RGB'、' #ARGB'、'#RRGGBB'、'#AARRGGBB'格式。 <br>可以使用[colorWithSpace](arkts-arkui-graphics-colormetrics-c.md#colorwithspace)方法构造指定色域属性的颜色。ColorMetrics类型 可以构造指定色域属性ColorSpace为sRGB或DISPLAY_P3的颜色。从API版本26.0.0开始，新增支持构造BT2020色域的颜色，并支持HDR提亮。同一 CanvasGradient对象中的所有渐变断点必须使用相同的色域属性，设置不同色域时将抛出异常，错误码：103701，此时不会添加该断点，CanvasGradient对象保持之前的状态。 <br>未按格式设置颜色无渐变效果。设置null和undefined时按无效值处理，不添加该断点。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [103701](../errorcode-canvas.md#103701-参数错误) | The color's ColorSpace is not the same as the last color's. |

**示例**

通过addColorStop设置指定色域的渐变断点值，包括偏移和颜色。设置窗口色域模式为广色域参照方法[setWindowColorSpace](../arkts-apis-window-Window.md#setwindowcolorspace)。

```TypeScript
// xxx.ets
import { BusinessError } from '@kit.BasicServicesKit';
import { ColorMetrics } from '@kit.ArkUI'

@Entry
@Component
struct AddColorStop {
  private settings: RenderingContextSettings = new RenderingContextSettings(true);
  private context: CanvasRenderingContext2D = new CanvasRenderingContext2D(this.settings);

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Canvas(this.context)
        .width('100%')
        .height('100%')
        .onReady(() => {
          // 设置fillStyle为sRGB色域效果的gradient
          let gradSRGB = this.context.createLinearGradient(85, 10, 160, 110)
          // 使用try catch对可能出现的异常进行捕获
          try {
            gradSRGB.addColorStop(0.0, ColorMetrics.colorWithSpace(ColorSpace.SRGB, 1.0, 0.0, 0.0, 1.0))
            gradSRGB.addColorStop(0.5, ColorMetrics.colorWithSpace(ColorSpace.SRGB, 1.0, 1.0, 1.0, 1.0))
            gradSRGB.addColorStop(1.0, ColorMetrics.colorWithSpace(ColorSpace.SRGB, 0.0, 1.0, 0.0, 1.0))
          } catch (error) {
            let e: BusinessError = error as BusinessError;
            console.error(`Failed to addColorStop. Code: ${e.code}, message: ${e.message}`);
          }
          this.context.fillStyle = gradSRGB
          this.context.fillRect(10, 10, 150, 150)

          // 设置fillStyle为DISPLAY_P3色域效果的gradient
          let gradP3 = this.context.createLinearGradient(245, 10, 320, 110)
          // 使用try catch对可能出现的异常进行捕获
          try {
            gradP3.addColorStop(0.0, ColorMetrics.colorWithSpace(ColorSpace.DISPLAY_P3, 1.0, 0.0, 0.0, 1.0))
            gradP3.addColorStop(0.5, ColorMetrics.colorWithSpace(ColorSpace.DISPLAY_P3, 1.0, 1.0, 1.0, 1.0))
            gradP3.addColorStop(1.0, ColorMetrics.colorWithSpace(ColorSpace.DISPLAY_P3, 0.0, 1.0, 0.0, 1.0))
          } catch (error) {
            let e: BusinessError = error as BusinessError;
            console.error(`Failed to addColorStop. Code: ${e.code}, message: ${e.message}`);
          }
          this.context.fillStyle = gradP3
          this.context.fillRect(170, 10, 150, 150)
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

从API版本26.0.0开始，[addColorStop](#addcolorstop)接口新增支持通过ColorMetrics类型入参进行HDR提亮。

```TypeScript
// xxx.ets
import { ColorMetrics } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct CanvasGradientDemo {
  private settings: RenderingContextSettings = new RenderingContextSettings(true);
  private context: CanvasRenderingContext2D = new CanvasRenderingContext2D(this.settings);

  build() {
    Column({ space: 30 }) {
      Canvas(this.context)
        .width(340)
        .height(240)
        .onReady(() => {
          // HDR渐变支持超出1.0的亮度值，在支持HDR的设备上，右侧高光区域会比左侧更亮
          this.drawCanvas();
        })
    }
    .width('100%')
    .height('100%')
    .justifyContent(FlexAlign.Center)
  }

  private drawCanvas() {
    // 左侧：SDR渐变，红 -> 白 -> 绿
    let gradSDR = this.context.createLinearGradient(20, 20, 160, 160)
    try {
      gradSDR.addColorStop(0.0, ColorMetrics.colorWithSpace(ColorSpace.SRGB, 1.0, 0.0, 0.0, 1.0)) // 红色
      gradSDR.addColorStop(0.5, ColorMetrics.colorWithSpace(ColorSpace.SRGB, 1.0, 1.0, 1.0, 1.0)) // 白色
      gradSDR.addColorStop(1.0, ColorMetrics.colorWithSpace(ColorSpace.SRGB, 0.0, 1.0, 0.0, 1.0)) // 绿色
    } catch (error) {
      let e: BusinessError = error as BusinessError;
      console.error(`SDR Failed to addColorStop. Code: ${e.code}, message: ${e.message}`);
    }
    this.context.fillStyle = gradSDR
    this.context.fillRect(10, 10, 150, 150)

    this.context.fillStyle = '#FFFFFF'
    this.context.font = '16px sans-serif'
    this.context.textAlign = 'center'
    this.context.fillText("SDR", 85, 190)

    // 右侧：HDR渐变，红 -> 高亮白(亮度1.5) -> 绿
    let gradHDR = this.context.createLinearGradient(190, 20, 330, 160)
    try {
      gradHDR.addColorStop(0.0, ColorMetrics.createHDRColor(ColorSpace.BT2020, 1.0, 0.0, 0.0, 1.0)) // 红色
      gradHDR.addColorStop(0.5, ColorMetrics.createHDRColor(ColorSpace.BT2020, 1.5, 1.5, 1.5, 1.0)) // 高亮白色
      gradHDR.addColorStop(1.0, ColorMetrics.createHDRColor(ColorSpace.BT2020, 0.0, 1.0, 0.0, 1.0)) // 绿色
    } catch (error) {
      let e: BusinessError = error as BusinessError;
      console.error(`HDR Failed to addColorStop. Code: ${e.code}, message: ${e.message}`);
    }
    this.context.fillStyle = gradHDR
    this.context.fillRect(180, 10, 150, 150)

    this.context.fillStyle = '#FFFFFF'
    this.context.fillText("HDR", 255, 190)
  }
}
```

