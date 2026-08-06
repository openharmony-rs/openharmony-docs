# Image

## Image

```TypeScript
export declare function Image(
    src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent | undefined,
    imageAIOptions?: ImageAIOptions
): ImageAttribute
```

Defines the Image component.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export declare function Image(    src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent | undefined,    imageAIOptions?: ImageAIOptions): ImageAttribute--><!--Device-unnamed-export declare function Image(    src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent | undefined,    imageAIOptions?: ImageAIOptions): ImageAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| ResourceStr \| DrawableDescriptor \| ImageContent \| undefined | 是 | image resource type. |
| imageAIOptions | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | Options for AI analyzer. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | The attribute of the Image. |


## Image

```TypeScript
export declare function Image(
    src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent | undefined,
    imageAIOptions?: ImageAIOptions,
    reloadKey?: string
): ImageAttribute
```

定义Image组件。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export declare function Image(    src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent | undefined,    imageAIOptions?: ImageAIOptions,    reloadKey?: string): ImageAttribute--><!--Device-unnamed-export declare function Image(    src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent | undefined,    imageAIOptions?: ImageAIOptions,    reloadKey?: string): ImageAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| ResourceStr \| DrawableDescriptor \| ImageContent \| undefined | 是 | 图片资源类型。 |
| imageAIOptions | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | AI分析器的参数。 |
| reloadKey | string | 否 | 用于图像重新加载的选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | Image的属性。 |


## Image

```TypeScript
export declare function Image(
    src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent | undefined,
    reloadKey?: string
): ImageAttribute
```

定义Image组件。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export declare function Image(    src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent | undefined,    reloadKey?: string): ImageAttribute--><!--Device-unnamed-export declare function Image(    src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent | undefined,    reloadKey?: string): ImageAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| ResourceStr \| DrawableDescriptor \| ImageContent \| undefined | 是 | 图片资源类型。 |
| reloadKey | string | 否 | 用于图像重新加载的选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | The attribute of the Image. |


## Image

```TypeScript
export declare function Image(style: CustomBuilderT<ImageAttribute>): ImageAttribute
```

定义Image组件。它需要在组件属性设置开始时调用setImageOptions。 它需要在组件属性设置结束时调用applyAttributeFinish。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**装饰器类型：** @Builder

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export declare function Image(style: CustomBuilderT<ImageAttribute>): ImageAttribute--><!--Device-unnamed-export declare function Image(style: CustomBuilderT<ImageAttribute>): ImageAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;\_\_\_MD\_LINK\_USD\_1\_\_\_&gt; | 是 | 设置组件属性的回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | Image的属性。 |

