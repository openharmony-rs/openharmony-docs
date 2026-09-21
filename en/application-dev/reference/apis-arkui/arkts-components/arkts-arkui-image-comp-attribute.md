# Image properties/events

```TypeScript
declare class ImageAttribute extends CommonMethod<ImageAttribute>
```

The **Image** component is usually used to display images in applications. It supports data sources of the following types: [PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md), [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md), and [DrawableDescriptor](arkts-arkui-image-comp-drawabledescriptor-t.md). Supported image formats include PNG, JPG, JPEG, BMP, SVG, WEBP, GIF, HEIF, and TIFF. Note that the APNG and SVGA formats are not supported.

> **NOTE:** 

> - This component supports the TIFF image format since API version 23.
> 
> - When keyboard shortcuts are used to copy an **Image** component, the **Image** component must be in a focused state. For instructions on how to set focus, see [Setting Whether a Component Is Focusable](../../../ui/arkts-common-events-focus-event.md#setting-whether-a- component-is-focusable).By default, the **Image** component is not focusable. To enable it to gain focus, set both the [focusable](arkts-arkui-common-comp-commonmethod-c.md#focusable) and [focusOnTouch](arkts-arkui-common-comp-commonmethod-c.md#focusontouch) attributes to
> **true**.
> 
> - The **Image** component supports SVG image sources. For details about SVG tags, see [SVG Tags](arkts-arkui-common-comp.md#common).
> 
> - For animated images, animation playback is disabled by default and depends on the visibility of the **Image**component. When the component is visible, the animation is started through the callback. When the component is invisible, the animation is stopped. The visibility status of the **Image** component can be identified through the
> 
> [onVisibleAreaChange]
> [onVisibleAreaChange](arkts-arkui-common-comp-commonmethod-c.md#onvisibleareachange)
> event. If the value of **ratios** is greater than 0, the component is visible.
> 
> - For details about how to resolve white block issues during image loading, see [Solution to White Image Blocks](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-image-white-lump-solution).For details about how to address slow image loading, see [Optimizing Preset Image Loading](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-texture-&gt; compression-improve-performance#section91526132216). &gt;

**Inheritance/Implementation:** ImageAttribute extends CommonMethod<ImageAttribute>

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## alt

```TypeScript
alt(value: string | Resource | PixelMap)
```

Sets the placeholder image displayed during image loading.

The placeholder image supports configuration of [objectFit](#objectfit) for setting the fill effect, which is consistent with the fill effect of the image.

This attribute does not take effect when the parameter type of the component is [AnimatedDrawableDescriptor](../arkts-apis/arkts-arkui-arkui-drawabledescriptor-animateddrawabledescriptor-c.md).

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) &#124; [PixelMap](arkts-arkui-common-comp-pixelmap-t.md) | Yes | Placeholder image displayed during loading. Local images (in PNG, JPG, BMP, SVG, GIF, or HEIF format) and [PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md) objects are supported, but online images are not.<br>- Base64 strings are supported.<br>- Strings prefixed with the **file://** path are supported (application sandbox URI: **file://&lt;bundleName&gt;/&lt;sandboxPath&gt;**). For details about how to construct the application sandbox path URI, see [constructor](../../apis-core-file-kit/arkts-apis/arkts-corefile-fileuri-fileuri-c.md#constructor). The sandbox path must be converted to an application sandbox URI using the [fileUri.getUriFromPath(path)](../../apis-core-file-kit/arkts-apis/arkts-corefile-fileuri-geturifrompath-f.md) API before being passed in for display. In addition, ensure that the application has the read permission to the files in the specified path.<br>Default value: **null**<br>When the value is switched from a valid one (an image resource that can be parsed and loaded correctly) to an invalid one (an image path that cannot be parsed or loaded), the component retains the previously successfully loaded image content without clearing or resetting it.<br>**Since:** 12 |

<a id="alt-1"></a>

## alt

```TypeScript
alt(src: ResourceStr | PixelMap | ImageAlt)
```

Sets the placeholder image displayed during image loading and when image loading fails.

> **NOTE:** 
> 
> When a placeholder image is configured via [ImageAlt](arkts-arkui-image-comp-imagealt-i.md), **Image** takes effect based on the
> placeholder image sources configured for the loading and load-failure states. If no placeholder image is
> configured, it is not displayed by default.

The placeholder image supports configuration of [objectFit](#objectfit) for setting the fill effect, which is consistent with the fill effect of the image.

This attribute does not take effect when the parameter type of the component is [AnimatedDrawableDescriptor](../arkts-apis/arkts-arkui-arkui-drawabledescriptor-animateddrawabledescriptor-c.md).

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**Widget capability:** This API can be used in ArkTS widgets since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| src | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) &#124; [PixelMap](arkts-arkui-common-comp-pixelmap-t.md) &#124; [ImageAlt](arkts-arkui-image-comp-imagealt-i.md) | Yes | Placeholder image displayed during loading or in case of loading failure. Local images (in PNG, JPG, BMP, SVG, GIF, or HEIF format) and [PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md) objects are supported, but online images are not.<br>- Base64 strings are supported.<br>- Strings prefixed with the **file://** path are supported (application sandbox URI: **file://&lt;bundleName&gt;/&lt;sandboxPath&gt;**). For details about how to construct the application sandbox path URI, see [constructor](../../apis-core-file-kit/arkts-apis/arkts-corefile-fileuri-fileuri-c.md#constructor). The sandbox path must be converted to an application sandbox URI using the [fileUri.getUriFromPath(path)](../../apis-core-file-kit/arkts-apis/arkts-corefile-fileuri-geturifrompath-f.md) API before being passed in for display. In addition, ensure that the application has the read permission to the files in the specified path. |

## antialiased

```TypeScript
antialiased(isAntialiased: Optional<boolean>)
```

Sets whether to enable anti-aliasing for the edges of a pixel map image. If the attribute is not set, anti-aliasing is disabled by default. This attribute is not applicable to SVG images.

> **NOTE:** 
> 
> If the [backgroundColor](arkts-arkui-common-comp-commonmethod-c.md#backgroundcolor) attribute is set for an image,
> setting the **antialiased** attribute of the image to **true** does not affect the aliasing effect of the
> background color.
> 
> This attribute does not take effect when used together with [resizable](#resizable).

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isAntialiased | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Sets whether to enable anti-aliasing for the edges of a pixel map image.<br> **true**: Enable edge anti-aliasing.<br>**false**: Disable edge anti-aliasing.<br>When this parameter is set to **undefined**, edge anti-aliasing is disabled. |

## autoResize

```TypeScript
autoResize(value: boolean)
```

Specifies whether to resize the image source based on the size of the display area during image decoding. As downsampling images results in some loss of information, it may reduce the image quality, causing issues such as aliasing. To retain the original image quality, set **autoResize** to **false**, but this may increase the memory usage.

If the original image size does not match the display size, the image may be distorted or blurred. Recommended configuration for the optimal definition:

When the image is scaled down: .autoResize(false) + .interpolation(.Medium)

When the image is scaled up: .interpolation(.High)

This attribute does not take effect when the parameter type of the component is [AnimatedDrawableDescriptor](../arkts-apis/arkts-arkui-arkui-drawabledescriptor-animateddrawabledescriptor-c.md) or the image format is SVG.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to resize the image source based on the size of the display area during image decoding. This resizing can help reduce the memory usage. For example, if the original image size is 800 x 1200 and the display area size is 200 x 200, the image will be decoded to 200 x 300 at a downsampled resolution (the actual result may vary depending on the scaling and fill type configurations used in the calculation), greatly reducing the memory occupied by the image.<br>Default value: **false**<br>**true**: Enable resizing.<br> **false**: Disable resizing. |

## colorFilter

```TypeScript
colorFilter(value: ColorFilter | DrawingColorFilter)
```

Sets the color filter for the image.

When this attribute is set, [renderMode](#rendermode) is not effective.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ColorFilter](../arkts-apis/arkts-arkui-colorfilter-c.md) &#124; [DrawingColorFilter](arkts-arkui-image-comp-drawingcolorfilter-t.md) | Yes | 1. Color filter of the image. The input parameter is a 4 x 5 RGBA transformation matrix.<br>2. The ColorFilter type of **@ohos.graphics.drawing** can be used as an input parameter since API version 12.<br>**NOTE:** <br>This parameter is not available for SVG images in API version 11 and earlier versions.<br>The DrawingColorfilter type can be used in atomic services since API version 12. For SVG sources, the effect only applies when the **stroke** property is set (regardless of the value).<br>Since API version 21, when [supportSvg2](#supportsvg2) is set to **true**, **colorFilter** takes effect on the entire SVG image source.<br>**Since:** 12 |

<a id="colorfilter-1"></a>

## colorFilter

```TypeScript
colorFilter(value: ColorFilter | DrawingColorFilter | ResourceColor)
```

Sets the color filter for the image.

<p>&lt;strong&gt;NOTE&lt;/strong&gt;: <br>When this attribute is set, renderMode is not effective. <br>When value is ResourceColor type, it will be converted to ColorFilter with blend mode. </p>

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ColorFilter](../arkts-apis/arkts-arkui-colorfilter-c.md) &#124; [DrawingColorFilter](arkts-arkui-image-comp-drawingcolorfilter-t.md) &#124; [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Color filter of image. |

## contentTransition

```TypeScript
contentTransition(transition: ContentTransitionEffect)
```

Triggers transition animations when the image content changes.

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 21.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| transition | [ContentTransitionEffect](arkts-arkui-common-comp-contenttransitioneffect-c.md) | Yes | Type of transition animation.<br>The value **ContentTransitionEffect.OPACITY** indicates the fade-in/fade-out effect, and the value **ContentTransitionEffect.IDENTITY** indicates no animation effect.<br>Default value: **ContentTransitionEffect.IDENTITY**<br>When this parameter is set to **undefined** or **null**, the value defaults to **ContentTransitionEffect.IDENTITY**.<br>Note: This parameter does not take effect for dynamic image resources. |

## copyOption

```TypeScript
copyOption(value: CopyOptions)
```

Specifies whether the image can be copied. When **copyOption** is set to a value other than **CopyOptions.None**, the image can be copied through multiple interactions, such as long press, right-click, or Ctrl+C. SVG images cannot be copied.

This attribute does not take effect when the parameter type of the component is [AnimatedDrawableDescriptor](../arkts-apis/arkts-arkui-arkui-drawabledescriptor-animateddrawabledescriptor-c.md).

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [CopyOptions](../arkts-apis/arkts-arkui-copyoptions-e.md) | Yes | Specifies whether the image can be copied.<br>Default value: **CopyOptions.None** |

## draggable

```TypeScript
draggable(value: boolean)
```

Specifies whether the image is draggable.

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether the image is draggable. The value **true** means that the image is draggable, in which case the bound long press gesture will not take effect.<br>Default value:<br>API version 9 and earlier: **false**<br> Since API version 10: **true**<br> To bind custom gestures to the component, set **draggable** to **false**. With the value **false**, drag-related events are not triggered. |

## dynamicRangeMode

```TypeScript
dynamicRangeMode(value: DynamicRangeMode)
```

Sets the dynamic range of the image to be displayed. This attribute is not applicable to SVG images.

**Device behavior difference**: This API takes effect on mobile phones, PCs, 2-in-1 devices, and tablets, but not on other device types.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [DynamicRangeMode](arkts-arkui-image-comp-dynamicrangemode-e.md) | Yes | Dynamic range of the image.<br>Default value: **DynamicRangeMode.STANDARD** |

## enableAnalyzer

```TypeScript
enableAnalyzer(enable: boolean)
```

Sets whether to enable the AI image analyzer, which supports subject recognition, text recognition, and object lookup.

This attribute cannot be used together with the [overlay](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-overlay.md#overlay) attribute. If they are set at the same time, the [CustomBuilder](../../../reference/apis-arkui/arkui-ts/ts-types.md#custombuilder8) attribute in **overlay** has no effect. This feature also depends on device capabilities.

Images to be analyzed must be static, non-vector images. That is, SVG and GIF images cannot be analyzed. [Pixel maps](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md) in [RGBA_8888](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmapformat-e.md) format can be passed in for analysis. For details, see [Example 5: Enabling the AI Image Analyzer] (../../../reference/apis-arkui/arkui-ts/ts-basic-components-image.md#example-5-enabling-the-ai-image-analyzer).

The [alt](#alt) placeholder image does not support analysis. The [objectRepeat](#objectrepeat) attribute supports analysis only when it is set to **ImageRepeat.NoRepeat**. Analysis is not supported when the [obscured](arkts-arkui-common-comp-commonmethod-c.md#obscured) attribute is enabled.

Analysis is performed based on the complete original image. Even if the settings of the [clip](arkts-arkui-common-comp-commonmethod-c.md#clip), [margin](arkts-arkui-common-comp-commonmethod-c.md#margin), [borderRadius](arkts-arkui-common-comp-commonmethod-c.md#borderradius), [position](arkts-arkui-common-comp-commonmethod-c.md#position), and [objectFit](#objectfit) attributes cause incomplete image display, or if a mask layer is set via [renderMode](#rendermode), analysis will still be conducted on the complete original image. The [copyOption](#copyoption) attribute does not affect the AI image analyzer functionality.

This attribute does not take effect when the parameter type of the component is [AnimatedDrawableDescriptor](../arkts-apis/arkts-arkui-arkui-drawabledescriptor-animateddrawabledescriptor-c.md).

> **NOTE:** 
> 
> - The **ohos.permission.INTERNET** permission is required.
> 
> - This API can be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) since API version 12.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Whether the **Image** component supports AI analysis.<br>When this parameter is set to **true**, the **Image** component supports AI analysis. When this parameter is set to **false**, the **Image** component does not support AI analysis.<br>Default value: **false** |

## fillColor

```TypeScript
fillColor(value: ResourceColor)
```

Fill color to be superimposed on the image. This attribute applies only to SVG images. Once set, the fill color will replace the fill colors of all drawable elements within the SVG image. To set the fill color for a PNG image, use [colorFilter](#colorfilter).

This attribute does not take effect when the parameter type of the component is [AnimatedDrawableDescriptor](../arkts-apis/arkts-arkui-arkui-drawabledescriptor-animateddrawabledescriptor-c.md).

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | Yes | Fill color to be superimposed on the image.<br>**NOTE:** <br> By default, no fill color is applied. If an invalid value is passed, the system uses the default theme color: black in light mode and white in dark mode.<br>Since API version 21, when [supportSvg2](#supportsvg2) is set to **true**, **fillColor** depends on the **fill** attribute configuration in the SVG image source. If the **fill** attribute in the SVG image source is set to **'none'**, **fillColor** does not take effect. When **supportSvg2** is set to **false**, **fillColor** takes effect and replaces the fill colors of all drawable elements in the SVG image. |

<a id="fillcolor-1"></a>

## fillColor

```TypeScript
fillColor(color: ResourceColor | ColorContent)
```

Fill color to be superimposed on the image. This attribute applies only to SVG images. Once set, the fill color will replace the fill colors of all drawable elements within the SVG image. To set the fill color for a PNG image, use [colorFilter](#colorfilter). To reset the fill color, pass a value of the [ColorContent](arkts-arkui-image-comp-colorcontent-c.md) type.

This attribute does not take effect when the parameter type of the component is [AnimatedDrawableDescriptor](../arkts-apis/arkts-arkui-arkui-drawabledescriptor-animateddrawabledescriptor-c.md).

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| color | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) &#124; [ColorContent](arkts-arkui-image-comp-colorcontent-c.md) | Yes | Fill color to be superimposed on the image.<br>**NOTE:** <br> By default, no fill color is applied. If an invalid value is passed, the system uses the default theme color: black in light mode and white in dark mode.<br>Since API version 21, when [supportSvg2](#supportsvg2) is set to **true**, **fillColor** depends on the **fill** attribute configuration in the SVG image source. If the **fill** attribute in the SVG image source is set to **'none'**, **fillColor** does not take effect. |

<a id="fillcolor-2"></a>

## fillColor

```TypeScript
fillColor(color: ResourceColor | ColorContent | ColorMetrics)
```

Fill color to be superimposed on the image. This attribute applies only to SVG images. Once set, the fill color will replace the fill colors of all drawable elements within the SVG image. To set the fill color for a PNG image, use [colorFilter](#colorfilter). To reset the fill color, pass a value of the [ColorContent](arkts-arkui-image-comp-colorcontent-c.md) type. You can set P3 color gamut values by passing in the [ColorMetrics](../arkts-apis/arkts-arkui-graphics-colormetrics-c.md) type, which can achieve richer color performance on devices that support high color gamut.

This attribute does not take effect when the parameter type of the component is [AnimatedDrawableDescriptor](../arkts-apis/arkts-arkui-arkui-drawabledescriptor-animateddrawabledescriptor-c.md).

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| color | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) &#124; [ColorContent](arkts-arkui-image-comp-colorcontent-c.md) &#124; ColorMetrics | Yes | Fill color to be superimposed on the image.<br> **NOTE:** <br> By default, no fill color is applied. If an invalid value is passed, the system uses the default theme color: black in light mode and white in dark mode.<br>Since API version 21, when [supportSvg2](#supportsvg2) is set to **true**, **fillColor** depends on the **fill** attribute configuration in the SVG image source. If the **fill** attribute in the SVG image source is set to **'none'**, **fillColor** does not take effect. |

## fitOriginalSize

```TypeScript
fitOriginalSize(value: boolean)
```

Specifies whether the image display size follows the size of the image source.

This attribute does not take effect when the component has the **width** and **height** attributes set.

This attribute does not take effect when the parameter type of the component is [AnimatedDrawableDescriptor](../arkts-apis/arkts-arkui-arkui-drawabledescriptor-animateddrawabledescriptor-c.md).

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether the image display size follows the size of the image source.<br>Default value: **false**<br>**NOTE:** <br>**false** or not set: The image display size does not follow the size of the image source.<br> **true**: The image display size follows the size of the image source. |

## hdrBrightness

```TypeScript
hdrBrightness(brightness: number)
```

Sets the brightness of HDR images displayed by the component.

This attribute is not applicable to SVG images.

If this attribute and the [dynamicRangeMode](#dynamicrangemode) attribute are both set, [dynamicRangeMode](#dynamicrangemode) does not take effect.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| brightness | number | Yes | Brightness of HDR images displayed by the component. This API only takes effect for HDR image sources.<br>Default value: **1.0**<br>Value range: [0.0, 1.0]. Values less than 0 or greater than 1.0 are clamped to **1.0**. **0**: The image is displayed at SDR brightness.<br>**1.0**: The image is displayed at the highest allowed HDR brightness. |

## imageMatrix

```TypeScript
imageMatrix(matrix: ImageMatrix)
```

Sets the transformation matrix of the image. This API allows you to use the functions provided by the [ImageMatrix](#imagematrix) object, such as translate, rotate, and scale, to achieve the optimal display of grid thumbnails. This attribute is not applicable to SVG images.

This attribute does not take effect when [resizable](#resizable) and [objectRepeat](#objectrepeat) are set. This attribute only processes the image source and does not trigger any callback events of the **Image** component.

This attribute is strongly associated with [objectFit](#objectfit) and takes effect only when [objectFit](#objectfit) is set to **ImageFit.MATRIX**.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| matrix | [ImageMatrix](arkts-arkui-image-comp-imagematrix-t.md) | Yes | Transformation matrix of the image. |

## interpolation

```TypeScript
interpolation(value: ImageInterpolation)
```

Defines the image interpolation effect. This attribute mitigates aliasing during image scaling. This attribute is not applicable to SVG images.

This attribute does not take effect when the parameter type of the component is [AnimatedDrawableDescriptor](../arkts-apis/arkts-arkui-arkui-drawabledescriptor-animateddrawabledescriptor-c.md).

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ImageInterpolation](arkts-arkui-image-comp-imageinterpolation-e.md) | Yes | Interpolation effect of the image.<br>Default value: **ImageInterpolation.Low**<br>When set to **undefined**, the value is treated as **ImageInterpolation.None**. |

## matchTextDirection

```TypeScript
matchTextDirection(value: boolean)
```

Specifies whether the image follows the system language direction, displaying a mirrored effect in a right-to-left (RTL) language environments.

This attribute does not take effect when the parameter type of the component is [AnimatedDrawableDescriptor](../arkts-apis/arkts-arkui-arkui-drawabledescriptor-animateddrawabledescriptor-c.md).

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether the image follows the system language direction, displaying a mirrored effect in an RTL language environment.<br>Default value: **false**<br>The value **true** means that the image follows the system language direction, displaying a mirrored effect in an RTL language environment, and **false** means the opposite. |

## objectFit

```TypeScript
objectFit(value: ImageFit)
```

Sets how the image is resized to fit its container. If the attribute is not set, the default value is **ImageFit.Cover**, which scales the image up or down while maintaining its aspect ratio.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ImageFit](../arkts-apis/arkts-arkui-imagefit-e.md) | Yes | How the image is resized to fit its container. |

## objectRepeat

```TypeScript
objectRepeat(value: ImageRepeat)
```

Sets how the image is repeated. When set to repeat, the image is repeated from the center to edges. The last image will be clipped if it does not fit in the component. This attribute is not applicable to SVG images.

This attribute does not take effect when the parameter type of the component is [AnimatedDrawableDescriptor](../arkts-apis/arkts-arkui-arkui-drawabledescriptor-animateddrawabledescriptor-c.md).

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ImageRepeat](../arkts-apis/arkts-arkui-imagerepeat-e.md) | Yes | How the image is repeated.<br>Default value: **ImageRepeat.NoRepeat** |

## onComplete

```TypeScript
onComplete(
    callback: (event?: {
      /**
       * The width of the image source.
       *
       * @type { number }
       * @syscap SystemCapability.ArkUI.ArkUI.Full
       * @since 7
       */
      /**
       * The width of the image source.
       *
       * @type { number }
       * @syscap SystemCapability.ArkUI.ArkUI.Full
       * @since 9
       * @form
       */
      /**
       * The width of the image source.
       *
       * @type { number }
       * @syscap SystemCapability.ArkUI.ArkUI.Full
       * @crossplatform
       * @since 10
       * @form
       */
      /**
       * The width of the image source.
       *
       * @type { number }
       * @syscap SystemCapability.ArkUI.ArkUI.Full
       * @crossplatform
       * @atomicservice
       * @since 11
       * @form
       */
      width: number;
      /**
       * The height of the image source.
       *
       * @type { number }
       * @syscap SystemCapability.ArkUI.ArkUI.Full
       * @since 7
       */
      /**
       * The height of the image source.
       *
       * @type { number }
       * @syscap SystemCapability.ArkUI.ArkUI.Full
       * @since 9
       * @form
       */
      /**
       * The height of the image source.
       *
       * @type { number }
       * @syscap SystemCapability.ArkUI.ArkUI.Full
       * @crossplatform
       * @since 10
       * @form
       */
      /**
       * The height of the image source.
       *
       * @type { number }
       * @syscap SystemCapability.ArkUI.ArkUI.Full
       * @crossplatform
       * @atomicservice
       * @since 11
       * @form
       */
      height: number;
      /**
       * The width of the component source.
       *
       * @type { number }
       * @syscap SystemCapability.ArkUI.ArkUI.Full
       * @since 7
       */
      /**
       * The width of the component source.
       *
       * @type { number }
       * @syscap SystemCapability.ArkUI.ArkUI.Full
       * @since 9
       * @form
       */
      /**
       * The width of the component source.
       *
       * @type { number }
       * @syscap SystemCapability.ArkUI.ArkUI.Full
       * @crossplatform
       * @since 10
       * @form
       */
      /**
       * The width of the component source.
       *
       * @type { number }
       * @syscap SystemCapability.ArkUI.ArkUI.Full
       * @crossplatform
       * @atomicservice
       * @since 11
       * @form
       */
      componentWidth: number;
      /**
       * The height of the component source.
       *
       * @type { number }
       * @syscap SystemCapability.ArkUI.ArkUI.Full
       * @since 7
       */
      /**
       * The height of the component source.
       *
       * @type { number }
       * @syscap SystemCapability.ArkUI.ArkUI.Full
       * @since 9
       * @form
       */
      /**
       * The height of the component source.
       *
       * @type { number }
       * @syscap SystemCapability.ArkUI.ArkUI.Full
       * @crossplatform
       * @since 10
       * @form
       */
      /**
       * The height of the component source.
       *
       * @type { number }
       * @syscap SystemCapability.ArkUI.ArkUI.Full
       * @crossplatform
       * @atomicservice
       * @since 11
       * @form
       */
      componentHeight: number;
      /**
       * The value of the status of the image being loaded successfully.
       * If the returned status value is 0, the image data is successfully loaded.
       * If the returned status value is 1, the image is successfully decoded.
       *
       * @type { number }
       * @syscap SystemCapability.ArkUI.ArkUI.Full
       * @since 7
       */
      /**
       * The value of the status of the image being loaded successfully.
       * If the returned status value is 0, the image data is successfully loaded.
       * If the returned status value is 1, the image is successfully decoded.
       *
       * @type { number }
       * @syscap SystemCapability.ArkUI.ArkUI.Full
       * @since 9
       * @form
       */
      /**
       * The value of the status of the image being loaded successfully.
       * If the returned status value is 0, the image data is successfully loaded.
       * If the returned status value is 1, the image is successfully decoded.
       *
       * @type { number }
       * @syscap SystemCapability.ArkUI.ArkUI.Full
       * @crossplatform
       * @since 10
       * @form
       */
      /**
       * The value of the status of the image being loaded successfully.
       * If the returned status value is 0, the image data is successfully loaded.
       * If the returned status value is 1, the image is successfully decoded.
       *
       * @type { number }
       * @syscap SystemCapability.ArkUI.ArkUI.Full
       * @crossplatform
       * @atomicservice
       * @since 11
       * @form
       */
      loadingStatus: number;
      /**
       * The width of the picture that is actually drawn.
       *
       * @type { number }
       * @syscap SystemCapability.ArkUI.ArkUI.Full
       * @stagemodelonly
       * @crossplatform
       * @since 10
       * @form
       */
      /**
       * The width of the picture that is actually drawn.
       *
       * @type { number }
       * @syscap SystemCapability.ArkUI.ArkUI.Full
       * @stagemodelonly
       * @crossplatform
       * @atomicservice
       * @since 11
       * @form
       */
      contentWidth: number;
      /**
       * The height of the picture that is actually drawn.
       *
       * @type { number }
       * @syscap SystemCapability.ArkUI.ArkUI.Full
       * @stagemodelonly
       * @crossplatform
       * @since 10
       * @form
       */
      /**
       * The height of the picture that is actually drawn.
       *
       * @type { number }
       * @syscap SystemCapability.ArkUI.ArkUI.Full
       * @stagemodelonly
       * @crossplatform
       * @atomicservice
       * @since 11
       * @form
       */
      contentHeight: number;
      /**
       * The actual draw is offset from the x-axis of the component itself.
       *
       * @type { number }
       * @syscap SystemCapability.ArkUI.ArkUI.Full
       * @stagemodelonly
       * @crossplatform
       * @since 10
       * @form
       */
      /**
       * The actual draw is offset from the x-axis of the component itself.
       *
       * @type { number }
       * @syscap SystemCapability.ArkUI.ArkUI.Full
       * @stagemodelonly
       * @crossplatform
       * @atomicservice
       * @since 11
       * @form
       */
      contentOffsetX: number;
      /**
       * The actual draw is offset from the y-axis of the component itself.
       *
       * @type { number }
       * @syscap SystemCapability.ArkUI.ArkUI.Full
       * @stagemodelonly
       * @crossplatform
       * @since 10
       * @form
       */
      /**
       * The actual draw is offset from the y-axis of the component itself.
       *
       * @type { number }
       * @syscap SystemCapability.ArkUI.ArkUI.Full
       * @stagemodelonly
       * @crossplatform
       * @atomicservice
       * @since 11
       * @form
       */
      contentOffsetY: number;
    }) => void,
  )
```

Triggered when an image is successfully loaded or decoded. The size of the image source that is successfully loaded is returned, in pixels.

<p>&lt;strong&gt;NOTE&lt;/strong&gt;: <br>This event is not triggered if the parameter type of the component is AnimatedDrawableDescriptor. </p>

**Since:** 11

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | (event?: {       /**        * The width of the image source.        *        * @type { number }        * @syscap SystemCapability.ArkUI.ArkUI.Full        * @since 7        */       /**        * The width of the image source.        *        * @type { number }        * @syscap SystemCapability.ArkUI.ArkUI.Full        * @since 9        * @form        */       /**        * The width of the image source.        *        * @type { number }        * @syscap SystemCapability.ArkUI.ArkUI.Full        * @crossplatform        * @since 10        * @form        */       /**        * The width of the image source.        *        * @type { number }        * @syscap SystemCapability.ArkUI.ArkUI.Full        * @crossplatform        * @atomicservice        * @since 11        * @form        */       width: number;       /**        * The height of the image source.        *        * @type { number }        * @syscap SystemCapability.ArkUI.ArkUI.Full        * @since 7        */       /**        * The height of the image source.        *        * @type { number }        * @syscap SystemCapability.ArkUI.ArkUI.Full        * @since 9        * @form        */       /**        * The height of the image source.        *        * @type { number }        * @syscap SystemCapability.ArkUI.ArkUI.Full        * @crossplatform        * @since 10        * @form        */       /**        * The height of the image source.        *        * @type { number }        * @syscap SystemCapability.ArkUI.ArkUI.Full        * @crossplatform        * @atomicservice        * @since 11        * @form        */       height: number;       /**        * The width of the component source.        *        * @type { number }        * @syscap SystemCapability.ArkUI.ArkUI.Full        * @since 7        */       /**        * The width of the component source.        *        * @type { number }        * @syscap SystemCapability.ArkUI.ArkUI.Full        * @since 9        * @form        */       /**        * The width of the component source.        *        * @type { number }        * @syscap SystemCapability.ArkUI.ArkUI.Full        * @crossplatform        * @since 10        * @form        */       /**        * The width of the component source.        *        * @type { number }        * @syscap SystemCapability.ArkUI.ArkUI.Full        * @crossplatform        * @atomicservice        * @since 11        * @form        */       componentWidth: number;       /**        * The height of the component source.        *        * @type { number }        * @syscap SystemCapability.ArkUI.ArkUI.Full        * @since 7        */       /**        * The height of the component source.        *        * @type { number }        * @syscap SystemCapability.ArkUI.ArkUI.Full        * @since 9        * @form        */       /**        * The height of the component source.        *        * @type { number }        * @syscap SystemCapability.ArkUI.ArkUI.Full        * @crossplatform        * @since 10        * @form        */       /**        * The height of the component source.        *        * @type { number }        * @syscap SystemCapability.ArkUI.ArkUI.Full        * @crossplatform        * @atomicservice        * @since 11        * @form        */       componentHeight: number;       /**        * The value of the status of the image being loaded successfully.        * If the returned status value is 0, the image data is successfully loaded.        * If the returned status value is 1, the image is successfully decoded.        *        * @type { number }        * @syscap SystemCapability.ArkUI.ArkUI.Full        * @since 7        */       /**        * The value of the status of the image being loaded successfully.        * If the returned status value is 0, the image data is successfully loaded.        * If the returned status value is 1, the image is successfully decoded.        *        * @type { number }        * @syscap SystemCapability.ArkUI.ArkUI.Full        * @since 9        * @form        */       /**        * The value of the status of the image being loaded successfully.        * If the returned status value is 0, the image data is successfully loaded.        * If the returned status value is 1, the image is successfully decoded.        *        * @type { number }        * @syscap SystemCapability.ArkUI.ArkUI.Full        * @crossplatform        * @since 10        * @form        */       /**        * The value of the status of the image being loaded successfully.        * If the returned status value is 0, the image data is successfully loaded.        * If the returned status value is 1, the image is successfully decoded.        *        * @type { number }        * @syscap SystemCapability.ArkUI.ArkUI.Full        * @crossplatform        * @atomicservice        * @since 11        * @form        */       loadingStatus: number;       /**        * The width of the picture that is actually drawn.        *        * @type { number }        * @syscap SystemCapability.ArkUI.ArkUI.Full        * @stagemodelonly        * @crossplatform        * @since 10        * @form        */       /**        * The width of the picture that is actually drawn.        *        * @type { number }        * @syscap SystemCapability.ArkUI.ArkUI.Full        * @stagemodelonly        * @crossplatform        * @atomicservice        * @since 11        * @form        */       contentWidth: number;       /**        * The height of the picture that is actually drawn.        *        * @type { number }        * @syscap SystemCapability.ArkUI.ArkUI.Full        * @stagemodelonly        * @crossplatform        * @since 10        * @form        */       /**        * The height of the picture that is actually drawn.        *        * @type { number }        * @syscap SystemCapability.ArkUI.ArkUI.Full        * @stagemodelonly        * @crossplatform        * @atomicservice        * @since 11        * @form        */       contentHeight: number;       /**        * The actual draw is offset from the x-axis of the component itself.        *        * @type { number }        * @syscap SystemCapability.ArkUI.ArkUI.Full        * @stagemodelonly        * @crossplatform        * @since 10        * @form        */       /**        * The actual draw is offset from the x-axis of the component itself.        *        * @type { number }        * @syscap SystemCapability.ArkUI.ArkUI.Full        * @stagemodelonly        * @crossplatform        * @atomicservice        * @since 11        * @form        */       contentOffsetX: number;       /**        * The actual draw is offset from the y-axis of the component itself.        *        * @type { number }        * @syscap SystemCapability.ArkUI.ArkUI.Full        * @stagemodelonly        * @crossplatform        * @since 10        * @form        */       /**        * The actual draw is offset from the y-axis of the component itself.        *        * @type { number }        * @syscap SystemCapability.ArkUI.ArkUI.Full        * @stagemodelonly        * @crossplatform        * @atomicservice        * @since 11        * @form        */       contentOffsetY: number;     }) =&gt; void | Yes |  |

## onError

```TypeScript
onError(callback: ImageErrorCallback)
```

Triggered when an error occurs during image loading.

This event is not triggered if the parameter type of the component is [AnimatedDrawableDescriptor](../arkts-apis/arkts-arkui-arkui-drawabledescriptor-animateddrawabledescriptor-c.md).

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [ImageErrorCallback](arkts-arkui-image-comp-imageerrorcallback-t.md) | Yes | Callback triggered when an error occurs during image loading. **NOTE:** &lt;You are advised to use this callback to quickly identify the cause of image loading failures. For details, see the [ImageError](arkts-arkui-image-comp-imageerror-i.md) error codes.<br>**Since:** 11 |

## onFinish

```TypeScript
onFinish(event: () => void)
```

Triggered when the animation playback in the loaded SVG image is complete. If the animation is an infinite loop, this callback is not triggered.

Only images in SVG format are supported. This event is not triggered if the parameter type of the component is [AnimatedDrawableDescriptor](../arkts-apis/arkts-arkui-arkui-drawabledescriptor-animateddrawabledescriptor-c.md).

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | () =&gt; void | Yes | Triggered when the animation playback in the loaded SVG image is complete. If the animation is an infinite loop, this callback is not triggered. |

## orientation

```TypeScript
orientation(orientation: ImageRotateOrientation) : ImageAttribute
```

Sets the display orientation of the image content.

This attribute does not apply to placeholder images specified by [alt](#alt).

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| orientation | [ImageRotateOrientation](arkts-arkui-image-comp-imagerotateorientation-e.md) | Yes | Display orientation of the image content.<br>Only static pixel map display is supported.<br>For images containing rotation or flip information, use **ImageRotateOrientation.AUTO**.<br>Default value: **ImageRotateOrientation.UP**<br>When this parameter is set to **undefined** or **null**, the value is **ImageRotateOrientation.AUTO**. |

## privacySensitive

```TypeScript
privacySensitive(supported: boolean)
```

Sets whether to secure sensitive information on widgets.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| supported | boolean | Yes | Whether to secure sensitive information on widgets.<br>**false** (default): Do not secure sensitive information on widgets.<br>**true**: Secure sensitive information on widgets, obscuring the image with a semi-transparent background style in privacy mode.<br>**NOTE:** <br>If this parameter is set to **null**, the image is not obscured.<br>Privacy mode requires support from the widget framework. |

## renderMode

```TypeScript
renderMode(value: ImageRenderMode)
```

Sets the rendering mode of the image. This attribute is not applicable to SVG images.

This attribute does not take effect when [ColorFilter](#colorfilter) is set.

This attribute does not take effect when the parameter type of the component is [AnimatedDrawableDescriptor](../arkts-apis/arkts-arkui-arkui-drawabledescriptor-animateddrawabledescriptor-c.md).

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ImageRenderMode](arkts-arkui-image-comp-imagerendermode-e.md) | Yes | Rendering mode of the image, which can be **Original** or **Template** (monochrome).<br>Default value: **ImageRenderMode.Original** |

## resizable

```TypeScript
resizable(value: ResizableOptions)
```

Sets the resizable image options. Resizing is effective for drag previews and placeholder images.

When a valid [ResizableOptions](arkts-arkui-image-comp-resizableoptions-i.md) is set, the **objectRepeat**, **antialiased**, and **orientation** attributes do not take effect.

When the sum of the values of **top** and **bottom** is greater than the source image height, or the sum of the values of **left** and **right** is greater than the source image width, the [ResizableOptions](arkts-arkui-image-comp-resizableoptions-i.md) attribute does not take effect.

This attribute does not take effect when the parameter type of the component is [AnimatedDrawableDescriptor](../arkts-apis/arkts-arkui-arkui-drawabledescriptor-animateddrawabledescriptor-c.md) or the image format is SVG.

> **NOTE:** 
> 
> This API can be called in [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) since API version 20.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResizableOptions](arkts-arkui-image-comp-resizableoptions-i.md) | Yes | Resizable image options. |

## sourceSize

```TypeScript
sourceSize(value: ImageSourceSize)
```

Sets the decoding size of the image. This attribute works only when the target size is smaller than the source size. This attribute is not applicable to SVG images or **PixelMap** objects.

This attribute does not take effect when the parameter type of the component is [AnimatedDrawableDescriptor](../arkts-apis/arkts-arkui-arkui-drawabledescriptor-animateddrawabledescriptor-c.md).

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ImageSourceSize](arkts-arkui-image-comp-imagesourcesize-i.md) | Yes | Decoding size of the image. This parameter can be used to reduce the image resolution when the image display size needs to be smaller than the component size. When this parameter is used with **ImageFit.None** of the [objectFit](#objectfit) API, a small image can be displayed in the component.<br>**Since:** 18 |

## supportSvg2

```TypeScript
supportSvg2(enable: boolean) : ImageAttribute
```

Sets whether to enable [enhanced SVG tag parsing](../../../reference/apis-arkui/arkui-ts/ts-image-svg2-capabilities.md). When this feature is enabled, SVG image rendering behavior changes accordingly.

After the **Image** component is created, the value of this attribute cannot be dynamically changed.

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 21.

**Widget capability:** This API can be used in ArkTS widgets since API version 21.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Determines whether to enable the enhanced SVG tag parsing feature.<br>Default value: **false**<br>**true**: Enable enhanced SVG parsing.<br>**false**: Use original SVG parsing. |

## syncLoad

```TypeScript
syncLoad(value: boolean)
```

Specifies whether to load the image synchronously. When loading a small local image, you are advised to set **syncLoad** to **true** so that the image loading can be quickly completed on the main thread.

This attribute does not take effect when the parameter type of the component is [AnimatedDrawableDescriptor](../arkts-apis/arkts-arkui-arkui-drawabledescriptor-animateddrawabledescriptor-c.md).

If image flickering occurs during loading, set **syncLoad** to **true**. For details, see [Optimizing Concurrent Tasks] (https://developer.huawei.com/consumer/en/doc/best-practices/bpta-click-to-click-response- optimization#section715115119192).

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to load the image synchronously. By default, the image is loaded asynchronously. During synchronous loading, the UI thread is blocked and the placeholder image is not displayed.<br>Default value: **false**<br>**true**: Load the image synchronously.<br>**false**: Load the image asynchronously.<br>If the main thread is blocked for more than 6s, AppFreeze will occur. For details, see [Application Freeze Detection](../../../dfx/appfreeze-guidelines.md). |
