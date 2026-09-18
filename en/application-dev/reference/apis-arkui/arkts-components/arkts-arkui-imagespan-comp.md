# ImageSpan

As a child of the Text and ContainerSpan components, the **ImageSpan** component is used to display inline images.

## Child Components

Not supported

## ImageSpan

```TypeScript
ImageSpan(value: ResourceStr | PixelMap)
```

Defines the constructor of ImageSpan.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) &#124; [PixelMap](arkts-arkui-pixelmap-t.md) | Yes | Image source. Both local and network images are supported.<br>When using an image referenced using a relative path, for example, **ImageSpan("common/test.jpg")**, the **ImageSpan** component cannot be called across bundles or modules. Therefore, you are advised to use **&#36;r** to reference image resources that need to be used globally.<br>- The supported formats include PNG, JPG, BMP, SVG, GIF, and HEIF.<br>- Base64 strings are supported. The value format is data:image/[png&#124;jpeg&#124;bmp&#124;webp&#124;heif];base64, [base64 data], where *[base64 data]* is a Base64 string.<br>- Character string prefixed with file://data/ storage, which is used to read image resources in the file folder in the application installation directory. Ensure that the application has the read permission to the files in the specified path. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [ImageLoadResult](arkts-arkui-imageloadresult-i.md) | Describes the object returned after the callback is triggered when an image is successfully loaded or decoded. |

### Types

| Name | Description |
| --- | --- |
| [ImageCompleteCallback](arkts-arkui-imagecompletecallback-t.md) | Defines the callback triggered when the image is successfully loaded or decoded. |

## Examples

```TypeScript
### Example 1: Setting the Alignment Mode

This example demonstrates the alignment and scaling effects of the ImageSpan component using the [verticalAlign](#verticalalign) and [objectFit](#objectfit) attributes, available since API version 10.


```

```TypeScript
### Example 2: Setting the Background Style

This example demonstrates how to set the background style for text using the [textBackgroundStyle](ts-basic-components-span.md#textbackgroundstyle11) attribute, available since API version 11.


```

```TypeScript
### Example 3: Adding Events to an Image

This example demonstrates how to add load success and load error events to the ImageSpan component using [onComplete](#oncomplete12) and [onError](#onerror12), available since API version 12.
```

```TypeScript
### Example 4: Setting the Color Filter

This example demonstrates the effect of setting a color filter for the ImageSpan component using the [colorFilter](#colorfilter14) attribute, available since API version 14.


```

```TypeScript
### Example 5: Setting a Placeholder Image

This example demonstrates how to use the [alt](#alt12) attribute to display a placeholder image in the ImageSpan component while loading a network image, available since API version 12.

When using a network image, you need to apply for the ohos.permission.INTERNET permission. For details about how to apply for the permission, see [Declaring Permissions](../../../security/AccessToken/declare-permissions.md).


```

```TypeScript
### Example 6: Displaying an SVG Image Using the supportSvg2 Property

This example shows how to make the [SVG usability improvement capability](ts-image-svg2-capabilities.md#improved-svg-usability) of the [SVG tag parsing enhancement feature](ts-image-svg2-capabilities.md) take effect by configuring the [supportSvg2](#supportsvg222) attribute, available since API version 22.


```

```TypeScript
### Example 7: Setting Image Stretching

This example shows how to stretch the ImageSpan image in different directions using the slice option of the [resizable](#resizable) attribute.

Since API version 26.1.0, the resizable attribute is added.
```
