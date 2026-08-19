# Image

## Image

```TypeScript
@ComponentBuilder
export declare function Image(
    src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent | undefined,
    imageAIOptions?: ImageAIOptions
): ImageAttribute
```

Defines the Image component.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function Image(    src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent | undefined,    imageAIOptions?: ImageAIOptions): ImageAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function Image(    src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent | undefined,    imageAIOptions?: ImageAIOptions): ImageAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | [PixelMap](../../apis-arkui/arkts-components/arkts-arkui-pixelmap-t.md) \| [ResourceStr](../../apis-arkui/arkts-apis/arkts-arkui-resourcestr-t.md) \| [DrawableDescriptor](../../apis-arkui/arkts-apis/arkts-arkui-arkui-drawabledescriptor-drawabledescriptor-c.md) \| [ImageContent](arkts-na-image-imagecontent-e.md) \| undefined | 是 | image resource type. |
| imageAIOptions | [ImageAIOptions](arkts-na-imagecommon-imageaioptions-i.md) | 否 | Options for AI analyzer. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ImageAttribute | The attribute of the Image. |


## Image

```TypeScript
@ComponentBuilder
export declare function Image(
    src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent | undefined,
    imageAIOptions?: ImageAIOptions,
    reloadKey?: string
): ImageAttribute
```

定义Image组件。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function Image(    src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent | undefined,    imageAIOptions?: ImageAIOptions,    reloadKey?: string): ImageAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function Image(    src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent | undefined,    imageAIOptions?: ImageAIOptions,    reloadKey?: string): ImageAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | [PixelMap](../../apis-arkui/arkts-components/arkts-arkui-pixelmap-t.md) \| [ResourceStr](../../apis-arkui/arkts-apis/arkts-arkui-resourcestr-t.md) \| [DrawableDescriptor](../../apis-arkui/arkts-apis/arkts-arkui-arkui-drawabledescriptor-drawabledescriptor-c.md) \| [ImageContent](arkts-na-image-imagecontent-e.md) \| undefined | 是 | 图片资源类型。 |
| imageAIOptions | [ImageAIOptions](arkts-na-imagecommon-imageaioptions-i.md) | 否 | AI分析器的参数。 |
| reloadKey | string | 否 | 用于图像重新加载的选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ImageAttribute | Image的属性。 |


## Image

```TypeScript
@ComponentBuilder
export declare function Image(
    src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent | undefined,
    reloadKey?: string
): ImageAttribute
```

定义Image组件。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@ComponentBuilderexport declare function Image(    src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent | undefined,    reloadKey?: string): ImageAttribute--><!--Device-unnamed-@ComponentBuilderexport declare function Image(    src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent | undefined,    reloadKey?: string): ImageAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | [PixelMap](../../apis-arkui/arkts-components/arkts-arkui-pixelmap-t.md) \| [ResourceStr](../../apis-arkui/arkts-apis/arkts-arkui-resourcestr-t.md) \| [DrawableDescriptor](../../apis-arkui/arkts-apis/arkts-arkui-arkui-drawabledescriptor-drawabledescriptor-c.md) \| [ImageContent](arkts-na-image-imagecontent-e.md) \| undefined | 是 | 图片资源类型。 |
| reloadKey | string | 否 | 用于图像重新加载的选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ImageAttribute | The attribute of the Image. |


## Image

```TypeScript
@Builder
export declare function Image(style: CustomBuilderT<ImageAttribute>): ImageAttribute
```

定义Image组件。它需要在组件属性设置开始时调用setImageOptions。 它需要在组件属性设置结束时调用applyAttributeFinish。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Builderexport declare function Image(style: CustomBuilderT<ImageAttribute>): ImageAttribute--><!--Device-unnamed-@Builderexport declare function Image(style: CustomBuilderT<ImageAttribute>): ImageAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | CustomBuilderT&lt;ImageAttribute&gt; | 是 | 设置组件属性的回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ImageAttribute | Image的属性。 |

