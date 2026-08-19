# ImageBitmap

ImageBitmap对象可以存储canvas渲染的像素数据。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class ImageBitmap--><!--Device-unnamed-export declare class ImageBitmap-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## close

```TypeScript
close(): void
```

释放ImageBitmap对象相关联的所有图形资源，并将ImageBitmap对象的宽高置为0。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageBitmap-close(): void--><!--Device-ImageBitmap-close(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(src: PixelMap | string, unit?: LengthMetricsUnit)
```

根据传入的图片路径或PixelMap对象创建ImageBitmap对象，支持使用unit配置ImageBitmap对象的单位模式。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageBitmap-constructor(src: PixelMap | string, unit?: LengthMetricsUnit)--><!--Device-ImageBitmap-constructor(src: PixelMap | string, unit?: LengthMetricsUnit)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | [PixelMap](../../apis-arkui/arkts-components/arkts-arkui-pixelmap-t.md) \| string | 是 | 图片的数据源支持本地图片或PixelMap对象。<br> 当类型为string时，用于加载本地图片，例如ImageBitmap("common/images/example.jpg")， type为"entry"和"feature"类型的Module，其图片加载路径的起点为当前Module的ets文件夹， type为"har"和"shared"类型的Module，其图片加载路径的起点为当前构建的"entry"或"feature" 类型Module的ets文件夹。<br> type为"har"和"shared"类型的Module中推荐使用 [ImageSource](../../../media/image/image-decoding.md)图片解码方式将资源图片解码为统一的 PixelMap加载使用。<br> 支持本地图片类型：bmp、jpg、png、svg和webp类型。<br> 当类型为[PixelMap](../../../apis-image-kit/arkts-apis-image-PixelMap.md)时， 图片的数据源支持PixelMap对象。 |
| unit | [LengthMetricsUnit](../../apis-arkui/arkts-apis/arkts-arkui-lengthmetricsunit-t.md) | 否 | 用来配置ImageBitmap对象的单位模式，配置后无法动态更改， 配置方法同[CanvasRenderingContext2D](../../../reference/apis-arkui/arkui-ts/ts-canvasrenderingcontext2d.md)。 <br>异常值undefined、NaN和Infinity按默认值处理。 |

## constructor

```TypeScript
constructor(src: Resource | PixelMap | string, unit?: LengthMetricsUnit)
```

根据传入的图片路径、PixelMap对象或Resource对象创建ImageBitmap对象， 支持使用unit配置ImageBitmap对象的单位模式。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageBitmap-constructor(src: Resource | PixelMap | string, unit?: LengthMetricsUnit)--><!--Device-ImageBitmap-constructor(src: Resource | PixelMap | string, unit?: LengthMetricsUnit)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | [Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-resource-i.md) \| [PixelMap](../../apis-arkui/arkts-components/arkts-arkui-pixelmap-t.md) \| string | 是 | 图片的数据源支持本地图片、PixelMap对象或Resource对象。 <br>当类型为string时，用于加载本地图片，例如ImageBitmap("common/images/example.jpg")， type为"entry"和"feature"类型的Module，其图片加载路径的起点为当前Module的ets文件夹， type为"har"和"shared"类型的Module，其图片加载路径的起点为当前构建的"entry"或"feature" 类型Module的ets文件夹。<br> type为"har"和"shared"类型的Module中推荐使用 [ImageSource](../../../media/image/image-decoding.md)图片解码方式将资源图片解码为统一的 PixelMap加载使用。<br> 支持本地图片类型：bmp、jpg、png、svg和webp类型。<br> 当类型为[PixelMap](../../../apis-image-kit/arkts-apis-image-PixelMap.md)时， 图片的数据源支持PixelMap对象。<br> 当类型为Resource时，图片的数据源支持Resource对象。 |
| unit | [LengthMetricsUnit](../../apis-arkui/arkts-apis/arkts-arkui-lengthmetricsunit-t.md) | 否 | 用来配置ImageBitmap对象的单位模式，配置后无法动态更改， 配置方法同[CanvasRenderingContext2D](../../../reference/apis-arkui/arkui-ts/ts-canvasrenderingcontext2d.md)。 <br>异常值undefined、NaN和Infinity按默认值处理。 |

