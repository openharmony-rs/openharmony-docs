# Image

The **Image** component is usually used to display images in applications. It supports data sources of the following types: [PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md), [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md), and [DrawableDescriptor](arkts-arkui-drawabledescriptor-t.md). Supported image formats include PNG, JPG, JPEG, BMP, SVG, WEBP, GIF, HEIF, and TIFF. Note that the APNG and SVGA formats are not supported.

> **NOTE**

> - This component supports the TIFF image format since API version 23. > > - When keyboard shortcuts are used to copy an **Image** component, the **Image** component must be in a focused > state. For instructions on how to set focus, see > [Setting Whether a Component Is Focusable] > (../../../ui/arkts-common-events-focus-event.md#setting-whether-a-component-is-focusable). > By default, the **Image** component is not focusable. To enable it to gain focus, set both the > focusable and [focusOnTouch](arkts-arkui-commonmethod-c.md#focusontouch) attributes to > **true**. > > - The **Image** component supports SVG image sources. For details about SVG tags, see SVG Tags. > > - For animated images, animation playback is disabled by default and depends on the visibility of the **Image** > component. When the component is visible, the animation is started through the callback. When the component is > invisible, the animation is stopped. The visibility status of the **Image** component can be identified through the > > [onVisibleAreaChange] > [onVisibleAreaChange](arkts-arkui-commonmethod-c.md#onvisibleareachange) > event. If the value of **ratios** is greater than 0, the component is visible. > > - For details about how to resolve white block issues during image loading, see > [Solution to White Image Blocks] > (https://developer.huawei.com/consumer/en/doc/best-practices/bpta-image-white-lump-solution). > For details about how to address slow image loading, see > [Optimizing Preset Image Loading] > (https://developer.huawei.com/consumer/en/doc/best-practices/bpta-texture-compression-improve- > performance#section91526132216). >

Required Permissions

The **ohos.permission.INTERNET** permission is required for using online images. For details about how to apply for a permission, see [Declaring Permissions](../../../security/AccessToken/declare-permissions.md).

Child Components

Not supported

## Image

```TypeScript
Image(src: PixelMap | ResourceStr | DrawableDescriptor)
```

Obtains an image from the specified source for subsequent rendering and display.

If the **Image** component fails to obtain the image or the obtained image size is 0, the **Image** component is automatically resized to 0 and does not follow the layout constraints of its parent component.

By default, the **Image** component crops images to keep their center. For example, if the component has the same width and height, it crops any image whose width and height are different, so as to keep its center.

If the **Image** component does not have its width and height set, its size adapts to that of its parent component once the image is successfully loaded.

> **NOTE:** 
> 
> - Passing a URL directly to an **Image** component may lead to potential performance issues, such as: (1) Large images cannot be downloaded in advance during loading, resulting in a long display time of white blocks; (2)Small images set to load synchronously may block the UI thread in a weak network environment, causing screen freezes; (3) In a rapidly scrolling waterfall flow, images that are about to be displayed cannot be downloaded in advance, resulting in many white blocks during scrolling. Performance issues may manifest differently in different scenarios. To minimize these issues, separate the network download part from the display of the
> **Image** component, and download in advance or asynchronously. For details about how to resolve white block
> issues during image loading, see
> [Solution to White Image Blocks]
> (https://developer.huawei.com/consumer/en/doc/best-practices/bpta-image-white-lump-solution).
> For details about how to address slow image loading, see
> [Optimizing Preset Image Loading]
> (https://developer.huawei.com/consumer/en/doc/best-practices/bpta-texture-compression-improve-performance).
> 
> 
> - When **src** is switched from a valid value (an image resource that can be parsed and loaded correctly) to an invalid value (an image path that cannot be parsed or loaded), the component retains the previously successfully loaded image content without clearing or resetting it.
> 
> - If the input parameter is of the [PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md) type, the **Image**component can detect data changes only when the **PixelMap** object is updated to point to a new instance. If modifications are made to the content of the **PixelMap** object, such as pixel values, but the reference to the object remains the same, the **Image** component will not recognize these modifications as a data change.
> 
> - If the input parameter of the **Image** component is a Base64 string, the standard format of the Base64 string is **data:image/subtype;base64,Base64EncodedData**. In this format, **subtype** indicates the type declaration,
> **Base64EncodedData** indicates the Base64-encoded data, and other values are fixed strings. For example, the
> input parameter of a PNG image is **data:image/png;base64,iVBORw0KGgo...**.
> 
> 
> 
> 1. **image/subType** declares the data type. The **Image** component does not enforce that the declared type exactly matches the actual image format decoded from Base64. In some scenarios, the image may still display correctly even if the declared type does not match the actual format. To prevent future behavior changes or unknown issues, it is recommended that the declared type always match the actual image format.
> 
> 
> 
> 2. The **Image** component does not support the wildcard syntax: **data:image/*;base64,Base64EncodedData**.The **subType** must explicitly declare the specific image type.
> 
> 
> 
> 3. The **Image** component does not support loading SVG images in Base64 string format.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| src | [PixelMap](arkts-arkui-pixelmap-t.md) &#124; [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) &#124; [DrawableDescriptor](arkts-arkui-drawabledescriptor-t.md) | Yes | Data source of the image. Local and online sources are supported. For details about how to reference an image, see [Loading Image Resources](../../../ui/arkts-graphics-display.md#loading-image-resources).<br>1. **PixelMap**: a pixel map storing graphical information, commonly used for image editing scenarios.<br>2. **ResourceStr**: a string or a Resource object.<br>The string type can be used to load local images and, more frequently, online images. When [using a local image referenced using a relative path](../../../reference/apis-arkui/arkui-ts/ts-basic-compon ents-image.md#example-25-displaying-an-image-using-a-relative-path), the **Image** component cannot be called across bundles or modules. If an image needs to be used globally, you are advised to use the Resource format.<br>Since DevEco Studio 6.0.0 Beta2, resources in non-**resource** directories are not packaged by default for new projects or modules. To enable packaging, go to **buildOption**   > **resOptions** > **copyCodeResource** to set **enable** to **true** in the module's **build-profile.json5** file. For details, see [resOptions](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-hvigor-build- profile#table1476161719356). <br>- Base64 strings are supported.<br>- When providing an HTTPS network image URL, refer to [Example 2: Downloading and Displaying Static Online Images](../../../reference/apis-arkui/arkui-ts/ts-basic- components-image.md#example-2-downloading-and-displaying-static-online-images) for implementation guidance.<br>- Strings prefixed with the **file://** path are supported (application sandbox URI: **file://&lt;bundleName&gt;/&lt;sandboxPath&gt;**). For details about how to construct the application sandbox path URI, see [constructor](../../apis-core-file-kit/arkts-apis/arkts-corefile-fileuri-fileuri-c.md#constructor). The sandbox path must be converted to an application sandbox URI using the [fileUri.getUriFromPath(path)](../../apis-core-file-kit/arkts-apis/arkts-corefile-fileuri-geturifrompath-f.md) API before being passed in for display. In addition, ensure that the application has the read permission to the files in the specified path.<br>The Resource format allows for access across bundles and modules. It is recommended for accessing local images. For details, see [Cross-HAP/HSP Resources](../../../quick-start/resource-categories-and-access.md#cross-haphsp-resources).<br> 3. **DrawableDescriptor**: an object created when the passed resource ID or name belongs to a common image. The [AnimatedDrawableDescriptor](../arkts-apis/arkts-arkui-arkui-drawabledescriptor-animateddrawabledescriptor-c.md) type can be passed to play animations from a **PixelMap** array.<br>**NOTE:** <br>- ArkTS widgets support GIF animations, but the animations only play once on display.<br>- ArkTS widgets do not support the strings with the **http://** or **file://** prefix. |

## Image

```TypeScript
Image(src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent)
```

Obtains an image. The [ImageContent](arkts-arkui-imagecontent-e.md) type allows you to specify the image content.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| src | [PixelMap](arkts-arkui-pixelmap-t.md) &#124; [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) &#124; [DrawableDescriptor](arkts-arkui-drawabledescriptor-t.md) &#124; [ImageContent](arkts-arkui-imagecontent-e.md) | Yes | Data source of the image. Local and online sources are supported. For details about how to reference an image, see [Loading Image Resources](../../../ui/arkts-graphics-display.md#loading-image-resources).<br>For details about how to use **PixelMap**, **ResourceStr**, and **DrawableDescriptor**, see the **src** parameter description of [Image](../../../reference/apis-arkui/arkui-ts/ts-basic-components-image.md#image-1).<br> [ImageContent](arkts-arkui-imagecontent-e.md): image content.<br>**NOTE:** <br>- ArkTS widgets support GIF animations, but the animations only play once on display.<br>- ArkTS widgets do not support the strings with the **http://** or **file://** prefix. |

## Image

```TypeScript
Image(src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent, reloadKey?: string)
```

Set src to obtain images

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| src | [PixelMap](arkts-arkui-pixelmap-t.md) &#124; [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) &#124; [DrawableDescriptor](arkts-arkui-drawabledescriptor-t.md) &#124; [ImageContent](arkts-arkui-imagecontent-e.md) | Yes |  |
| reloadKey | string | No |  |

## Image

```TypeScript
Image(src: PixelMap | ResourceStr | DrawableDescriptor, imageAIOptions: ImageAIOptions)
```

Obtains an image. The [imageAIOptions](../arkts-apis/arkts-arkui-imageaioptions-i.md) parameter allows you to set AI image analysis options.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| src | [PixelMap](arkts-arkui-pixelmap-t.md) &#124; [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) &#124; [DrawableDescriptor](arkts-arkui-drawabledescriptor-t.md) | Yes | Data source of the image. Local and online sources are supported. For details about how to reference an image, see [Loading Image Resources](../../../ui/arkts-graphics-display.md#loading-image-resources).<br>For details about how to use **PixelMap**, **ResourceStr**, and **DrawableDescriptor**, see the **src** parameter description of [Image](../../../reference/apis-arkui/arkui-ts/ts-basic-components-image.md#image-1).<br>**NOTE:** <br>- ArkTS widgets support GIF animations, but the animations only play once on display.<br>- ArkTS widgets do not support the strings with the **http://** or **file://** prefix. |
| imageAIOptions | [ImageAIOptions](../arkts-apis/arkts-arkui-imageaioptions-i.md) | Yes | AI image analysis options. You can configure the analysis type or bind an analyzer controller through this parameter. |

## Image

```TypeScript
Image(src: PixelMap | ResourceStr | DrawableDescriptor,
      imageAIOptions?: ImageAIOptions, reloadKey?: string)
```

Set src and ai options to obtain images

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| src | [PixelMap](arkts-arkui-pixelmap-t.md) &#124; [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) &#124; [DrawableDescriptor](arkts-arkui-drawabledescriptor-t.md) | Yes |  |
| imageAIOptions | [ImageAIOptions](../arkts-apis/arkts-arkui-imageaioptions-i.md) | No |  |
| reloadKey | string | No |  |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [ImageAlt](arkts-arkui-imagealt-i.md) | Sets the placeholder image. |
| [ImageError](arkts-arkui-imageerror-i.md) | Describes the object returned by the image loading error callback. |
| [ImageSourceSize](arkts-arkui-imagesourcesize-i.md) | Defines source size of image. |
| [ResizableOptions](arkts-arkui-resizableoptions-i.md) | Defines the resizable image options. |

### Types

| Name | Description |
| --- | --- |
| [BusinessError](arkts-arkui-businesserror-t.md) | Represents the error information returned when an error occurs during image loading. |
| [DrawableDescriptor](arkts-arkui-drawabledescriptor-t.md) | Represents a parameter object for the **Image** component. |
| [DrawingColorFilter](arkts-arkui-drawingcolorfilter-t.md) | Represents a color filter object. |
| [DrawingLattice](arkts-arkui-drawinglattice-t.md) | Represents a matrix grid object that divides an image into a rectangular grid. |
| [ImageErrorCallback](arkts-arkui-imageerrorcallback-t.md) | Triggered when an error occurs during image loading. |
| [ImageMatrix](arkts-arkui-imagematrix-t.md) | Represents the current matrix object. |
| [RequestDownloadInfo](arkts-arkui-requestdownloadinfo-t.md) | Describes the download information when an online image fails to load or encounters an exception. This object contains resource information, network information, and performance statistics of the download task, which can be used to locate the cause of the loading exception. |
| [ResolutionQuality](arkts-arkui-resolutionquality-t-sys.md) | Enumerates all the levels available for the image resolution quality. |

### Enums

| Name | Description |
| --- | --- |
| [DynamicRangeMode](arkts-arkui-dynamicrangemode-e.md) | Describes the dynamic range of the image to be displayed. |
| [ImageContent](arkts-arkui-imagecontent-e.md) | Defines the image content. |
| [ImageInterpolation](arkts-arkui-imageinterpolation-e.md) | Interpolation effect of the image. |
| [ImageRenderMode](arkts-arkui-imagerendermode-e.md) | Interpolation effect of the image. |
| [ImageRotateOrientation](arkts-arkui-imagerotateorientation-e.md) | Describes the desired display orientation for image content. |

## Examples

```TypeScript
### Example 1: Loading Images of Basic Types

This example demonstrates how to load images of basic types, such as PNG, GIF, SVG, and JPG, by passing in [Resource](ts-types.md#resource) resources.


```

```TypeScript
### Example 2: Downloading and Displaying Static Online Images

The default timeout is 5 minutes for loading online images. When using an online image, you are advised to use alt to configure a placeholder image displayed during loading. You can use [HTTP](../../../network/http-request.md) to send a network request, and then decode the returned data into a PixelMap object for the Image component. Note that a GIF image loaded into a PixelMap object will be displayed as a static image. For details about image development, see the [Image Kit](../../../media/image/image-overview.md) overview.

The ohos.permission.INTERNET permission is required for using online images. For details about how to apply for a permission, see [Declaring Permissions](../../../security/AccessToken/declare-permissions.md).


```

```TypeScript
### Example 3: Downloading and Displaying Online GIF Images

This example shows how to use the cacheDownload.download API to download online GIF images.

The ohos.permission.INTERNET permission is required for using online images. For details about how to apply for a permission, see [Declaring Permissions](../../../security/AccessToken/declare-permissions.md).
```

```TypeScript
### Example 4: Adding Events to an Image

This example demonstrates how to add the [onClick](ts-universal-events-click.md#onclick) and [onFinish](#onfinish) events to an image.


```

```TypeScript
### Example 5: Enabling the AI Image Analyzer

This example shows how to enable the AI image analyzer using the [enableAnalyzer](#enableanalyzer11) API.


```

```TypeScript
### Example 6: Stretching an Image Using slice

This example demonstrates how to stretch an image in different directions using the slice option of the [resizable](#resizable11) attribute.


```

```TypeScript
### Example 7: Stretching an Image Using lattice

This example demonstrates how to stretch an image using the lattice option of the [resizable](#resizable11) attribute with a rectangular lattice object.


```

```TypeScript
### Example 8: Playing a PixelMap Array Animation

This example demonstrates how to play an animation using a PixelMap array through an AnimatedDrawableDescriptor object.


```

```TypeScript
### Example 9: Setting a Color Filter for an Image

This example shows how to set a color filter for an image using the [colorFilter](#colorfilter9) attribute.


```

```TypeScript
### Example 10: Setting the Fill Effect for an Image

This example shows how to use the [objectFit](#objectfit) attribute to specify how an image is resized to fit its container.


```

```TypeScript
### Example 11: Switching Between Different Types of Images

This example demonstrates the effect of displaying images with [ResourceStr](ts-types.md#resourcestr) and [ImageContent](arkts-arkui-imagecontent-e.md) as types of data sources.


```

```TypeScript
### Example 12: Securing Sensitive Information

This example shows how to secure sensitive information on widgets using the [privacySensitive](#privacysensitive12) attribute. The display requires widget framework support.


```

```TypeScript
### Example 13: Setting the Scan Effect for an Image

This example shows how to enable the scan effect for an image using [linearGradient](./ts-basic-components-datapanel.md#lineargradient10) and [animateTo()](../arkts-apis-uicontext-uicontext.md#animateto).


```

```TypeScript
### Example 14: Adding Transform Effects to an Image

This example demonstrates how to apply rotation and translation effects to an image using the [imageMatrix](#imagematrix15) and [objectFit](#objectfit) attributes.

The imageMatrix attribute is added since API version 15.


```

```TypeScript
### Example 15: Setting the Image Decoding Size Using sourceSize

This example uses the [sourceSize](#sourcesize) API to customize the image decoding size.


```

```TypeScript
### Example 16: Setting the Image Rendering Mode Using renderMode

This example uses the [renderMode](#rendermode) API to set the image rendering mode to monochrome.


```

```TypeScript
### Example 17: Setting the Image Repeat Pattern Using objectRepeat

This example uses the [objectRepeat](arkts-arkui-image-comp-attribute.md#objectrepeat) API to repeat the image along the vertical axis.


```

```TypeScript
### Example 18: Setting the Fill Color for an SVG Image

This example shows how to set different fill colors for an SVG image using the [fillColor](#fillcolor15) attribute.


```

```TypeScript
### Example 19: Adjusting HDR Image Brightness

This example demonstrates how to adjust the HDR image brightness using the [hdrBrightness](#hdrbrightness19) attribute, changing the value from 0 to 1.

The hdrBrightness attribute is added since API version 19.
```

```TypeScript
### Example 20: Setting Whether the Image Follows the System Language Direction

This example shows how to use the [matchTextDirection](arkts-arkui-image-comp-attribute.md#matchtextdirection) API to set whether the image should be mirrored when the device system language is set to Uyghur.


```

```TypeScript
### Example 21: Setting Image Display Orientation

This example shows how to configure different image display orientations using the [orientation](#orientation14) attribute.


```

```TypeScript
### Example 22: Using EXIF Metadata for Image Display Orientation

This example demonstrates how to use the [getImageProperty](../../apis-image-kit/arkts-apis-image-ImageSource.md#getimageproperty) API to obtain the EXIF metadata of an image, and then set the image display orientation through the [orientation](#orientation14) attribute based on the obtained EXIF metadata.


```

```TypeScript
### Example 23: Dynamically Switching an SVG Image Between Fill Colors

This example demonstrates how to dynamically switch an SVG Image between fill colors across different color spaces using ColorMetrics.


```

```TypeScript
### Example 24: Displaying an Image Using an Application Sandbox Path

This example demonstrates how to display an image using the application sandbox path, where a preloaded image named cloud.png is placed in the haps/entry/files directory of the current application.


```

```TypeScript
### Example 25: Displaying an Image Using a Relative Path

This example demonstrates how to display an image using a relative path. First, create a common directory at the same level as the project's pages directory. Then, place a preloaded image named cloud1.png in the common directory and display it using the relative path.


```

```TypeScript
### Example 26: Displaying an SVG Image Using supportSvg2

In this example, the [supportSvg2](#supportsvg221) attribute is set to enable the enhanced SVG tag parsing feature.

The supportSvg2 attribute is added since API version 21.


```

```TypeScript
### Example 27: Implementing Fade-in/Fade-out Transition Effects for Images Using ContentTransition

This example demonstrates how to use the [contentTransition](#contenttransition21) attribute to implement the fade-in/fade-out effect for smooth image transitions when the image source is switched on a click. This attribute is supported since API version 21.


```

```TypeScript
### Example 28: Using the alt Attribute to Set the Placeholder Images Displayed During Image Loading and When Image Loading Fails

This example demonstrates how to display specified images during image loading and when image loading fails by setting the [alt](#alt22) attribute.


```

```TypeScript
### Example 29 Listening to Online Image Loading Exceptions Using onError

This example demonstrates how to obtain detailed download information ([ImageError](arkts-arkui-imageerror-i.md)) when an online image fails to load via the [onError](#onerror9) callback. When image loading fails, you can obtain detailed online image download information through the downloadInfo attribute in ImageError, including download resource information, network request information, and performance statistics. This helps quickly identify the cause of network exceptions or resource errors.

The downloadInfo attribute is added to ImageError since API version 23.
```

```TypeScript
### Example 30 Setting Anti-aliasing for Pixel Map Image Edges

This example demonstrates how to enable the anti-aliasing feature for pixel map image edges by setting the [antialiased](arkts-arkui-image-comp-attribute.md#antialiased) API.

The [antialiased](arkts-arkui-image-comp-attribute.md#antialiased) API is added since API version 23.
```
