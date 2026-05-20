# ExtendableImage（可扩展的Image）
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zany_pink-->
<!--Designer: @shiyu_huang_plus-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

[Image](./ts-basic-components-image.md)的扩展组件的基类。开发者可以自定义扩展组件继承ExtendableImage，支持重写Image中的[属性](./ts-basic-components-image.md#属性)和[通用属性](./ts-component-general-attributes.md)，同时支持自定义属性。在阅读本文档前，建议提前阅读[Image](./ts-basic-components-image.md)。

**起始版本：** 26.0.0

>  **说明：**
>
>  本模块仅支持ArkTS-Sta。

## 导入模块

```ts
import { ExtendableImage } from '@kit.ArkUI';
```

## 子组件

无。

## 属性

自定义的Image扩展组件类支持重写Image的[属性](./ts-basic-components-image.md#属性)和[通用属性](./ts-component-general-attributes.md)，若不重写，则遵循对应属性的默认行为。此外，扩展组件类支持以下属性和自定义属性。

### setImageOptions

setImageOptions(src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent | undefined, imageAIOptions?: ImageAIOptions): this

设置图片配置参数。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS模式：** 该接口适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型                                    | 必填 | 说明                 |
| ------- | --------------------------------------- | ---- | -------------------- |
| src | [PixelMap](ts-image-common.md#pixelmap) \| [ResourceStr](ts-types.md#resourcestr) \| [DrawableDescriptor](ts-basic-components-image.md#drawabledescriptor10) \| [ImageContent](./ts-basic-components-image.md#imagecontent12) \| undefined | 是   | 图片的数据源，支持本地图片和网络图片。 |
| imageAIOptions | [ImageAIOptions](ts-image-common.md#imageaioptions12) | 否   | AI分析器选项。<br/> 未设置时，则按照imageAIOptions中各参数的默认值配置。 |

### setImageOptions

setImageOptions(src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent | undefined, imageAIOptions?: ImageAIOptions, reloadKey?: string): this

设置图片配置参数。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS模式：** 该接口适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型                                    | 必填 | 说明                 |
| ------- | --------------------------------------- | ---- | -------------------- |
| src | [PixelMap](ts-image-common.md#pixelmap) \| [ResourceStr](ts-types.md#resourcestr) \| [DrawableDescriptor](ts-basic-components-image.md#drawabledescriptor10) \| [ImageContent](./ts-basic-components-image.md#imagecontent12) \| undefined | 是   | 图片的数据源，支持本地图片和网络图片。 |
| imageAIOptions | [ImageAIOptions](ts-image-common.md#imageaioptions12) | 否   | AI分析器选项。<br/> 未设置时，则按照imageAIOptions中各参数的默认值配置。 |
| reloadKey | string | 否   | 图片重新加载的标识。当reloadKey的值发生变化时，将不使用缓存重新加载图片。适用于图片源地址不变但图片内容已更新的场景（例如本地图片内容被重写）。<br/>默认值：空字符串。 |

### setImageOptions

setImageOptions(src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent | undefined, reloadKey?: string): this

设置图片配置参数。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**模型约束：** 此接口仅可在Stage模型下使用。

**ArkTS模式：** 该接口适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型                                    | 必填 | 说明                 |
| ------- | --------------------------------------- | ---- | -------------------- |
| src | [PixelMap](ts-image-common.md#pixelmap) \| [ResourceStr](ts-types.md#resourcestr) \| [DrawableDescriptor](ts-basic-components-image.md#drawabledescriptor10) \| [ImageContent](./ts-basic-components-image.md#imagecontent12) \| undefined | 是   | 图片的数据源，支持本地图片和网络图片。 |
| reloadKey | string | 否   | 图片重新加载的标识。当reloadKey的值发生变化时，将不使用缓存重新加载图片。适用于图片源地址不变但图片内容已更新的场景（例如本地图片内容被重写）。<br/>默认值：空字符串。 |

## 事件

支持Image的[事件](./ts-basic-components-image.md#事件)和[通用事件](ts-component-general-events.md)。

## 示例

```ts
'use static'

import { ExtendableImage, Length, LayoutPolicy, Entry, Component, Column, ImageAIOptions, PixelMap, ResourceStr, ImageContent, ImageFit, Alignment, Color, $r } from '@kit.ArkUI';

class MyImage extends ExtendableImage {
  // 通用属性
  width(): this {
    super.width('100%');
    return this;
  }

  // 自定义属性
  newAttribute(): this {
    super.height('50%');
    super.margin(15)
    return this;
  }
}

@Entry
@Component
struct Index {
  build() {
    Column() {
      // 调用扩展组件
      MyImage($r('app.media.startIcon'))
        .width() // 调用重写属性
        .newAttribute() // 调用自定义属性
        .overlay('png', { align: Alignment.Bottom, offset: { x: 0, y: 20 } })
        .border({ width: 2, color: Color.Pink })
        .objectFit(ImageFit.TOP_START)
    }
  }
}
```

