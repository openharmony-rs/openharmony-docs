# ExtendableImage

扩展图像组件定义

**继承/实现关系：** ExtendableImage implements ImageAttribute

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export declare abstract class ExtendableImage--><!--Device-unnamed-export declare abstract class ExtendableImage-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## $_instantiate

```TypeScript
@ComponentBuilder
  static $_instantiate<T extends ExtendableImage>(
    factory: ConstructorT<T>, 
    src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent | undefined,
    imageAIOptions?: ImageAIOptions
  ): T
```

扩展图像组件构造器

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExtendableImage-@ComponentBuilder  static $_instantiate<T extends ExtendableImage>(    factory: ConstructorT<T>,     src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent | undefined,    imageAIOptions?: ImageAIOptions  ): T--><!--Device-ExtendableImage-@ComponentBuilder  static $_instantiate<T extends ExtendableImage>(    factory: ConstructorT<T>,     src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent | undefined,    imageAIOptions?: ImageAIOptions  ): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| factory | [ConstructorT](arkts-na-constructort-t.md)&lt;T&gt; | 是 |  |
| src | [PixelMap](../../apis-arkui/arkts-components/arkts-arkui-pixelmap-t.md) \| [ResourceStr](../../apis-arkui/arkts-apis/arkts-arkui-resourcestr-t.md) \| [DrawableDescriptor](../../apis-arkui/arkts-apis/arkts-arkui-arkui-drawabledescriptor-drawabledescriptor-c.md) \| [ImageContent](arkts-na-image-imagecontent-e.md) \| undefined | 是 |  |
| imageAIOptions | [ImageAIOptions](arkts-na-imagecommon-imageaioptions-i.md) | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T |  |

## $_instantiate

```TypeScript
@ComponentBuilder
  static $_instantiate<T extends ExtendableImage>(
    factory: ConstructorT<T>, 
    src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent | undefined,
    imageAIOptions?: ImageAIOptions,
    reloadKey?: string
  ): T
```

扩展图像组件构造器

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExtendableImage-@ComponentBuilder  static $_instantiate<T extends ExtendableImage>(    factory: ConstructorT<T>,     src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent | undefined,    imageAIOptions?: ImageAIOptions,    reloadKey?: string  ): T--><!--Device-ExtendableImage-@ComponentBuilder  static $_instantiate<T extends ExtendableImage>(    factory: ConstructorT<T>,     src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent | undefined,    imageAIOptions?: ImageAIOptions,    reloadKey?: string  ): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| factory | [ConstructorT](arkts-na-constructort-t.md)&lt;T&gt; | 是 |  |
| src | [PixelMap](../../apis-arkui/arkts-components/arkts-arkui-pixelmap-t.md) \| [ResourceStr](../../apis-arkui/arkts-apis/arkts-arkui-resourcestr-t.md) \| [DrawableDescriptor](../../apis-arkui/arkts-apis/arkts-arkui-arkui-drawabledescriptor-drawabledescriptor-c.md) \| [ImageContent](arkts-na-image-imagecontent-e.md) \| undefined | 是 |  |
| imageAIOptions | [ImageAIOptions](arkts-na-imagecommon-imageaioptions-i.md) | 否 |  |
| reloadKey | string | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T |  |

## $_instantiate

```TypeScript
@ComponentBuilder
  static $_instantiate<T extends ExtendableImage>(
    factory: ConstructorT<T>, 
    src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent | undefined,
    reloadKey?: string
  ): T
```

扩展图像组件

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExtendableImage-@ComponentBuilder  static $_instantiate<T extends ExtendableImage>(    factory: ConstructorT<T>,     src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent | undefined,    reloadKey?: string  ): T--><!--Device-ExtendableImage-@ComponentBuilder  static $_instantiate<T extends ExtendableImage>(    factory: ConstructorT<T>,     src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent | undefined,    reloadKey?: string  ): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| factory | [ConstructorT](arkts-na-constructort-t.md)&lt;T&gt; | 是 |  |
| src | [PixelMap](../../apis-arkui/arkts-components/arkts-arkui-pixelmap-t.md) \| [ResourceStr](../../apis-arkui/arkts-apis/arkts-arkui-resourcestr-t.md) \| [DrawableDescriptor](../../apis-arkui/arkts-apis/arkts-arkui-arkui-drawabledescriptor-drawabledescriptor-c.md) \| [ImageContent](arkts-na-image-imagecontent-e.md) \| undefined | 是 |  |
| reloadKey | string | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T |  |

