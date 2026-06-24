# Image

定义图片组件实例.


## Image

```TypeScript
Image(src: PixelMap | ResourceStr | DrawableDescriptor)
```

通过图片数据源获取图片，用于后续渲染展示。

Image组件加载图片失败或图片尺寸为0时，图片组件大小自动为0，不跟随父组件的布局约束。

Image组件默认按照居中裁剪，例如组件宽高设置相同，原图长宽不等，此时按照中间区域进行裁剪。

Image加载成功且组件不设置宽高时，其显示大小自适应父组件。

> **说明：**
>
> - Image直接传入URL可能会带来的潜在性能问题，例如：(1) 大图加载时无法提前下载，
> 白块显示的时间较长；(2) 小图设置同步
> 加载，在弱网环境下，可能会阻塞UI线程造成冻屏问题；(3) 在快速滑动的瀑布流中，
> 无法提前对即将要显示的图片进行下载，
> 导致滑动白块较多。不同场景下，性能问题会有不同的表现，建议将网络下载部分与Image的显示剥离，可提前下载或者异步
> 下载。如果图片加载过程中出现白色块，请参考
> [Image白块解决方案]
> (https://developer.huawei.com/consumer/cn/doc/best-practices/bpta-image-white-lump-solution)。
> 如果图片加载时间过长，请参考
> [预置图片资源加载优化](https://developer.huawei.com/consumer/cn/doc/best-practices/bpta-texture-compression-
> improve-performance)。
>
> - src由有效值（可正常解析并加载的图片资源）切换为无效值（无法解析或加载的图片路径）时，组件保持显示此前成功加载
> 的图片内容，不进行清除或重置操作。
>
> - 当Image组件入参为[PixelMap]{@link @ohos.multimedia.image:image.PixelMap}类型时，
> 只有当PixelMap对象发生变化（即指向一个新的PixelMap实例），Image组件才能感知到数据的变化。
> 仅修改PixelMap对象的内容（如像素值）而不更换对象引用，无法触发数据变化的感知。
>
> - Image组件入参为Base64字符串时，Base64字符串通用格式为`data:image/subtype;base64,Base64EncodedData`，
> 其中subtype为类型声明，Base64 EncodedData为数据对应的base64编码，其他为固定字符串。
> 例如：png图像对应的入参为`data:image/png;base64,iVBORw0KGgo...`。
>
> 1. image/subType用于声明数据内容的类型。从API版本26.0.0开始，Image组件接受任意`data:image/xxx;base64,
> Base64EncodedData`格式的Base64字符串，具
> 体图片类型由系统多媒体能力根据实际数据内容识别，无需枚举所有支持的MIME类型。对于API版本26.0.0之前版本，
> Image组件不会强制校验声明的类型与Base64解码后的实际图片格式是否完全一致。在部分场景下，
> 即使声明的类型与真实格
> 式不一致，图片仍可能正常显示。为避免未来行为变化或未知问题，建议始终保持类型与实际图片格式一致。
>
> 2. Image组件从API版本26.0.0开始支持通过`data:image/*;base64,Base64EncodedData`的通配写法，对于API版本26.0.0之前
> 版本，Image组件不支持`data:image/*;base64,Base64EncodedData`的通配写法，subType必须显式声明具体的图片类型。
>
> 3. Image组件从API版本26.0.0开始支持通过Base64加载SVG图片，对于API版本26.0.0之前版本，
> Image组件不支持通过Base64字符串形式加载SVG图片。

**起始版本：** 7

**ArkTS模式:** 仅支持ArkTS-Dyn，ArkTS-Dyn起始版本为7.

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | PixelMap | ResourceStr | DrawableDescriptor | 是 |  |

## Image

```TypeScript
Image(src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent)
```

src新增[ImageContent]{@link ImageContent}类型，可指定对应的图形内容。

**起始版本：** 12

**ArkTS模式:** 仅支持ArkTS-Dyn，ArkTS-Dyn起始版本为12.

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | PixelMap | ResourceStr | DrawableDescriptor | ImageContent | 是 |  |

## Image

```TypeScript
Image(src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent, reloadKey?: string)
```

获取图片，支持通过reloadKey参数触发图片重新加载。当reloadKey的值发生变化时，将不使用缓存重新加载图片。

**起始版本：** 26.0.0

**ArkTS模式:** 仅支持ArkTS-Dyn，ArkTS-Dyn起始版本为26.0.0.

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | PixelMap | ResourceStr | DrawableDescriptor | ImageContent | 是 |  |
| reloadKey | string | 否 |  |

## Image

```TypeScript
Image(src: PixelMap | ResourceStr | DrawableDescriptor, imageAIOptions: ImageAIOptions)
```

Image新增[ImageAIOptions]{@link ImageAIOptions}参数，为组件设置AI分析选项。

**起始版本：** 12

**ArkTS模式:** 仅支持ArkTS-Dyn，ArkTS-Dyn起始版本为12.

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | PixelMap | ResourceStr | DrawableDescriptor | 是 |  |
| imageAIOptions | ImageAIOptions | 是 |  |

## Image

```TypeScript
Image(src: PixelMap | ResourceStr | DrawableDescriptor,
      imageAIOptions?: ImageAIOptions, reloadKey?: string)
```

获取图片，支持通过[ImageAIOptions]{@link ImageAIOptions}参数设置AI分析选项。当reloadKey的值发生变化时，
将不使用缓存重新加载图片。

**起始版本：** 26.0.0

**ArkTS模式:** 仅支持ArkTS-Dyn，ArkTS-Dyn起始版本为26.0.0.

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | PixelMap | ResourceStr | DrawableDescriptor | 是 |  |
| imageAIOptions | ImageAIOptions | 否 |  |
| reloadKey | string | 否 |  |

## 汇总

- [ImageAlt](arkts-arkui-image-imagealt-i.md)
- [ImageError](arkts-arkui-image-imageerror-i.md)
- [ImageSourceSize](arkts-arkui-image-imagesourcesize-i.md)
- [ResizableOptions](arkts-arkui-image-resizableoptions-i.md)
- [BusinessError](arkts-arkui-image-businesserror-t.md)
- [DrawableDescriptor](arkts-arkui-image-drawabledescriptor-t.md)
- [DrawingColorFilter](arkts-arkui-image-drawingcolorfilter-t.md)
- [DrawingLattice](arkts-arkui-image-drawinglattice-t.md)
- [ImageErrorCallback](arkts-arkui-image-imageerrorcallback-t.md)
- [ImageMatrix](arkts-arkui-image-imagematrix-t.md)
- [RequestDownloadInfo](arkts-arkui-image-requestdownloadinfo-t.md)
- [ResolutionQuality](arkts-arkui-image-resolutionquality-t-sys.md)
- [DynamicRangeMode](arkts-arkui-image-dynamicrangemode-e.md)
- [ImageContent](arkts-arkui-image-imagecontent-e.md)
- [ImageInterpolation](arkts-arkui-image-imageinterpolation-e.md)
- [ImageRenderMode](arkts-arkui-image-imagerendermode-e.md)
- [ImageRotateOrientation](arkts-arkui-image-imagerotateorientation-e.md)
