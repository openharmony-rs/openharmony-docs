# Image

The **Image** component is usually used to display images in applications. It supports data sources of the following types: [PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md), [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md), and [DrawableDescriptor](arkts-arkui-image-comp-drawabledescriptor-t.md). Supported image formats include PNG, JPG, JPEG, BMP, SVG, WEBP, GIF, HEIF, and TIFF. Note that the APNG and SVGA formats are not supported.

> **NOTE**

> - This component supports the TIFF image format since API version 23. > > - When keyboard shortcuts are used to copy an **Image** component, the **Image** component must be in a focused > state. For instructions on how to set focus, see > [Setting Whether a Component Is Focusable] > (../../../ui/arkts-common-events-focus-event.md#setting-whether-a-component-is-focusable). > By default, the **Image** component is not focusable. To enable it to gain focus, set both the > [focusable](arkts-arkui-common-comp-commonmethod-c.md#focusable) and [focusOnTouch](arkts-arkui-common-comp-commonmethod-c.md#focusontouch) attributes to > **true**. > > - The **Image** component supports SVG image sources. For details about SVG tags, see [SVG Tags](arkts-arkui-common-comp.md#common). > > - For animated images, animation playback is disabled by default and depends on the visibility of the **Image** > component. When the component is visible, the animation is started through the callback. When the component is > invisible, the animation is stopped. The visibility status of the **Image** component can be identified through the > > [onVisibleAreaChange] > [onVisibleAreaChange](arkts-arkui-common-comp-commonmethod-c.md#onvisibleareachange) > event. If the value of **ratios** is greater than 0, the component is visible. > > - For details about how to resolve white block issues during image loading, see > [Solution to White Image Blocks] > (https://developer.huawei.com/consumer/en/doc/best-practices/bpta-image-white-lump-solution). > For details about how to address slow image loading, see > [Optimizing Preset Image Loading] > (https://developer.huawei.com/consumer/en/doc/best-practices/bpta-texture-compression-improve- > performance#section91526132216). >

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

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| src | [PixelMap](arkts-arkui-common-comp-pixelmap-t.md) &#124; [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) &#124; [DrawableDescriptor](arkts-arkui-image-comp-drawabledescriptor-t.md) | Yes | Data source of the image. Local and online sources are supported. For details about how to reference an image, see [Loading Image Resources](../../../ui/arkts-graphics-display.md#loading-image-resources).<br>1. **PixelMap**: a pixel map storing graphical information, commonly used for image editing scenarios.<br>2. **ResourceStr**: a string or a Resource object.<br>The string type can be used to load local images and, more frequently, online images. When [using a local image referenced using a relative path](../../../reference/apis-arkui/arkui-ts/ts-basic-compon ents-image.md#example-25-displaying-an-image-using-a-relative-path), the **Image** component cannot be called across bundles or modules. If an image needs to be used globally, you are advised to use the Resource format.<br>Since DevEco Studio 6.0.0 Beta2, resources in non-**resource** directories are not packaged by default for new projects or modules. To enable packaging, go to **buildOption**   > **resOptions** > **copyCodeResource** to set **enable** to **true** in the module's **build-profile.json5** file. For details, see [resOptions](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-hvigor-build- profile#table1476161719356). <br>- Base64 strings are supported.<br>- When providing an HTTPS network image URL, refer to [Example 2: Downloading and Displaying Static Online Images](../../../reference/apis-arkui/arkui-ts/ts-basic- components-image.md#example-2-downloading-and-displaying-static-online-images) for implementation guidance.<br>- Strings prefixed with the **file://** path are supported (application sandbox URI: **file://&lt;bundleName&gt;/&lt;sandboxPath&gt;**). For details about how to construct the application sandbox path URI, see [constructor](../../apis-core-file-kit/arkts-apis/arkts-corefile-fileuri-fileuri-c.md#constructor). The sandbox path must be converted to an application sandbox URI using the [fileUri.getUriFromPath(path)](../../apis-core-file-kit/arkts-apis/arkts-corefile-fileuri-geturifrompath-f.md) API before being passed in for display. In addition, ensure that the application has the read permission to the files in the specified path.<br>The Resource format allows for access across bundles and modules. It is recommended for accessing local images. For details, see [Cross-HAP/HSP Resources](../../../quick-start/resource-categories-and-access.md#cross-haphsp-resources).<br> 3. **DrawableDescriptor**: an object created when the passed resource ID or name belongs to a common image. The [AnimatedDrawableDescriptor](../arkts-apis/arkts-arkui-arkui-drawabledescriptor-animateddrawabledescriptor-c.md) type can be passed to play animations from a **PixelMap** array.<br>**NOTE:** <br>- ArkTS widgets support GIF animations, but the animations only play once on display.<br>- ArkTS widgets do not support the strings with the **http://** or **file://** prefix. |

## Image

```TypeScript
Image(src: PixelMap | ResourceStr | DrawableDescriptor | ImageContent)
```

Obtains an image. The [ImageContent](arkts-arkui-image-comp-imagecontent-e.md) type allows you to specify the image content.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| src | [PixelMap](arkts-arkui-common-comp-pixelmap-t.md) &#124; [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) &#124; [DrawableDescriptor](arkts-arkui-image-comp-drawabledescriptor-t.md) &#124; [ImageContent](arkts-arkui-image-comp-imagecontent-e.md) | Yes | Data source of the image. Local and online sources are supported. For details about how to reference an image, see [Loading Image Resources](../../../ui/arkts-graphics-display.md#loading-image-resources).<br>For details about how to use **PixelMap**, **ResourceStr**, and **DrawableDescriptor**, see the **src** parameter description of [Image](../../../reference/apis-arkui/arkui-ts/ts-basic-components-image.md#image-1).<br> [ImageContent](arkts-arkui-image-comp-imagecontent-e.md): image content.<br>**NOTE:** <br>- ArkTS widgets support GIF animations, but the animations only play once on display.<br>- ArkTS widgets do not support the strings with the **http://** or **file://** prefix. |

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
| src | [PixelMap](arkts-arkui-common-comp-pixelmap-t.md) &#124; [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) &#124; [DrawableDescriptor](arkts-arkui-image-comp-drawabledescriptor-t.md) &#124; [ImageContent](arkts-arkui-image-comp-imagecontent-e.md) | Yes |  |
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
| src | [PixelMap](arkts-arkui-common-comp-pixelmap-t.md) &#124; [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) &#124; [DrawableDescriptor](arkts-arkui-image-comp-drawabledescriptor-t.md) | Yes | Data source of the image. Local and online sources are supported. For details about how to reference an image, see [Loading Image Resources](../../../ui/arkts-graphics-display.md#loading-image-resources).<br>For details about how to use **PixelMap**, **ResourceStr**, and **DrawableDescriptor**, see the **src** parameter description of [Image](../../../reference/apis-arkui/arkui-ts/ts-basic-components-image.md#image-1).<br>**NOTE:** <br>- ArkTS widgets support GIF animations, but the animations only play once on display.<br>- ArkTS widgets do not support the strings with the **http://** or **file://** prefix. |
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
| src | [PixelMap](arkts-arkui-common-comp-pixelmap-t.md) &#124; [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) &#124; [DrawableDescriptor](arkts-arkui-image-comp-drawabledescriptor-t.md) | Yes |  |
| imageAIOptions | [ImageAIOptions](../arkts-apis/arkts-arkui-imageaioptions-i.md) | No |  |
| reloadKey | string | No |  |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [ImageAlt](arkts-arkui-image-comp-imagealt-i.md) | Sets the placeholder image. |
| [ImageError](arkts-arkui-image-comp-imageerror-i.md) | Describes the object returned by the image loading error callback. |
| [ImageSourceSize](arkts-arkui-image-comp-imagesourcesize-i.md) | Defines source size of image. |
| [ResizableOptions](arkts-arkui-image-comp-resizableoptions-i.md) | Defines the resizable image options. |

### Types

| Name | Description |
| --- | --- |
| [BusinessError](arkts-arkui-image-comp-businesserror-t.md) | Represents the error information returned when an error occurs during image loading. |
| [DrawableDescriptor](arkts-arkui-image-comp-drawabledescriptor-t.md) | Represents a parameter object for the **Image** component. |
| [DrawingColorFilter](arkts-arkui-image-comp-drawingcolorfilter-t.md) | Represents a color filter object. |
| [DrawingLattice](arkts-arkui-image-comp-drawinglattice-t.md) | Represents a matrix grid object that divides an image into a rectangular grid. |
| [ImageErrorCallback](arkts-arkui-image-comp-imageerrorcallback-t.md) | Triggered when an error occurs during image loading. |
| [ImageMatrix](arkts-arkui-image-comp-imagematrix-t.md) | Represents the current matrix object. |
| [RequestDownloadInfo](arkts-arkui-image-comp-requestdownloadinfo-t.md) | Describes the download information when an online image fails to load or encounters an exception. This object contains resource information, network information, and performance statistics of the download task, which can be used to locate the cause of the loading exception. |
| [ResolutionQuality](arkts-arkui-image-comp-resolutionquality-t-sys.md) | Enumerates all the levels available for the image resolution quality. |

### Enums

| Name | Description |
| --- | --- |
| [DynamicRangeMode](arkts-arkui-image-comp-dynamicrangemode-e.md) | Describes the dynamic range of the image to be displayed. |
| [ImageContent](arkts-arkui-image-comp-imagecontent-e.md) | Defines the image content. |
| [ImageInterpolation](arkts-arkui-image-comp-imageinterpolation-e.md) | Interpolation effect of the image. |
| [ImageRenderMode](arkts-arkui-image-comp-imagerendermode-e.md) | Interpolation effect of the image. |
| [ImageRotateOrientation](arkts-arkui-image-comp-imagerotateorientation-e.md) | Describes the desired display orientation for image content. |

## Examples

### Example 1: Loading Images of Basic Types

This example demonstrates how to load images of basic types, such as PNG, GIF, SVG, and JPG, by passing in [Resource](ts-types.md#resource) resources.



```TypeScript
@Entry
@Component
struct ImageExample1 {
  build() {
    Column() {
      Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Start }) {
        Row() {
          // Load a PNG image.
          // Replace $r('app.media.ic_camera_master_ai_leaf') with the image resource file you use.
          Image($r('app.media.ic_camera_master_ai_leaf'))
            .width(110).height(110).margin(15)
            .overlay('png', { align: Alignment.Bottom, offset: { x: 0, y: 20 } })
          // Load a GIF image.
          // Replace $r('app.media.loading') with the image resource file you use.
          Image($r('app.media.loading'))
            .width(110).height(110).margin(15)
            .overlay('gif', { align: Alignment.Bottom, offset: { x: 0, y: 20 } })
        }
        Row() {
          // Load an SVG image.
          // Replace $r('app.media.ic_camera_master_ai_clouded') with the image resource file you use.
          Image($r('app.media.ic_camera_master_ai_clouded'))
            .width(110).height(110).margin(15)
            .overlay('svg', { align: Alignment.Bottom, offset: { x: 0, y: 20 } })
          // Load a JPG image.
          // Replace $r('app.media.ic_public_favor_filled') with the image resource file you use.
          Image($r('app.media.ic_public_favor_filled'))
            .width(110).height(110).margin(15)
            .overlay('jpg', { align: Alignment.Bottom, offset: { x: 0, y: 20 } })
        }
      }
    }.height(320).width(360).padding({ right: 10, top: 10 })
  }
}
```

### Example 2: Downloading and Displaying Static Online Images

The default timeout is 5 minutes for loading online images. When using an online image, you are advised to use alt to configure a placeholder image displayed during loading. You can use [HTTP](../../../network/http-request.md) to send a network request, and then decode the returned data into a PixelMap object for the Image component. Note that a GIF image loaded into a PixelMap object will be displayed as a static image. For details about image development, see the [Image Kit](../../../media/image/image-overview.md) overview.

The ohos.permission.INTERNET permission is required for using online images. For details about how to apply for a permission, see [Declaring Permissions](../../../security/AccessToken/declare-permissions.md).



```TypeScript
import { http } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';

@Entry
@Component
struct ImageExample2 {
  @State pixelMapImg: PixelMap | undefined = undefined;

  aboutToAppear() {
    this.requestImageUrl('https://www.example.com/xxx.png'); // Enter a specific online image URL.
  }

  requestImageUrl(url: string) {
    http.createHttp().request(url, (error: BusinessError, data: http.HttpResponse) => {
      if (error) {
        console.error(`request image failed: url: ${url}, code: ${error.code}, message: ${error.message}`);
      } else {
        let imgData: ArrayBuffer = data.result as ArrayBuffer;
        console.info(`request image success, size: ${imgData.byteLength}`);
        let imgSource: image.ImageSource = image.createImageSource(imgData);
        class sizeTmp {
          height: number = 100;
          width: number = 100;
        }
        let options: Record<string, number | boolean | sizeTmp> = {
          'alphaType': 0,
          'editable': false,
          'pixelFormat': 3,
          'scaleMode': 1,
          'size': { height: 100, width: 100 }
        }
        imgSource.createPixelMap(options).then((pixelMap: PixelMap) => {
          console.info('image createPixelMap success');
          this.pixelMapImg = pixelMap;
          imgSource.release();
        }).catch((err: BusinessError) => {
          console.error(`Failed to create pixel map. Code: ${err.code}, message: ${err.message}`);
          imgSource.release();
        })
      }
    })
  }

  build() {
    Column() {
      Image(this.pixelMapImg)
        // Replace $r('app.media.img') with the image resource file you use.
        .alt($r('app.media.img'))
        .objectFit(ImageFit.None)
        .width('100%')
        .height('100%')
    }
  }
}
```

### Example 3: Downloading and Displaying Online GIF Images

This example shows how to use the [cacheDownload.download](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-cachedownload-download-f.md) API to download online GIF images.

The ohos.permission.INTERNET permission is required for using online images. For details about how to apply for a permission, see [Declaring Permissions](../../../security/AccessToken/declare-permissions.md).

```TypeScript
import { cacheDownload } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  @State src: string = 'https://www.example.com/xxx.gif'; // Enter a specific online image URL.

  async aboutToAppear(): Promise<void> {
    // Provide configuration options for the cached download task.
    let options: cacheDownload.CacheDownloadOptions = {};
    try {
      // Perform cached download. If the download is successful, the resource will be cached to the specified file in the application memory or sandbox directory.
      cacheDownload.download(this.src, options);
      console.info(`success to download the resource. `);
    } catch (err) {
      console.error(`Failed to download the resource: code: ${err.code}, message: ${err.message}`);
    }
  }

  build() {
    Column() {
      // If src specifies an online image that has been successfully downloaded and cached, the image will be displayed without requiring re-downloading.
      Image(this.src)
        .width(100)
        .height(100)
        .objectFit(ImageFit.Cover)
        .borderWidth(1)
    }
    .height('100%')
    .width('100%')
  }
}
```

### Example 4: Adding Events to an Image

This example demonstrates how to add the [onClick](ts-universal-events-click.md#onclick) and [onFinish](#onfinish) events to an image.



```TypeScript
@Entry
@Component
struct ImageExample3 {
  // Replace $r('app.media.earth') with the image resource file you use.
  private imageOne: Resource = $r('app.media.earth');
  // Replace $r('app.media.star') with the image resource file you use.
  private imageTwo: Resource = $r('app.media.star');
  // Replace $r('app.media.moveStar') with the image resource file you use.
  private imageThree: Resource = $r('app.media.moveStar');
  @State src: Resource = this.imageOne;
  @State src2: Resource = this.imageThree;
  build(){
    Column(){
      // Add a click event so that a specific image is loaded upon clicking.
      Image(this.src)
        .width(100)
        .height(100)
        .onClick(() => {
          this.src = this.imageTwo;
        })

      // When the image to be loaded is in SVG format:
      Image(this.src2)
        .width(100)
        .height(100)
        .onFinish(() => {
          // Load another image when the SVG image has finished its animation.
          this.src2 = this.imageOne;
        })
    }.width('100%').height('100%')
  }
}
```

### Example 5: Enabling the AI Image Analyzer

This example shows how to enable the AI image analyzer using the [enableAnalyzer](#enableanalyzer11) API.



```TypeScript
import { image } from '@kit.ImageKit';

@Entry
@Component
struct ImageExample4 {
  @State imagePixelMap: image.PixelMap | undefined = undefined;
  private aiController: ImageAnalyzerController = new ImageAnalyzerController();
  private options: ImageAIOptions = {
    types: [ImageAnalyzerType.SUBJECT, ImageAnalyzerType.TEXT],
    aiController: this.aiController
  };

  async aboutToAppear() {
    // Replace $r('app.media.app_icon') with the image resource file you use.
    this.imagePixelMap = await this.getPixmapFromMedia($r('app.media.app_icon'));
  }

  build() {
    Column() {
      Image(this.imagePixelMap, this.options)
        .enableAnalyzer(true)
        .width(200)
        .height(200)
        .margin({bottom:10})
      Button('getTypes', { type: ButtonType.Circle, stateEffect: false })
        .width(100)
        .height(100)
        .onClick(() => {
          this.aiController.getImageAnalyzerSupportTypes();
        })
    }
  }
  private async getPixmapFromMedia(resource: Resource) {
    let unit8Array = await this.getUIContext().getHostContext()?.resourceManager?.getMediaContent(resource.id);
    let imageSource = image.createImageSource(unit8Array?.buffer.slice(0, unit8Array.buffer.byteLength));
    let pixelMap: image.PixelMap = await imageSource.createPixelMap({
      desiredPixelFormat: image.PixelMapFormat.RGBA_8888
    });
    await imageSource.release();
    return pixelMap;
  }
}
```

### Example 6: Stretching an Image Using slice

This example demonstrates how to stretch an image in different directions using the slice option of the [resizable](#resizable11) attribute.



```TypeScript
@Entry
@Component
struct Index {
  @State top: number = 10;
  @State bottom: number = 10;
  @State left: number = 10;
  @State right: number = 10;

  build() {
    Column({ space: 5 }) {
      // Original image effect
      // Replace $r('app.media.landscape') with the image resource file you use.
      Image($r('app.media.landscape'))
        .width(200).height(200)
        .border({ width: 2, color: Color.Pink })
        .objectFit(ImageFit.Contain)

      // Set the resizable attribute to stretch the image in different directions.
      // Replace $r('app.media.landscape') with the image resource file you use.
      Image($r('app.media.landscape'))
        .resizable({
          slice: {
            // When a number is passed in, it uses the default vp unit, which is parsed into different px sizes on different devices. Choose the unit based on your needs.
            left: `${this.left}px`,
            right: `${this.right}px`,
            top: `${this.top}px`,
            bottom: `${this.bottom}px`
          }
        })
        .width(200)
        .height(200)
        .border({ width: 2, color: Color.Pink })
        .objectFit(ImageFit.Contain)

      Row() {
        Button('add top to ' + this.top).fontSize(10)
          .onClick(() => {
            this.top += 10;
          })
        Button('add bottom to ' + this.bottom).fontSize(10)
          .onClick(() => {
            this.bottom += 10;
          })
      }

      Row() {
        Button('add left to ' + this.left).fontSize(10)
          .onClick(() => {
            this.left += 10;
          })
        Button('add right to ' + this.right).fontSize(10)
          .onClick(() => {
            this.right += 10;
          })
      }

    }
    .justifyContent(FlexAlign.Start).width('100%').height('100%')
  }
}
```

### Example 7: Stretching an Image Using lattice

This example demonstrates how to stretch an image using the lattice option of the [resizable](#resizable11) attribute with a rectangular lattice object.



```TypeScript
import { drawing } from '@kit.ArkGraphics2D';

@Entry
@Component
struct drawingLatticeTest {
  private xDivs: Array<number> = [1, 2, 200];
  private yDivs: Array<number> = [1, 2, 200];
  private fXCount: number = 3;
  private fYCount: number = 3;
  private drawingLatticeFirst: DrawingLattice =
    drawing.Lattice.createImageLattice(this.xDivs, this.yDivs, this.fXCount, this.fYCount);

  build() {
    Scroll() {
      Column({ space: 10 }) {
        Text('Original Image').fontSize(20).fontWeight(700)
        Column({ space: 10 }) {
          // Replace $r('app.media.mountain') with the image resource file you use.
          Image($r('app.media.mountain'))
            .width(260).height(260)
        }.width('100%')

        Text('Resize by lattice').fontSize(20).fontWeight(700)
        Column({ space: 10 }) {
          // Replace $r('app.media.mountain') with the image resource file you use.
          Image($r('app.media.mountain'))
            .objectRepeat(ImageRepeat.X)
            .width(260)
            .height(260)
            .resizable({
              lattice: this.drawingLatticeFirst
            })
        }.width('100%')
      }.width('100%')
    }
  }
}
```

### Example 8: Playing a PixelMap Array Animation

This example demonstrates how to play an animation using a PixelMap array through an [AnimatedDrawableDescriptor](../arkts-apis/arkts-arkui-arkui-drawabledescriptor-animateddrawabledescriptor-c.md) object.



```TypeScript
import { AnimationOptions, AnimatedDrawableDescriptor } from '@kit.ArkUI';
import { image } from '@kit.ImageKit';

@Entry
@Component
struct ImageExample {
  pixelMaps: PixelMap[] = [];
  @State options: AnimationOptions = { iterations: 1 };
  @State animated: AnimatedDrawableDescriptor | undefined = undefined;

  async aboutToAppear() {
    this.pixelMaps = await this.getPixelMaps();
    this.animated = new AnimatedDrawableDescriptor(this.pixelMaps, this.options);
  }

  build() {
    Column() {
      Row() {
        Image(this.animated)
          .width('500px').height('500px')
          .onFinish(() => {
            // When the image source of the Image component is an AnimatedDrawableDescriptor object, the onFinish callback will not be executed.
            console.info('finish');
          })
      }.height('50%')

      Row() {
        Button('once').width(100).padding(5).onClick(() => {
          this.options = { iterations: 1 };
          this.animated = new AnimatedDrawableDescriptor(this.pixelMaps, this.options);
        }).margin(5)
        Button('infinite').width(100).padding(5).onClick(() => {
          this.options = { iterations: -1 };
          this.animated = new AnimatedDrawableDescriptor(this.pixelMaps, this.options);
        }).margin(5)
      }
    }.width('50%')
  }

  private async getPixmapListFromMedia(resource: Resource) {
    let unit8Array = await this.getUIContext().getHostContext()?.resourceManager?.getMediaContent(resource.id);
    let imageSource = image.createImageSource(unit8Array?.buffer.slice(0, unit8Array.buffer.byteLength));
    let createPixelMap: image.PixelMap[] = await imageSource.createPixelMapList({
      desiredPixelFormat: image.PixelMapFormat.RGBA_8888
    });
    await imageSource.release();
    return createPixelMap;
  }

  private async getPixmapFromMedia(resource: Resource) {
    let unit8Array = await this.getUIContext().getHostContext()?.resourceManager?.getMediaContent(resource.id);
    let imageSource = image.createImageSource(unit8Array?.buffer.slice(0, unit8Array.buffer.byteLength));
    let pixelMap: image.PixelMap = await imageSource.createPixelMap({
      desiredPixelFormat: image.PixelMapFormat.RGBA_8888
    });
    await imageSource.release();
    return pixelMap;
  }

  private async getPixelMaps() {
    // Replace $r('app.media.mountain') with the image resource file you use.
    let myPixelMaps: PixelMap[] = await this.getPixmapListFromMedia($r('app.media.mountain')); // Add the image.
    // Replace $r('app.media.sky') with the image resource file you use.
    myPixelMaps.push(await this.getPixmapFromMedia($r('app.media.sky')));
    // Replace $r('app.media.clouds') with the image resource file you use.
    myPixelMaps.push(await this.getPixmapFromMedia($r('app.media.clouds')));
    // Replace $r('app.media.landscape') with the image resource file you use.
    myPixelMaps.push(await this.getPixmapFromMedia($r('app.media.landscape')));
    return myPixelMaps;
  }
}
```

### Example 9: Setting a Color Filter for an Image

This example shows how to set a color filter for an image using the [colorFilter](#colorfilter9) attribute.



```TypeScript
import { drawing, common2D } from '@kit.ArkGraphics2D';

@Entry
@Component
struct ImageExample3 {
  // When the image to be loaded is in SVG format:
  // Replace $r('app.media.svg1') with the image resource file you use.
  private imageOne: Resource = $r('app.media.svg1');
  // Replace $r('app.media.1') with the image resource file you use.
  private imageTwo: Resource = $r('app.media.1');
  @State src: Resource = this.imageOne;
  @State src2: Resource = this.imageTwo;
  private colorFilterMatrix: number[] = [1, 0, 0, 0, 0.5,
                                         0, 1, 0, 0, 0,
                                         0, 0, 1, 0, 0,
                                         0, 0, 0, 1, 0];
  private color: common2D.Color = {
    alpha: 255,
    red: 255,
    green: 0,
    blue: 0
  };
  @State drawingColorFilterFirst: ColorFilter | undefined = undefined;
  @State drawingColorFilterSecond: ColorFilter | undefined = undefined;
  @State drawingColorFilterThird: ColorFilter | undefined = undefined;

  build() {
    Column() {
      Image(this.src)
        .width(100)
        .height(100)
        .colorFilter(this.drawingColorFilterFirst)
        .onClick(()=>{
          this.drawingColorFilterFirst =
            drawing.ColorFilter.createBlendModeColorFilter(this.color, drawing.BlendMode.SRC_IN);
        })

      Image(this.src2)
        .width(100)
        .height(100)
        .colorFilter(this.drawingColorFilterSecond)
        .onClick(()=>{
          this.drawingColorFilterSecond = new ColorFilter(this.colorFilterMatrix);
        })

      // When the image to be loaded is in SVG format:
      // Replace $r('app.media.svg2') with the image resource file you use.
      Image($r('app.media.svg2'))
        .width(110)
        .height(110)
        .margin(15)
        .colorFilter(this.drawingColorFilterThird)
        .onClick(()=>{
          this.drawingColorFilterThird =
            drawing.ColorFilter.createBlendModeColorFilter(this.color, drawing.BlendMode.SRC_IN);
        })
    }
  }
}
```

### Example 10: Setting the Fill Effect for an Image

This example shows how to use the [objectFit](#objectfit) attribute to specify how an image is resized to fit its container.



```TypeScript
@Entry
@Component
struct ImageExample{
  build() {
    Column() {
      Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Start }) {
        Row() {
          // Load a PNG image.
          // Replace $r('app.media.sky') with the image resource file you use.
          Image($r('app.media.sky'))
            .width(110).height(110).margin(15)
            .overlay('png', { align: Alignment.Bottom, offset: { x: 0, y: 20 } })
            .border({ width: 2, color: Color.Pink })
            .objectFit(ImageFit.TOP_START)
          // Load a GIF image.
          // Replace $r('app.media.loading') with the image resource file you use.
          Image($r('app.media.loading'))
            .width(110).height(110).margin(15)
            .overlay('gif', { align: Alignment.Bottom, offset: { x: 0, y: 20 } })
            .border({ width: 2, color: Color.Pink })
            .objectFit(ImageFit.BOTTOM_START)
        }
        Row() {
          // Load an SVG image.
          // Replace $r('app.media.svg') with the image resource file you use.
          Image($r('app.media.svg'))
            .width(110).height(110).margin(15)
            .overlay('svg', { align: Alignment.Bottom, offset: { x: 0, y: 20 } })
            .border({ width: 2, color: Color.Pink })
            .objectFit(ImageFit.TOP_END)
          // Load a JPG image.
          // Replace $r('app.media.jpg') with the image resource file you use.
          Image($r('app.media.jpg'))
            .width(110).height(110).margin(15)
            .overlay('jpg', { align: Alignment.Bottom, offset: { x: 0, y: 20 } })
            .border({ width: 2, color: Color.Pink })
            .objectFit(ImageFit.CENTER)
        }
      }
    }.height(320).width(360).padding({ right: 10, top: 10 })
  }
}
```

### Example 11: Switching Between Different Types of Images

This example demonstrates the effect of displaying images with [ResourceStr](ts-types.md#resourcestr) and [ImageContent](arkts-arkui-image-comp-imagecontent-e.md) as types of data sources.



```TypeScript
@Entry
@Component
struct ImageContentExample {
  @State imageSrcIndex: number = 0;
  // Replace $r('app.media.app_icon') with the image resource file you use.
  @State imageSrcList: (ResourceStr | ImageContent)[] = [$r('app.media.app_icon'), ImageContent.EMPTY];

  build() {
    Column({ space: 10 }) {
      Image(this.imageSrcList[this.imageSrcIndex])
        .width(100)
        .height(100)
      Button('Change Image src', { type: ButtonType.Capsule, stateEffect: false })
        .height(50)
        .onClick(() => {
          this.imageSrcIndex = (this.imageSrcIndex + 1) % this.imageSrcList.length;
        })
    }.width('100%')
    .padding(20)
  }
}
```

### Example 12: Securing Sensitive Information

This example shows how to secure sensitive information on widgets using the [privacySensitive](#privacysensitive12) attribute. The display requires widget framework support.



```TypeScript
@Entry
@Component
struct ImageExample {
  build() {
    Column({ space: 10 }) {
      // Replace $r('app.media.startIcon') with the image resource file you use.
      Image($r('app.media.startIcon'))
        .width(50)
        .height(50)
        .margin({top :30})
        .privacySensitive(true)
    }
    .alignItems(HorizontalAlign.Center)
    .width('100%')
  }
}
```

### Example 13: Setting the Scan Effect for an Image

This example shows how to enable the scan effect for an image using [linearGradient](./ts-basic-components-datapanel.md#lineargradient10) and [animateTo()](../arkts-apis-uicontext-uicontext.md#animateto).



```TypeScript
import { curves } from '@kit.ArkUI';

@Entry
@Component
struct ImageExample11 {
  private curve = curves.cubicBezierCurve(0.33, 0, 0.67, 1);
  @State moveImg: string[] = ['imageScanEffect'];
  @State moveImgVisible: Visibility = Visibility.Visible;
  @State durationTime: number = 1500;
  @State iterationsTimes: number = -1;
  @State private opacityValue: number = 0.5;
  @State imageWidth: number = 450;
  @State visible: Visibility = Visibility.Hidden;
  @State stackBackgroundColor: string = '#E1E4E9';
  @State linePositionX: number = 0 - this.imageWidth;
  @State linePositionY: number = 0;
  @State imgResource: Resource | undefined = undefined;

  startupAnimate() {
    this.moveImg.pop();
    this.moveImg.push('imageScanEffect');
    setTimeout(() => {
      // Replace $r('app.media.img') with the image resource file you use.
      this.imgResource = $r('app.media.img');
    }, 3000);
    this.getUIContext()?.animateTo({
      duration: this.durationTime,
      curve: this.curve,
      tempo: 1,
      iterations: this.iterationsTimes,
      delay: 0
    }, () => {
      this.linePositionX = this.imageWidth;
    })
  }

  build() {
    Column() {
      Row() {
        Stack() {
          Image(this.imgResource)
            .width(this.imageWidth)
            .height(200)
            .objectFit(ImageFit.Contain)
            .visibility(this.visible)
            .onComplete(() => {
              this.visible = Visibility.Visible;
              this.moveImg.pop();
            })
            .onError(() =>{
              setTimeout(() => {
                this.visible = Visibility.Visible;
                this.moveImg.pop();
              }, 2600)
            })
          ForEach(this.moveImg, (item: string) => {
            Row()
              .width(this.imageWidth)
              .height(200)
              .visibility(this.moveImgVisible)
              .position({ x: this.linePositionX, y: this.linePositionY })
              .linearGradient({
                direction: GradientDirection.Right,
                repeating: false,
                colors: [[0xE1E4E9, 0], [0xFFFFFF, 0.75], [0xE1E4E9, 1]]
              })
              .opacity(this.opacityValue)
          })
        }
        .backgroundColor(this.visible ? this.stackBackgroundColor : undefined)
        .margin({top: 20, left: 20, right: 20})
        .borderRadius(20)
        .clip(true)
        .onAppear(() => {
          this.startupAnimate();
        })
      }
    }
  }
}
```

### Example 14: Adding Transform Effects to an Image

This example demonstrates how to apply rotation and translation effects to an image using the [imageMatrix](#imagematrix15) and [objectFit](#objectfit) attributes.

The imageMatrix attribute is added since API version 15.



```TypeScript
import { matrix4 } from '@kit.ArkUI';

@Entry
@Component
struct Test {
  private matrix1 = matrix4.identity()
    .translate({ x: -400, y: -750 })
    .scale({ x: 0.5, y: 0.5 })
    .rotate({
      x: 2,
      y: 0.5,
      z: 3,
      centerX: 10,
      centerY: 10,
      angle: -10
    })

  build() {
    Row() {
      Column({ space: 50 }) {
        Column({ space: 5 }) {
          // Replace $r('app.media.example') with the image resource file you use.
          Image($r('app.media.example'))
            .border({ width:2, color: Color.Black })
            .objectFit(ImageFit.Contain)
            .width(150)
            .height(150)
          Text('No transformation')
            .fontSize('25px')
        }
        Column({ space: 5 }) {
          // Replace $r('app.media.example') with the image resource file you use.
          Image($r('app.media.example'))
            .border({ width:2, color: Color.Black })
            .objectFit(ImageFit.None)
            .translate({ x: 10, y: 10 })
            .scale({ x: 0.5, y: 0.5 })
            .width(100)
            .height(100)
          Text('Direct transformation on the image, with the upper left corner of the image source displayed by default')
            .fontSize('25px')
        }
        Column({ space: 5 }) {
          // Replace $r('app.media.example') with the image resource file you use.
          Image($r('app.media.example'))
            .objectFit(ImageFit.MATRIX)
            .imageMatrix(this.matrix1)
            .border({ width:2, color: Color.Black })
            .width(150)
            .height(150)
          Text('Transformation using imageMatrix to adjust the source position for optimal display')
            .fontSize('25px')
        }
      }
      .width('100%')
    }
  }
}
```

### Example 15: Setting the Image Decoding Size Using sourceSize

This example uses the [sourceSize](#sourcesize) API to customize the image decoding size.



```TypeScript
@Entry
@Component
struct Index {
  build() {
    Column() {
      // Replace $r('app.media.sky') with the image resource file you use.
      Image($r('app.media.sky'))
        .sourceSize({width:1393, height:1080})
        .height(300)
        .width(300)
        .objectFit(ImageFit.Contain)
        .borderWidth(1)
      // Replace $r('app.media.sky') with the image resource file you use.
      Image($r('app.media.sky'))
        .sourceSize({width:13, height:10})
        .height(300)
        .width(300)
        .objectFit(ImageFit.Contain)
        .borderWidth(1)
    }
    .height('100%')
    .width('100%')
  }
}
```

### Example 16: Setting the Image Rendering Mode Using renderMode

This example uses the [renderMode](#rendermode) API to set the image rendering mode to monochrome.



```TypeScript
@Entry
@Component
struct Index {
  build() {
    Column() {
      // Replace $r('app.media.sky') with the image resource file you use.
      Image($r('app.media.sky'))
        .renderMode(ImageRenderMode.Template)
        .height(300)
        .width(300)
        .objectFit(ImageFit.Contain)
        .borderWidth(1)
    }
    .height('100%')
    .width('100%')
  }
}
```

### Example 17: Setting the Image Repeat Pattern Using objectRepeat

This example uses the [objectRepeat](arkts-arkui-image-comp-attribute.md#objectrepeat) API to repeat the image along the vertical axis.



```TypeScript
@Entry
@Component
struct Index {
  build() {
    Column() {
      // Replace $r('app.media.sky') with the image resource file you use.
      Image($r('app.media.sky'))
        .objectRepeat(ImageRepeat.Y)
        .height('90%')
        .width('90%')
        .objectFit(ImageFit.Contain)
        .borderWidth(1)
    }
    .height('100%')
    .width('100%')
  }
}
```

### Example 18: Setting the Fill Color for an SVG Image

This example shows how to set different fill colors for an SVG image using the [fillColor](#fillcolor15) attribute.



```TypeScript
@Entry
@Component
struct Index {
  build() {
    Column() {
      Text('FillColor not set')
      // Replace $r('app.media.svgExample') with the image resource file you use.
      Image($r('app.media.svgExample'))
        .height(100)
        .width(100)
        .objectFit(ImageFit.Contain)
        .borderWidth(1)
      Text('fillColor set to ColorContent.ORIGIN')
      // Replace $r('app.media.svgExample') with the image resource file you use.
      Image($r('app.media.svgExample'))
        .height(100)
        .width(100)
        .objectFit(ImageFit.Contain)
        .borderWidth(1)
        .fillColor(ColorContent.ORIGIN)
      Text('fillColor set to Color.Blue')
      // Replace $r('app.media.svgExample') with the image resource file you use.
      Image($r('app.media.svgExample'))
        .height(100)
        .width(100)
        .objectFit(ImageFit.Contain)
        .borderWidth(1)
        .fillColor(Color.Blue)
      Text('fillColor set to undefined')
      // Replace $r('app.media.svgExample') with the image resource file you use.
      Image($r('app.media.svgExample'))
        .height(100)
        .width(100)
        .objectFit(ImageFit.Contain)
        .borderWidth(1)
        .fillColor(undefined)
    }
    .height('100%')
    .width('100%')
  }
}
```

### Example 19: Adjusting HDR Image Brightness

This example demonstrates how to adjust the HDR image brightness using the [hdrBrightness](#hdrbrightness19) attribute, changing the value from 0 to 1.

The hdrBrightness attribute is added since API version 19.

```TypeScript
import { image } from '@kit.ImageKit';

const TAG = 'AceImage';

@Entry
@Component
struct Index {
  // Replace 'img_1' with the image resource file you use.
  @State imgUrl: string = 'img_1';
  @State bright: number = 0; // The default brightness is 0.
  aboutToAppear(): void {
    // Obtain media resources from the resource manager.
    let img = this.getUIContext().getHostContext()?.resourceManager.getMediaByNameSync(this.imgUrl);
    // Create an image source and obtain image information.
    if (img && img.buffer) {
      let imageSource = image.createImageSource(img?.buffer.slice(0));
      let imageInfo = imageSource.getImageInfoSync();
      // Check whether the image information is obtained successfully.
      if (imageInfo == undefined) {
        console.error(TAG, 'Failed to obtain the image information.');
      } else {
        // After the image information is obtained successfully, print the HDR status.
        console.info(TAG, 'imageInfo.isHdr:' + imageInfo.isHdr);
      }
      imageSource.release();
    } else {
      console.error(TAG, 'Failed to obtain the image buffer.');
    }
  }

  build() {
    Column() {
      // Replace $r('app.media.img_1') with the image resource file you use.
      Image($r('app.media.img_1')).width('50%')
        .height('auto')
        .margin({ top: 160 })
        .hdrBrightness(this.bright) // Set the HDR image brightness controlled by the bright state.
      Button('Adjust Brightness 0 -> 1')
        .onClick(() => {
          // Animation transition for brightness changes
          this.getUIContext()?.animateTo({}, () => {
            this.bright = 1.0 - this.bright;
          });
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

### Example 20: Setting Whether the Image Follows the System Language Direction

This example shows how to use the [matchTextDirection](arkts-arkui-image-comp-attribute.md#matchtextdirection) API to set whether the image should be mirrored when the device system language is set to Uyghur.



```TypeScript
@Entry
@Component
struct Index {
  build() {
    Column() {
      Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Start }) {
        Row() {
          // The image does not follow the system language direction.
          // Replace $r('app.media.ocean') with the image resource file you use.
          Image($r('app.media.ocean'))
            .width(110).height(110).margin(15)
            .matchTextDirection(false)
        }
        Row() {
          // The image follows the system language direction.
          // Replace $r('app.media.ocean') with the image resource file you use.
          Image($r('app.media.ocean'))
            .width(110).height(110).margin(15)
            .matchTextDirection(true)
        }
      }
    }.height(320).width(360).padding({ right: 10, top: 10 })
  }
}
```

### Example 21: Setting Image Display Orientation

This example shows how to configure different image display orientations using the [orientation](#orientation14) attribute.



```TypeScript
@Entry
@Component
struct OrientationExample {
  build() {
    Column() {
      Row({ space: 25 }) {
        Column() {
          Text('AUTO')
          // Replace $r('app.media.hello') with the image resource file you use.
          Image($r('app.media.hello'))
            .width(125).height(125)
            .orientation(ImageRotateOrientation.AUTO)
        }

        Column() {
          Text('UP')
          // Replace $r('app.media.hello') with the image resource file you use.
          Image($r('app.media.hello'))
            .width(125).height(125)
            .orientation(ImageRotateOrientation.UP)
        }

        Column() {
          Text('RIGHT')
          // Replace $r('app.media.hello') with the image resource file you use.
          Image($r('app.media.hello'))
            .width(125).height(125)
            .orientation(ImageRotateOrientation.RIGHT)
        }
      }

      Row({ space: 25 }) {
        Column() {
          Text('DOWN')
          // Replace $r('app.media.hello') with the image resource file you use.
          Image($r('app.media.hello'))
            .width(125).height(125)
            .orientation(ImageRotateOrientation.DOWN)
        }

        Column() {
          Text('LEFT')
          // Replace $r('app.media.hello') with the image resource file you use.
          Image($r('app.media.hello'))
            .width(125).height(125)
            .orientation(ImageRotateOrientation.LEFT)
        }

        Column() {
          Text('UP_MIRRORED')
          // Replace $r('app.media.hello') with the image resource file you use.
          Image($r('app.media.hello'))
            .width(125).height(125)
            .orientation(ImageRotateOrientation.UP_MIRRORED)
        }
      }

      Row({ space: 15 }) {
        Column() {
          Text('RIGHT_MIRRORED')
          // Replace $r('app.media.hello') with the image resource file you use.
          Image($r('app.media.hello'))
            .width(125).height(125)
            .orientation(ImageRotateOrientation.RIGHT_MIRRORED)
        }

        Column() {
          Text('DOWN_MIRRORED')
          // Replace $r('app.media.hello') with the image resource file you use.
          Image($r('app.media.hello'))
            .width(125).height(125)
            .orientation(ImageRotateOrientation.DOWN_MIRRORED)
        }

        Column() {
          Text('LEFT_MIRRORED')
          // Replace $r('app.media.hello') with the image resource file you use.
          Image($r('app.media.hello'))
            .width(125).height(125)
            .orientation(ImageRotateOrientation.LEFT_MIRRORED)
        }
      }
    }
  }
}
```

### Example 22: Using EXIF Metadata for Image Display Orientation

This example demonstrates how to use the [getImageProperty](../../apis-image-kit/arkts-apis-image-ImageSource.md#getimageproperty) API to obtain the EXIF metadata of an image, and then set the image display orientation through the [orientation](#orientation14) attribute based on the obtained EXIF metadata.



```TypeScript
import { image } from '@kit.ImageKit';
import { resourceManager } from '@kit.LocalizationKit';

@Entry
@Component
struct Example {
  @State rotateOrientation: ImageRotateOrientation = ImageRotateOrientation.UP;
  @State pixelMap: image.PixelMap | undefined = undefined;
  @State text1: string = 'The exif orientation is ';
  @State text2: string = 'Set orientation to ';

  // Convert EXIF orientation information into ImageRotateOrientation.
  getOrientation(orientation: string): ImageRotateOrientation {
    if (orientation == 'Top-right') {
      this.text2 = this.text2 + 'UP_MIRRORED';
      return ImageRotateOrientation.UP_MIRRORED;
    } else if (orientation == 'Bottom-right') {
      this.text2 = this.text2 + 'DOWN';
      return ImageRotateOrientation.DOWN;
    } else if (orientation == 'Bottom-left') {
      this.text2 = this.text2 + 'DOWN_MIRRORED';
      return ImageRotateOrientation.DOWN_MIRRORED;
    } else if (orientation == 'Left-top') {
      this.text2 = this.text2 + 'LEFT_MIRRORED';
      return ImageRotateOrientation.LEFT_MIRRORED;
    } else if (orientation == 'Right-top') {
      this.text2 = this.text2 + 'RIGHT';
      return ImageRotateOrientation.RIGHT;
    } else if (orientation == 'Right-bottom') {
      this.text2 = this.text2 + 'RIGHT_MIRRORED';
      return ImageRotateOrientation.RIGHT_MIRRORED;
    } else if (orientation == 'Left-bottom') {
      this.text2 = this.text2 + 'LEFT';
      return ImageRotateOrientation.LEFT;
    } else if (orientation == 'Top-left') {
      this.text2 = this.text2 + 'UP';
      return ImageRotateOrientation.UP;
    } else {
      this.text2 = this.text2 + 'UP';
      return ImageRotateOrientation.UP;
    }
  }

  async getFileBuffer(context: Context): Promise<ArrayBuffer | undefined> {
    try {
      const resourceMgr: resourceManager.ResourceManager = context.resourceManager;
      // Obtain the content of the resource file with EXIF data as Uint8Array.
      // Replace 'hello.jpg' with the image resource file you use.
      const fileData: Uint8Array = await resourceMgr.getRawFileContent('hello.jpg');
      console.info('Successfully get RawFileContent');
      // Convert the array to an ArrayBuffer and return the ArrayBuffer.
      const buffer: ArrayBuffer = fileData.buffer.slice(0);
      return buffer;
    } catch (error) {
      console.error('Failed to get RawFileContent');
      return undefined;
    }
  }

  aboutToAppear() {
    let context = this.getUIContext().getHostContext();
    if (!context) {
      return;
    }
    this.getFileBuffer(context).then((buf: ArrayBuffer | undefined) => {
      let imageSource = image.createImageSource(buf);
      if (!imageSource) {
        return;
      }
      // Obtain EXIF orientation information.
      imageSource.getImageProperty(image.PropertyKey.ORIENTATION).then((orientation) => {
        this.rotateOrientation = this.getOrientation(orientation);
        this.text1 = this.text1 + orientation;
        let options: image.DecodingOptions = {
          'editable': true,
          'desiredPixelFormat': image.PixelMapFormat.RGBA_8888,
        }
        imageSource.createPixelMap(options).then((pixelMap: image.PixelMap) => {
          this.pixelMap = pixelMap;
          imageSource.release();
        });
      }).catch(() => {
        imageSource.release();
      });
    })
  }

  build() {
    Column({ space: 40 }) {
      Column({ space: 10 }) {
        Text('before').fontSize(20).fontWeight(700)
        // Replace 'hello.jpg' with the image resource file you use.
        Image($rawfile('hello.jpg'))
          .width(100)
          .height(100)
        Text(this.text1)
      }

      Column({ space: 10 }) {
        Text('after').fontSize(20).fontWeight(700)
        Image(this.pixelMap)
          .width(100)
          .height(100)
          .orientation(this.rotateOrientation)
        Text(this.text2)
      }
    }
    .height('80%')
    .width('100%')
  }
}
```

### Example 23: Dynamically Switching an SVG Image Between Fill Colors

This example demonstrates how to dynamically switch an SVG Image between fill colors across different color spaces using ColorMetrics.



```TypeScript
import { ColorMetrics } from '@kit.ArkUI';
@Entry
@Component
struct fillColorMetricsDemo {
  @State p3Red: ColorMetrics = ColorMetrics.colorWithSpace(ColorSpace.DISPLAY_P3, 0.631, 0.0392, 0.1294);
  @State sRGBRed: ColorMetrics = ColorMetrics.colorWithSpace(ColorSpace.SRGB, 0.631, 0.0392, 0.1294);
  @State p3Green: ColorMetrics = ColorMetrics.colorWithSpace(ColorSpace.DISPLAY_P3, 0.09, 0.662 ,0.552);
  @State sRGBGreen: ColorMetrics = ColorMetrics.colorWithSpace(ColorSpace.SRGB, 0.09, 0.662 ,0.552);
  @State p3Blue: ColorMetrics = ColorMetrics.colorWithSpace(ColorSpace.DISPLAY_P3, 0, 0.290 ,0.686);
  @State sRGBBlue: ColorMetrics = ColorMetrics.colorWithSpace(ColorSpace.SRGB, 0, 0.290 ,0.686);
  @State colorArray: (Color|undefined|ColorMetrics|ColorContent)[] = [
    this.p3Red, this.sRGBRed, this.p3Green, this.sRGBGreen, this.p3Blue,
    this.sRGBBlue, ColorContent.ORIGIN, Color.Gray, undefined
  ]
  @State colorArrayStr: string[] = [
    'P3 Red', 'SRGB Red', 'P3 Green', 'SRGB Green',
    'P3 Blue', 'SRGB Blue', 'ORIGIN', 'Gray', 'undefined'
  ]
  @State arrayIdx: number = 0
  build() {
    Column() {
      Text('FillColor is ' + this.colorArrayStr[this.arrayIdx])
      // Replace $r('app.media.svgExample') with the image resource file you use.
      Image($r('app.media.svgExample'))
        .width(110).height(110).margin(15)
        .fillColor(this.colorArray[this.arrayIdx])
      Button('ChangeFillColor')
        .onClick(()=>{
          this.arrayIdx = (this.arrayIdx + 1) % this.colorArray.length
        })
      Blank().height(30).width('100%')
      Text('FillColor is SRGB Red')
      // Replace $r('app.media.svgExample') with the image resource file you use.
      Image($r('app.media.svgExample'))
        .width(110).height(110).margin(15)
        .fillColor(this.sRGBRed)
      Blank().height(30).width('100%')
      Text('FillColor is SRGB Green')
      // Replace $r('app.media.svgExample') with the image resource file you use.
      Image($r('app.media.svgExample'))
        .width(110).height(110).margin(15)
        .fillColor(this.sRGBGreen)
      Blank().height(30).width('100%')
      Text('FillColor is SRGB Blue')
      // Replace $r('app.media.svgExample') with the image resource file you use.
      Image($r('app.media.svgExample'))
        .width(110).height(110).margin(15)
        .fillColor(this.sRGBBlue)
    }
  }
}
```

### Example 24: Displaying an Image Using an Application Sandbox Path

This example demonstrates how to display an image using the application sandbox path, where a preloaded image named cloud.png is placed in the haps/entry/files directory of the current application.



```TypeScript
import { fileUri } from '@kit.CoreFileKit';

@Entry
@Component
struct Index {
  private getSandBoxUri(): string {
    let context = this.getUIContext().getHostContext();
    if (!context) {
      return '';
    }
    // /data/storage/el2/base/haps/entry/files/cloud.png
    // Obtain the URI from the file path in the application sandbox.
    // Replace '/cloud.png' with the image resource file you use.
    return fileUri.getUriFromPath(context.filesDir + '/cloud.png');
  }

  build() {
    Column() {
      Image(this.getSandBoxUri())
        .width(150)
        .height(150)
    }
    .height('100%')
    .width('100%')
  }
}
```

### Example 25: Displaying an Image Using a Relative Path

This example demonstrates how to display an image using a relative path. First, create a common directory at the same level as the project's pages directory. Then, place a preloaded image named cloud1.png in the common directory and display it using the relative path.



```TypeScript
@Entry
@Component
struct Index {
  build() {
    Column({ space: 10 }) {
      Image('common/cloud1.png')
        .width(100)
        .height(100)
    }
    .height('100%')
    .width('100%')
  }
}
```

### Example 26: Displaying an SVG Image Using supportSvg2

In this example, the [supportSvg2](#supportsvg221) attribute is set to enable the enhanced SVG tag parsing feature.

The supportSvg2 attribute is added since API version 21.



```TypeScript
@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Text('supportSvg2 is set to true.')
        // Replace $rawfile('image.svg') with the image resource file you use.
        Image($rawfile('image.svg'))
          .width(200)
          .height(200)
          .border({ width: 2, color: 'red' })
          .supportSvg2(true)
          .margin({ bottom: 30 })
        Text('supportSvg2 is set to false (default value).')
        // Replace $rawfile('image.svg') with the image resource file you use.
        Image($rawfile('image.svg'))
          .width(200)
          .height(200)
          .border({ width: 2, color: 'red' })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### Example 27: Implementing Fade-in/Fade-out Transition Effects for Images Using ContentTransition

This example demonstrates how to use the [contentTransition](#contenttransition21) attribute to implement the fade-in/fade-out effect for smooth image transitions when the image source is switched on a click. This attribute is supported since API version 21.



```TypeScript
@Entry
@Component
struct ImageExample {
  // Replace $r('app.media.icon') with the image resource file you use.
  @State imageResource: Resource = $r('app.media.icon');

  build() {
    Row() {
      Column() {
        Image(this.imageResource)
          .width(200)
          .height(200)
          // Enable the fade-in/fade-out transition effect.
          .contentTransition(ContentTransitionEffect.OPACITY)
          .onClick(() => {
            // Replace $r('app.media.cloud1') with the image resource file you use.
            this.imageResource = $r('app.media.cloud1')
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### Example 28: Using the alt Attribute to Set the Placeholder Images Displayed During Image Loading and When Image Loading Fails

This example demonstrates how to display specified images during image loading and when image loading fails by setting the [alt](#alt22) attribute.



```TypeScript
@Entry
@Component
struct ImageExample {
  build() {
      Column() {
      Text('Both placeholder and error attributes set')
      // Set an invalid URL to trigger the placeholder and error attributes of alt.
      Image("https://www.example.com/xxx.png")
      // Replace $r('app.media.startIcon') and $r('app.media.example') with the image resource file you use.
        .alt({ placeholder: $r('app.media.startIcon'), error: $r('app.media.example') })
        .width(100)
        .height(100)
        .margin(20)
      Text('Only placeholder attribute set')
      Image("https://www.example.com/xxx.png")
        .alt({ placeholder: $r('app.media.startIcon')})
        .width(100)
        .height(100)
        .margin(20)
      Text('Only error attribute set')
      Image("https://www.example.com/xxx.png")
        .alt({error: $r('app.media.example')})
        .width(100)
        .height(100)
        .margin(20)
      }
    .width('100%')
    .height('100%')
  }
}
```

### Example 29 Listening to Online Image Loading Exceptions Using onError

This example demonstrates how to obtain detailed download information ([ImageError](arkts-arkui-image-comp-imageerror-i.md)) when an online image fails to load via the [onError](#onerror9) callback. When image loading fails, you can obtain detailed online image download information through the downloadInfo attribute in ImageError, including download resource information, network request information, and performance statistics. This helps quickly identify the cause of network exceptions or resource errors.

The downloadInfo attribute is added to ImageError since API version 23.

```TypeScript
@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Image('https://www.example.com/xxx.png') // Enter a specific online image URL.
        .height(100)
        .width(100)
        .onError((e)=>{
          console.error(`DownloadErrorInfo: ${JSON.stringify(e?.downloadInfo)}`)
        })
    }
    .height('100%')
    .width('100%')
  }
}
```