## _instantiateImpl

```TypeScript
@Builder
  static _instantiateImpl<T extends ExtendableImage>(
    styles: CustomBuilderT<T>, 
    factory: ConstructorT<T>
  ): void
```

扩展图像组件构入口

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExtendableImage-@Builder  static _instantiateImpl<T extends ExtendableImage>(    styles: CustomBuilderT<T>,     factory: ConstructorT<T>  ): void--><!--Device-ExtendableImage-@Builder  static _instantiateImpl<T extends ExtendableImage>(    styles: CustomBuilderT<T>,     factory: ConstructorT<T>  ): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| styles | CustomBuilderT&lt;T&gt; | 是 |  |
| factory | [ConstructorT](arkts-na-constructort-t.md)&lt;T&gt; | 是 |  |

## setImageOptions

```TypeScript
public setImageOptions(
    src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent | undefined, 
    imageAIOptions?: ImageAIOptions
  ): this
```

设置图像组件选项

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExtendableImage-public setImageOptions(    src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent | undefined,     imageAIOptions?: ImageAIOptions  ): this--><!--Device-ExtendableImage-public setImageOptions(    src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent | undefined,     imageAIOptions?: ImageAIOptions  ): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | [PixelMap](../../apis-arkui/arkts-components/arkts-arkui-pixelmap-t.md) \| [ResourceStr](../../apis-arkui/arkts-apis/arkts-arkui-resourcestr-t.md) \| [DrawableDescriptor](../../apis-arkui/arkts-apis/arkts-arkui-arkui-drawabledescriptor-drawabledescriptor-c.md) \| [ImageContent](arkts-na-image-imagecontent-e.md) \| undefined | 是 |  |
| imageAIOptions | [ImageAIOptions](arkts-na-imagecommon-imageaioptions-i.md) | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## setImageOptions

```TypeScript
public setImageOptions(
    src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent | undefined, 
    imageAIOptions?: ImageAIOptions,
    reloadKey?: string
  ): this
```

设置图像组件选项

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExtendableImage-public setImageOptions(    src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent | undefined,     imageAIOptions?: ImageAIOptions,    reloadKey?: string  ): this--><!--Device-ExtendableImage-public setImageOptions(    src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent | undefined,     imageAIOptions?: ImageAIOptions,    reloadKey?: string  ): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | [PixelMap](../../apis-arkui/arkts-components/arkts-arkui-pixelmap-t.md) \| [ResourceStr](../../apis-arkui/arkts-apis/arkts-arkui-resourcestr-t.md) \| [DrawableDescriptor](../../apis-arkui/arkts-apis/arkts-arkui-arkui-drawabledescriptor-drawabledescriptor-c.md) \| [ImageContent](arkts-na-image-imagecontent-e.md) \| undefined | 是 |  |
| imageAIOptions | [ImageAIOptions](arkts-na-imagecommon-imageaioptions-i.md) | 否 |  |
| reloadKey | string | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## setImageOptions

```TypeScript
public setImageOptions(
    src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent | undefined, 
    reloadKey?: string
  ): this
```

设置图像组件选项

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExtendableImage-public setImageOptions(    src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent | undefined,     reloadKey?: string  ): this--><!--Device-ExtendableImage-public setImageOptions(    src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent | undefined,     reloadKey?: string  ): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | [PixelMap](../../apis-arkui/arkts-components/arkts-arkui-pixelmap-t.md) \| [ResourceStr](../../apis-arkui/arkts-apis/arkts-arkui-resourcestr-t.md) \| [DrawableDescriptor](../../apis-arkui/arkts-apis/arkts-arkui-arkui-drawabledescriptor-drawabledescriptor-c.md) \| [ImageContent](arkts-na-image-imagecontent-e.md) \| undefined | 是 |  |
| reloadKey | string | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

