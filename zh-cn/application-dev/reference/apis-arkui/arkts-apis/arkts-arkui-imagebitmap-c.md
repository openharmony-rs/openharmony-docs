# ImageBitmap

ImageBitmap对象可以存储canvas渲染的像素数据。从API version 11开始，当应用创建 [Worker线程](../../../arkts-utils/worker-introduction.md)，支持使用postMessage将ImageBitmap实例传到 Worker中进行绘制，并使用onmessage接收Worker线程发送的绘制结果进行显示。

**起始版本：** 8

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## close

```TypeScript
close(): void
```

释放ImageBitmap对象相关联的所有图形资源，并将ImageBitmap对象的宽高置为0。

> **说明：**
> 
> - 必须与[constructor()](#constructor)方法配对
> 使用，创建ImageBitmap对象后，应在使用完毕时调用close()释放资源。未调用close()可能导致图形资源泄漏，影响应用性能。
> 
> - 建议在Canvas绘制完成后调用，如在[onReady](arkts-arkui-canvasattribute-c.md#onready)回调的最后调用close()。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(src: string)
```

通过ImageSrc创建ImageBitmap对象。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | string | 是 | 图片的数据源支持本地图片。 1、string格式用于加载本地图片，例如ImageBitmap("common/images/example.jpg")， type为"entry"和"feature"类型的Module，其图片加载路径的起点为当前Module的ets文件夹， type为"har"和"shared"类型的Module，其图片加载路径的起点为当前构建的"entry"或"feature"类型Module的ets文件夹。 type为"har"和"shared"类型的Module中推荐使用 [ImageSource](../../../media/image/image-decoding.md)图片解码方式将资源图片解码为统一的 PixelMap加载使用。 2、支持本地图片类型：bmp、jpg、png、svg和webp类型。    **说明：** - ArkTS卡片上不支持`http://`等网络相关路径前缀、`datashare://`路径前缀 以及`file://data/storage`路径前缀的字符串。 |

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
constructor(src: string, unit: LengthMetricsUnit)
```

通过ImageSrc创建ImageBitmap对象，支持使用unit配置ImageBitmap对象的单位模式。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | string | 是 | 图片的数据源支持本地图片。 1、string格式用于加载本地图片，例如ImageBitmap("common/images/example.jpg")， type为"entry"和"feature"类型的Module，其图片加载路径的起点为当前Module的ets文件夹， type为"har"和"shared"类型的Module，其图片加载路径的起点为当前构建的"entry"或"feature"类型Module的ets文件夹。 type为"har"和"shared"类型的Module中推荐使用 [ImageSource](../../../media/image/image-decoding.md)图片解码方式将资源图片解码为统一的 PixelMap加载使用。 2、支持本地图片类型：bmp、jpg、png、svg和webp类型。    **说明：** - ArkTS卡片上不支持`http://`等网络相关路径前缀、`datashare://`路径前缀 以及`file://data/storage`路径前缀的字符串。 |
| unit | LengthMetricsUnit | 是 | 用来配置ImageBitmap对象的单位模式，配置后无法动态更改， 配置方法同 [CanvasRenderingContext2D](arkts-arkui-canvasrenderingcontext2d-c.md)。 异常值undefined、NaN和Infinity按默认值处理。 |

**示例**

参见 [constructor](#constructor)

## constructor

```TypeScript
constructor(data: PixelMap)
```

通过PixelMap创建ImageBitmap对象。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | PixelMap | 是 | 图片的数据源支持PixelMap对象。 |

**示例**

参见 [constructor](#constructor)

## constructor

```TypeScript
constructor(data: PixelMap, unit: LengthMetricsUnit)
```

通过PixelMap创建ImageBitmap对象，支持使用unit配置ImageBitmap对象的单位模式。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | PixelMap | 是 | 图片的数据源支持PixelMap对象。 |
| unit | LengthMetricsUnit | 是 | 用来配置ImageBitmap对象的单位模式，配置后无法动态更改， 配置方法同 [CanvasRenderingContext2D](arkts-arkui-canvasrenderingcontext2d-c.md)。 |

**示例**

参见 [constructor](#constructor)

## constructor

```TypeScript
constructor(data: Resource, unit?: LengthMetricsUnit)
```

通过Resource创建ImageBitmap对象，支持使用unit配置ImageBitmap对象的单位模式。

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | Resource | 是 | 通过资源引用方式设置图片数据源。 |
| unit | LengthMetricsUnit | 否 | 用来配置ImageBitmap对象的单位模式，配置后无法动态更改。 默认值：LengthMetricsUnit.DEFAULT。 |

**示例**

参见 [constructor](#constructor)

## height

```TypeScript
readonly height: number
```

ImageBitmap的像素高度。 默认单位为vp。

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
readonly width: number
```

ImageBitmap的像素宽度。 默认单位为vp。

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
