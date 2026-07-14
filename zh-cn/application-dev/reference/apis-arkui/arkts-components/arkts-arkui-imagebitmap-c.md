# ImageBitmap

ImageBitmap对象可以存储canvas渲染的像素数据。从API version 11开始，当应用创建
[Worker线程](../../../../arkts-utils/worker-introduction.md)，支持使用postMessage将ImageBitmap实例传到
Worker中进行绘制，并使用onmessage接收Worker线程发送的绘制结果进行显示。

**起始版本：** 8

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## close

```TypeScript
close(): void
```

释放ImageBitmap对象相关联的所有图形资源，并将ImageBitmap对象的宽高置为0。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(src: string)
```

通过ImageSrc创建ImageBitmap对象。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | string | 是 | 图片的数据源支持本地图片。<br>1、string格式用于加载本地图片，例如ImageBitmap("common/images/example.jpg")，type为"entry"和"feature"类型的Module，其图片加载路径的起点为当前Module的ets文件夹，type为"har"和"shared"类型的Module，其图片加载路径的起点为当前构建的"entry"或"feature"类型Module的ets文件夹。<br/>type为"har"和"shared"类型的Module中推荐使用[ImageSource](../../../../media/image/image-decoding.md)图片解码方式将资源图片解码为统一的PixelMap加载使用。<br>2、支持本地图片类型：bmp、jpg、png、svg和webp类型。<br/>**说明：**<br/>- ArkTS卡片上不支持`http://`等网络相关路径前缀、`datashare://`路径前缀以及`file://data/storage`路径前缀的字符串。 |

## constructor

```TypeScript
constructor(src: string, unit: LengthMetricsUnit)
```

通过ImageSrc创建ImageBitmap对象，支持使用unit配置ImageBitmap对象的单位模式。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | string | 是 | 图片的数据源支持本地图片。<br>1、string格式用于加载本地图片，例如ImageBitmap("common/images/example.jpg")，type为"entry"和"feature"类型的Module，其图片加载路径的起点为当前Module的ets文件夹，type为"har"和"shared"类型的Module，其图片加载路径的起点为当前构建的"entry"或"feature"类型Module的ets文件夹。<br/>type为"har"和"shared"类型的Module中推荐使用[ImageSource](../../../../media/image/image-decoding.md)图片解码方式将资源图片解码为统一的PixelMap加载使用。<br>2、支持本地图片类型：bmp、jpg、png、svg和webp类型。<br/>**说明：**<br/>- ArkTS卡片上不支持`http://`等网络相关路径前缀、`datashare://`路径前缀以及`file://data/storage`路径前缀的字符串。 |
| unit | LengthMetricsUnit | 是 | 用来配置ImageBitmap对象的单位模式，配置后无法动态更改，配置方法同[CanvasRenderingContext2D](../../../../reference/apis-arkui/arkui-ts/ts-canvasrenderingcontext2d.md)。<br>异常值undefined、NaN和Infinity按默认值处理。 |

## constructor

```TypeScript
constructor(data: PixelMap)
```

通过PixelMap创建ImageBitmap对象。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | PixelMap | 是 | 图片的数据源支持PixelMap对象。 |

## constructor

```TypeScript
constructor(data: PixelMap, unit: LengthMetricsUnit)
```

通过PixelMap创建ImageBitmap对象，支持使用unit配置ImageBitmap对象的单位模式。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | PixelMap | 是 | 图片的数据源支持PixelMap对象。 |
| unit | LengthMetricsUnit | 是 | 用来配置ImageBitmap对象的单位模式，配置后无法动态更改，配置方法同[CanvasRenderingContext2D](../../../../reference/apis-arkui/arkui-ts/ts-canvasrenderingcontext2d.md)。 |

## constructor

```TypeScript
constructor(data: Resource, unit?: LengthMetricsUnit)
```

通过Resource创建ImageBitmap对象，支持使用unit配置ImageBitmap对象的单位模式。

**起始版本：** 26.0.0

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | Resource | 是 | 通过资源引用方式设置图片数据源。 |
| unit | LengthMetricsUnit | 否 | 用来配置ImageBitmap对象的单位模式，配置后无法动态更改。<br>默认值：LengthMetricsUnit.DEFAULT。 |

## height

```TypeScript
readonly height: number
```

ImageBitmap的像素高度。
<br>默认单位为vp。

**类型：** number

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
readonly width: number
```

ImageBitmap的像素宽度。
<br>默认单位为vp。

**类型：** number

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

