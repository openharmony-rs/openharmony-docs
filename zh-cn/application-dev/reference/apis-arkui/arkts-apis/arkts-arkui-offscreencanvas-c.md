# OffscreenCanvas

OffscreenCanvas组件用于绘制自定义图形。使用[Canvas](arkts-arkui-canvas-con.md)组件或 [CanvasRenderingContext2D](arkts-arkui-canvasrenderingcontext2d-c.md) 对象时，渲染、动画和用户交互通常发生在应用程序的主线程上，与画布动画和渲染相关的计算可能会影响 应用程序性能。OffscreenCanvas提供了一个可以在屏幕外渲染的画布，这样可以在单独的线程中运行一些任务， 从而避免影响应用程序主线程性能。

> **说明：**
> 
> OffscreenCanvas无法在ServiceExtensionAbility中使用，ServiceExtensionAbility中建议使用
> [Drawing模块](../../apis-arkgraphics2d/arkts-apis/arkts-graphics-drawing.md)
> 进行离屏绘制。
## 子组件不支持。@extends CanvasRenderer [since 8 - 10]

**起始版本：** 8

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## constructor

```TypeScript
constructor(width: number, height: number)
```

构造用于创建离屏画布对象的OffscreenCanvas。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| width | number | 是 | OffscreenCanvas组件的宽度。 异常值NaN和Infinity按无效值处理。 默认单位为vp。 |
| height | number | 是 | OffscreenCanvas组件的高度。 异常值NaN和Infinity按无效值处理。 默认单位为vp。 |

**示例**

以下示例展示了配置CanvasRenderingContext2D对象的单位模式，默认单位模式为LengthMetricsUnit.DEFAULT，对应默认单位vp，配置后无法动态更改。详细说明见LengthMetricsUnit。

```TypeScript
// xxx.ets
import { LengthMetricsUnit } from '@kit.ArkUI'

@Entry
@Component
struct LengthMetricsUnitDemo {
  private settings: RenderingContextSettings = new RenderingContextSettings(true);
  private contextPX: CanvasRenderingContext2D = new CanvasRenderingContext2D(this.settings, LengthMetricsUnit.PX);
  private contextVP: CanvasRenderingContext2D = new CanvasRenderingContext2D(this.settings);

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Canvas(this.contextPX)
        .width('100%')
        .height(150)
        .backgroundColor('#ffff00')
        .onReady(() => {
          // 使用px单位模式绘制图形
          this.contextPX.fillRect(10, 10, 100, 100)
          this.contextPX.clearRect(10, 10, 50, 50)
        })

      Canvas(this.contextVP)
        .width('100%')
        .height(150)
        .backgroundColor('#ffff00')
        .onReady(() => {
          this.contextVP.fillRect(10, 10, 100, 100)
          this.contextVP.clearRect(10, 10, 50, 50)
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

## constructor

```TypeScript
constructor(width: number, height: number, unit: LengthMetricsUnit)
```

构造用于创建离屏画布对象的OffscreenCanvas，支持配置OffscreenCanvas的单位模式。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| width | number | 是 | OffscreenCanvas组件的宽度。 异常值NaN和Infinity按无效值处理。 默认单位为vp。 |
| height | number | 是 | OffscreenCanvas组件的高度。 异常值NaN和Infinity按无效值处理。 默认单位为vp。 |
| unit | LengthMetricsUnit | 是 | 用来配置OffscreenCanvas对象的单位模式，配置后无法动态更改， 配置方法同 [CanvasRenderingContext2D](arkts-arkui-canvasrenderingcontext2d-c.md)。 异常值NaN和Infinity按默认值处理。 默认值：DEFAULT。 |

**示例**

参见 [constructor](#constructor)

## getContext

```TypeScript
getContext(contextType: "2d", options?: RenderingContextSettings): OffscreenCanvasRenderingContext2D
```

返回OffscreenCanvas组件的绘图上下文。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| contextType | "2d" | 是 | OffscreenCanvas组件绘图上下文的类型，当前仅支持"2d"类型。 "2d"：创建一个表示二维渲染上下文的OffscreenCanvasRenderingContext2D对象。 异常值undefined和null按无效值处理，当前接口返回undefined。 |
| options | [RenderingContextSettings](arkts-arkui-renderingcontextsettings-c.md) | 否 | 用来配置OffscreenCanvasRenderingContext2D对象的参数， 见[RenderingContextSettings](arkts-arkui-renderingcontextsettings-c.md)。 异常值undefined和null按RenderingContextSettings的默认值处理。 默认值：null。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [OffscreenCanvasRenderingContext2D](arkts-arkui-offscreencanvasrenderingcontext2d-c.md) | OffscreenCanvas组件的绘图上下文。 如果getContext方法的入参contextType为"2d"以外类型（包括null或者undefined），返回undefined， 使用前应判断返回值是否为undefined。 |

**示例**

```TypeScript
@Entry
@Component
struct OffscreenCanvasExamplePage {
  private settings: RenderingContextSettings = new RenderingContextSettings(true);
  private context: CanvasRenderingContext2D = new CanvasRenderingContext2D(this.settings);
  private offscreenCanvas: OffscreenCanvas = new OffscreenCanvas(600, 800);

