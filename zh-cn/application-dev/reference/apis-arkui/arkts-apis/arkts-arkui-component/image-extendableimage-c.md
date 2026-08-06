# ExtendableImage

扩展图像组件定义

**继承/实现关系：** ExtendableImage implements [ImageAttribute](image-imageattribute-i.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export declare abstract class ExtendableImage implements ImageAttribute--><!--Device-unnamed-export declare abstract class ExtendableImage implements ImageAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## $_instantiate

```TypeScript
static $_instantiate<T extends ExtendableImage>(
    factory: ConstructorT<T>, 
    src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent | undefined,
    imageAIOptions?: ImageAIOptions
  ): T
```

扩展图像组件构造器

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExtendableImage-static $_instantiate<T extends ExtendableImage>(    factory: ConstructorT<T>,     src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent | undefined,    imageAIOptions?: ImageAIOptions  ): T--><!--Device-ExtendableImage-static $_instantiate<T extends ExtendableImage>(    factory: ConstructorT<T>,     src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent | undefined,    imageAIOptions?: ImageAIOptions  ): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| factory | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;T&gt; | 是 |  |
| src | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| ResourceStr \| DrawableDescriptor \| ImageContent \| undefined | 是 |  |
| imageAIOptions | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T |  |

## $_instantiate

```TypeScript
static $_instantiate<T extends ExtendableImage>(
    factory: ConstructorT<T>, 
    src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent | undefined,
    imageAIOptions?: ImageAIOptions,
    reloadKey?: string
  ): T
```

扩展图像组件构造器

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExtendableImage-static $_instantiate<T extends ExtendableImage>(    factory: ConstructorT<T>,     src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent | undefined,    imageAIOptions?: ImageAIOptions,    reloadKey?: string  ): T--><!--Device-ExtendableImage-static $_instantiate<T extends ExtendableImage>(    factory: ConstructorT<T>,     src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent | undefined,    imageAIOptions?: ImageAIOptions,    reloadKey?: string  ): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| factory | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;T&gt; | 是 |  |
| src | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| ResourceStr \| DrawableDescriptor \| ImageContent \| undefined | 是 |  |
| imageAIOptions | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 |  |
| reloadKey | string | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T |  |

## $_instantiate

```TypeScript
static $_instantiate<T extends ExtendableImage>(
    factory: ConstructorT<T>, 
    src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent | undefined,
    reloadKey?: string
  ): T
```

扩展图像组件

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExtendableImage-static $_instantiate<T extends ExtendableImage>(    factory: ConstructorT<T>,     src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent | undefined,    reloadKey?: string  ): T--><!--Device-ExtendableImage-static $_instantiate<T extends ExtendableImage>(    factory: ConstructorT<T>,     src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent | undefined,    reloadKey?: string  ): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| factory | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;T&gt; | 是 |  |
| src | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| ResourceStr \| DrawableDescriptor \| ImageContent \| undefined | 是 |  |
| reloadKey | string | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T |  |

## _instantiateImpl

```TypeScript
static _instantiateImpl<T extends ExtendableImage>(
    styles: CustomBuilderT<T>, 
    factory: ConstructorT<T>
  ): void
```

扩展图像组件构入口

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**装饰器类型：** @Builder

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExtendableImage-static _instantiateImpl<T extends ExtendableImage>(    styles: CustomBuilderT<T>,     factory: ConstructorT<T>  ): void--><!--Device-ExtendableImage-static _instantiateImpl<T extends ExtendableImage>(    styles: CustomBuilderT<T>,     factory: ConstructorT<T>  ): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| styles | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;T&gt; | 是 |  |
| factory | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;T&gt; | 是 |  |

## setImageOptions

```TypeScript
public setImageOptions(
    src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent | undefined, 
    imageAIOptions?: ImageAIOptions
  ): this
```

设置图像组件选项

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExtendableImage-public setImageOptions(    src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent | undefined,     imageAIOptions?: ImageAIOptions  ): this--><!--Device-ExtendableImage-public setImageOptions(    src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent | undefined,     imageAIOptions?: ImageAIOptions  ): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| ResourceStr \| DrawableDescriptor \| ImageContent \| undefined | 是 |  |
| imageAIOptions | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 |  |

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

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExtendableImage-public setImageOptions(    src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent | undefined,     imageAIOptions?: ImageAIOptions,    reloadKey?: string  ): this--><!--Device-ExtendableImage-public setImageOptions(    src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent | undefined,     imageAIOptions?: ImageAIOptions,    reloadKey?: string  ): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| ResourceStr \| DrawableDescriptor \| ImageContent \| undefined | 是 |  |
| imageAIOptions | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 |  |
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

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExtendableImage-public setImageOptions(    src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent | undefined,     reloadKey?: string  ): this--><!--Device-ExtendableImage-public setImageOptions(    src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent | undefined,     reloadKey?: string  ): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| ResourceStr \| DrawableDescriptor \| ImageContent \| undefined | 是 |  |
| reloadKey | string | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