  build() {
    Flex({ direction: FlexDirection.Row, alignItems: ItemAlign.Start, justifyContent: FlexAlign.Start }) {
      Column() {
        Canvas(this.context)
          .width('100%')
          .height('100%')
          .backgroundColor('#FFFFFF')
          .onReady(() => {
            let offContext = this.offscreenCanvas.getContext("2d", this.settings)
            offContext.font = '70px sans-serif'
            offContext.fillText('Offscreen : Hello World!', 20, 60)
            offContext.fillStyle = '#0000ff'
            offContext.fillRect(230, 350, 50, 50)
            offContext.fillStyle = '#EE0077'
            offContext.translate(70, 70)
            offContext.fillRect(230, 350, 50, 50)
            offContext.fillStyle = '#77EE0077'
            offContext.translate(-70, -70)
            offContext.fillStyle = '#00ffff'
            offContext.rotate(45 * Math.PI / 180);
            offContext.fillRect(180, 120, 50, 50);
            offContext.rotate(-45 * Math.PI / 180);
            offContext.beginPath()
            offContext.moveTo(10, 150)
            offContext.bezierCurveTo(20, 100, 200, 100, 200, 20)
            offContext.stroke()
            offContext.fillStyle = '#FF00FF'
            offContext.fillRect(100, 100, 60, 60)
            let imageData = this.offscreenCanvas.transferToImageBitmap()
            this.context.transferFromImageBitmap(imageData)
          })
      }.width('100%').height('100%')
    }
    .width('100%')
    .height('100%')
  }
}
```

## transferToImageBitmap

```TypeScript
transferToImageBitmap(): ImageBitmap
```

从OffscreenCanvas组件中最近渲染的图像创建一个ImageBitmap对象。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ImageBitmap](arkts-arkui-imagebitmap-c.md) | 创建的ImageBitmap对象。 |

**示例**

```TypeScript
// xxx.ets
@Entry
@Component
struct OffscreenCanvasPage {
  private settings: RenderingContextSettings = new RenderingContextSettings(true);
  private context: CanvasRenderingContext2D = new CanvasRenderingContext2D(this.settings);
  private offCanvas: OffscreenCanvas = new OffscreenCanvas(400, 600);

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Canvas(this.context)
        .width('100%')
        .height('100%')
        .borderWidth(5)
        .borderColor('rgb(39,135,217)')
        .backgroundColor('#FFFFFF')
        .onReady(() => {
          let offContext = this.offCanvas.getContext("2d", this.settings)
          offContext.fillStyle = '#CDCDCD'
          offContext.fillRect(0, 0, 400, 600)
          offContext.fillStyle = '#000000'
          offContext.font = '40px serif bold'
          offContext.fillText('Offscreen : Hello World!', 20, 60)
          let image = this.offCanvas.transferToImageBitmap()
          this.context.transferFromImageBitmap(image)
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

```TypeScript
// xxx.ets
@Entry
@Component
struct PutImageData {
  private settings: RenderingContextSettings = new RenderingContextSettings(true);
  private context: CanvasRenderingContext2D = new CanvasRenderingContext2D(this.settings);
  private offCanvas: OffscreenCanvas = new OffscreenCanvas(600, 600);

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Canvas(this.context)
        .width('100%')
        .height('100%')
        .backgroundColor('rgb(213,213,213)')
        .onReady(() => {
          let offContext = this.offCanvas.getContext("2d", this.settings)
          let imageData = offContext.createImageData(100, 100)
          for (let i = 0; i < imageData.data.length; i += 4) {
            imageData.data[i + 0] = 112
            imageData.data[i + 1] = 112
            imageData.data[i + 2] = 112
            imageData.data[i + 3] = 255
          }
          offContext.putImageData(imageData, 10, 10)
          let image = this.offCanvas.transferToImageBitmap()
          this.context.transferFromImageBitmap(image)
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

## height

```TypeScript
height: number
```

OffscreenCanvas组件的高度。 默认单位为vp。

**类型：** number

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例**

```TypeScript
// xxx.ets
@Entry
@Component
struct OffscreenCanvasPage {
  private settings: RenderingContextSettings = new RenderingContextSettings(true);
  private context: CanvasRenderingContext2D = new CanvasRenderingContext2D(this.settings);
  private offCanvas: OffscreenCanvas = new OffscreenCanvas(200, 300);

  build() {
    Flex({ direction: FlexDirection.Row, alignItems: ItemAlign.Start, justifyContent: FlexAlign.Start }) {
      Column() {
        Canvas(this.context)
          .width('100%')
          .height('100%')
          .borderWidth(5)
          .borderColor('#057D02')
          .backgroundColor('#FFFFFF')
          .onReady(() => {
            let offContext = this.offCanvas.getContext("2d", this.settings)
            offContext.fillStyle = '#CDCDCD'
            offContext.fillRect(0, 0, 100, this.offCanvas.height)
            let image = this.offCanvas.transferToImageBitmap()
            this.context.setTransform(1, 0, 0, 1, 50, 200)
            this.context.transferFromImageBitmap(image)
          })
      }
    }.width('100%').height('100%')
  }
}
```

## width

```TypeScript
width: number
```

OffscreenCanvas组件的宽度。 默认单位为vp。

**类型：** number

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例**

```TypeScript
// xxx.ets
@Entry
@Component
struct OffscreenCanvasPage {
  private settings: RenderingContextSettings = new RenderingContextSettings(true);
  private context: CanvasRenderingContext2D = new CanvasRenderingContext2D(this.settings);
  private offCanvas: OffscreenCanvas = new OffscreenCanvas(200, 300);

  build() {
    Flex({ direction: FlexDirection.Row, alignItems: ItemAlign.Start, justifyContent: FlexAlign.Start }) {
      Column() {
        Canvas(this.context)
          .width('100%')
          .height('100%')
          .borderWidth(5)
          .borderColor('#057D02')
          .backgroundColor('#FFFFFF')
          .onReady(() => {
            let offContext = this.offCanvas.getContext("2d", this.settings)
            offContext.fillStyle = '#CDCDCD'
            offContext.fillRect(0, 0, this.offCanvas.width, 150)
            let image = this.offCanvas.transferToImageBitmap()
            this.context.setTransform(1, 0, 0, 1, 50, 200)
            this.context.transferFromImageBitmap(image)
          })
      }
    }.width('100%').height('100%')
  }
}
```
