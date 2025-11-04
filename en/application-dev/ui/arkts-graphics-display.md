# Image Display (Image)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liyujie43-->
<!--Designer: @weixin_52725220-->
<!--Tester: @xiong0104-->
<!--Adviser: @HelloCrease-->

More often than not, you may need to display images in your application, for example, icons in buttons, online images, and local images. This is where the **Image** component comes in handy. The **Image** component supports a wide range of image formats, including PNG, JPG, BMP, SVG, GIF, and HEIF, but does not support APNG and SVGA. For details, see [Image](../reference/apis-arkui/arkui-ts/ts-basic-components-image.md).


To use the **Image** component, call the following API:

```ts
Image(src: PixelMap | ResourceStr | DrawableDescriptor)
```


This API obtains a local or online image from the data source specified by **src**. For details about how to load the data source, see [Loading Image Resources](#loading-image-resources).

For details about how to resolve white block issues during image loading, see [Solution to White Image Blocks](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-image-white-lump-solution). For details about how to address slow image loading, see [Optimizing Preset Image Loading](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-texture-compression-improve-performance).


## Loading Image Resources

Images can be categorized into three types: archived files, pixel maps, and drawable descriptors.


### Archived Data Sources

Archived data sources can be classified into local resources, network resources, **Resource** objects, media library assets, and Base64 resources.

- Local resources

  To load local images, create an **ets** directory and place image files within this directory structure.

  In the **Image** component, set **src** to the local image path, with the **ets** directory as the root directory. Note that images cannot be loaded across bundles or modules.

  ```ts
  Image('images/view.jpg')
  .width(200)
  ```

  To avoid application instability, do not modify or replace local images while they are being loaded. To update an image file, first delete the existing file before creating a new one with the same name.

- Network resources

  To load network images, first declare the ohos.permission.INTERNET permission. For details, see [Declaring Permissions](../security/AccessToken/declare-permissions.md). Then, in the **Image** component, set **src** to the URL of the network image.

  Currently, the **Image** component supports only simple network images.

  If a network image has been loaded before, the **Image** component can obtain it from the cache, instead of having to request it from the Internet again. For details about the image cache, see [setImageCacheCount](../reference/apis-arkui/js-apis-system-app.md#setimagecachecount7), [setImageRawDataCacheSize](../reference/apis-arkui/js-apis-system-app.md#setimagerawdatacachesize7), and [setImageFileCacheSize](../reference/apis-arkui/js-apis-system-app.md#setimagefilecachesize7). Note that these cache APIs have limited flexibility and are not recommended for future development. For complex scenarios, you are advised to use [ImageKnife](https://gitcode.com/openharmony-tpc/ImageKnife) instead.

  Network images must comply with the RFC 9113 standard. Otherwise, the loading will fail. For images larger than 10 MB or bulk downloads, use the [HTTP](../network/http-request.md) API for pre-downloading to improve loading performance and simplify data management.

  The **Image** component employs a decoupled architecture where download and cache operations are handled by the unified [download and cache module](../reference/apis-basic-services-kit/js-apis-request-cacheDownload.md). This module provides pre-download capabilities, allowing images to be fetched before the **Image** component is created. Once the component is created, it requests the image data from the download and cache module. This way, the display performance of the **Image** component is improved. All network cache files are stored in the application's **cache** directory.

  ```ts
  Image('https://www.example.com/example.JPG') // Replace the URL with the actual URL.
  ```

- **Resource** objects

  **Resource** objects can be used to import images across bundles and modules. All images in the **resources** folder can be read and converted to the **Resource** objects through **$r**.

  **Figure 1** resources 

  ![image-resource](figures/image-resource.jpg)

  API:

  ```
  Image($r('app.media.icon'))
  ```

  You can also place the images in the **rawfile** folder.

  **Figure 2** rawfile folder 

  ![image-rawfile](figures/image-rawfile.jpg)

  API:

  ```
  Image($rawfile('example1.png'))
  ```

- Media library **file://data/storage**

  To load images from the [picker](../reference/apis-core-file-kit/js-apis-file-picker.md), use a path string that starts with **file://**.

  1. Call the API to obtain the image URL in the media library.

      ```ts
      import { photoAccessHelper } from '@kit.MediaLibraryKit';
      import { BusinessError } from '@kit.BasicServicesKit';

      @Entry
      @Component
      struct Index {
        @State imgDatas: string[] = [];
        // Obtain the image URL set.
        getAllImg() {
          try {
            let photoSelectOptions:photoAccessHelper.PhotoSelectOptions = new photoAccessHelper.PhotoSelectOptions();
            photoSelectOptions.MIMEType = photoAccessHelper.PhotoViewMIMETypes.IMAGE_TYPE;
            photoSelectOptions.maxSelectNumber = 5;
            let photoPicker:photoAccessHelper.PhotoViewPicker = new photoAccessHelper.PhotoViewPicker();
            photoPicker.select(photoSelectOptions).then((PhotoSelectResult:photoAccessHelper.PhotoSelectResult) => {
              this.imgDatas = PhotoSelectResult.photoUris;
              console.info('PhotoViewPicker.select successfully, PhotoSelectResult uri: ' + JSON.stringify(PhotoSelectResult));
            }).catch((err:Error) => {
              let message = (err as BusinessError).message;
              let code = (err as BusinessError).code;
              console.error(`PhotoViewPicker.select failed with. Code: ${code}, message: ${message}`);
            });
          } catch (err) {
            let message = (err as BusinessError).message;
            let code = (err as BusinessError).code;
            console.error(`PhotoViewPicker failed with. Code: ${code}, message: ${message}`);    }
        }

        // Call the preceding function in aboutToAppear to obtain the image URL set and store the URLs in imgDatas.
        async aboutToAppear() {
          this.getAllImg();
        }
        // Use the URL of imgDatas to load the image.
        build() {
          Column() {
            Grid() {
              ForEach(this.imgDatas, (item:string) => {
                GridItem() {
                  Image(item)
                    .width(200)
                }
              }, (item:string):string => JSON.stringify(item))
            }
          }.width('100%').height('100%')
        }
      }
      ```

  2. Check the format of the URL obtained from the media library:

      ```ts
      Image('file://media/Photos/5')
      .width(200)
      ```


- Base64

  As shown above, the URL format is data:image/[png|jpeg|bmp|webp|heif];base64,[base64 data], in which **[base64 data]** indicates Base64 string data.

  Base64 strings are widely used on web pages for storing pixel data of images.


### Pixel Map

A pixel map is a pixel image obtained after image decoding. For details, see [Introduction to Image Kit](../media/image/image-overview.md). In the following example, the data returned by the loaded online image is decoded into a pixel map, which is then displayed on the **Image** component.


   ```ts
   import { http } from '@kit.NetworkKit';
   import { image } from '@kit.ImageKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   
   @Entry
   @Component
   struct HttpExample {
     outData: http.HttpResponse | undefined = undefined;
     code: http.ResponseCode | number | undefined = undefined;
     @State image: PixelMap | undefined = undefined; // Create a PixelMap state variable.
   
     aboutToAppear(): void {
       http.createHttp().request('https://www.example.com/xxx.png', // Specify the network image URL.
         (error: BusinessError, data: http.HttpResponse) => {
           if (error) {
             console.error(`hello http request failed with. Code: ${error.code}, message: ${error.message}`);
             return;
           }
           this.outData = data;
           // Convert network response data to PixelMap format.
           if (http.ResponseCode.OK === this.outData.responseCode) {
             let imageData: ArrayBuffer = this.outData.result as ArrayBuffer;
             let imageSource: image.ImageSource = image.createImageSource(imageData);
             let options: image.DecodingOptions = {
               'desiredPixelFormat': image.PixelMapFormat.RGBA_8888,
             };
             imageSource.createPixelMap(options).then((pixelMap: PixelMap) => {
               this.image = pixelMap;
             });
           }
         })
     }
   
     build() {
       Column() {
         // Display the image.
         Image(this.image)
           .height(100)
           .width(100)
       }
     }
   }
   ```

### DrawableDescriptor

DrawableDescriptor is an advanced image abstraction mechanism in ArkUI that encapsulates image resources into programmable objects. It enables dynamic composition and runtime control capabilities beyond traditional Image components, supporting advanced features such as layered overlays (such as badge icons), dynamic attribute adjustments (e.g., color filters), and complex animation sequences. This mechanism is particularly suitable for scenarios requiring flexible image manipulation or complex visual interactions. For complete API details, see [DrawableDescriptor](../../application-dev/reference/apis-arkui/js-apis-arkui-drawableDescriptor.md).

The following example demonstrates image display and animation implementation using DrawableDescriptor:

```ts
import {
  DrawableDescriptor,
  PixelMapDrawableDescriptor,
  LayeredDrawableDescriptor,
  AnimatedDrawableDescriptor,
  AnimationOptions
} from '@kit.ArkUI';
import { image } from '@kit.ImageKit';

@Entry
@Component
struct Index {
  // Declare a DrawableDescriptor object.
  @State pixmapDesc: DrawableDescriptor | null = null;
  @State pixelMapDesc: PixelMapDrawableDescriptor | null = null;
  @State layeredDesc: LayeredDrawableDescriptor | null = null;
  @State animatedDesc: AnimatedDrawableDescriptor | null = null;
  // Configure animation parameters.
  private animationOptions: AnimationOptions = {
    duration: 3000,
    iterations: -1
  };

  async aboutToAppear() {
    const resManager = this.getUIContext().getHostContext()?.resourceManager;
    if (!resManager) {
      return;
    }
    // Create standard DrawableDescriptor object.
    let pixmapDescResult = resManager.getDrawableDescriptor($r('app.media.landscape').id);
    if (pixmapDescResult) {
      this.pixmapDesc = pixmapDescResult as DrawableDescriptor;
    }
    // Create a PixelMapDrawableDescriptor object.
    const pixelMap = await this.getPixmapFromMedia($r('app.media.landscape'));
    this.pixelMapDesc = new PixelMapDrawableDescriptor(pixelMap);
    // Create a layered icon.
    const foreground = await this.getDrawableDescriptor($r('app.media.foreground'));
    const background = await this.getDrawableDescriptor($r('app.media.landscape'));
    this.layeredDesc = new LayeredDrawableDescriptor(foreground, background);
    // Create an animated image sequence (requires loading of multiple images).
    const frame1 = await this.getPixmapFromMedia($r('app.media.sky'));
    const frame2 = await this.getPixmapFromMedia($r('app.media.landscape'));
    const frame3 = await this.getPixmapFromMedia($r('app.media.clouds'));
    if (frame1 && frame2 && frame3) {
      this.animatedDesc = new AnimatedDrawableDescriptor([frame1, frame2, frame3], this.animationOptions);
    }
  }

  // Helper method: Obtain the pixel map from the resource.
  private async getPixmapFromMedia(resource: Resource): Promise<image.PixelMap | undefined> {
    const unit8Array = await this.getUIContext().getHostContext()?.resourceManager.getMediaContent(resource.id);
    if (!unit8Array) {
      return undefined;
    }
    const imageSource = image.createImageSource(unit8Array.buffer.slice(0, unit8Array.buffer.byteLength));
    const pixelMap = await imageSource.createPixelMap({
      desiredPixelFormat: image.PixelMapFormat.RGBA_8888
    });
    await imageSource.release();
    return pixelMap;
  }

  // Helper method: Obtain a DrawableDescriptor object.
  private async getDrawableDescriptor(resource: Resource): Promise<DrawableDescriptor | undefined> {
    const resManager = this.getUIContext().getHostContext()?.resourceManager;
    if (!resManager) {
      return undefined;
    }
    return (resManager.getDrawableDescriptor(resource.id)) as DrawableDescriptor;
  }

  build() {
    RelativeContainer() {
      Column() {

        // Display a standard image.
        Image(this.pixmapDesc)
          .width(100)
          .height(100)
          .border({ width: 1, color: Color.Black })
        // Display a PixelMap image.
        Image(this.pixelMapDesc)
          .width(100)
          .height(100)
          .border({ width: 1, color: Color.Red })
        // Display a layered icon.
        if (this.layeredDesc) {
          Image(this.layeredDesc)
            .width(100)
            .height(100)
            .border({ width: 1, color: Color.Blue })
        }
        // Display an animated image.
        if (this.animatedDesc) {
          Image(this.animatedDesc)
            .width(200)
            .height(200)
            .margin({ top: 20 })
        }
      }
    }
    .height('100%')
    .width('100%')
    .margin(50)
  }
}
```

![drawableDescriptor](figures/drawableDescriptor.gif)


## Displaying Vector Images

The Image component supports Scalable Vector Graphics (SVG). For SVG element reference, see [SVG Tags](../../application-dev/reference/apis-arkui/arkui-ts/ts-basic-svg.md).

To display an SVG image without intrinsic dimensions, you must set the width and height for the **Image** component. SVG images cannot reference local SVG or GIF images through **\<image>** tags.

You can use the **fillColor** attribute to change the fill color of an SVG image.


```ts
Image($r('app.media.cloud'))
  .width(50)
  .fillColor(Color.Blue) 
```

  **Figure 3** Original image 

![screenshot_20230223_141141](figures/screenshot_20230223_141141.png)

  **Figure 4** SVG image after the fill color is set 

![screenshot_20230223_141404](figures/screenshot_20230223_141404.png)

### Using an SVG File with a Local Bitmap Reference

When using the **Image** component to load an SVG file that references any local bitmap, make sure the SVG file path is a relative path to the **ets** project root directory, and the local bitmap referenced in the SVG file is located at the same level as the SVG file and specified using a relative path.

Example for setting the SVG image path in the **Image** component:

```ts
Image("images/icon.svg")
  .width(50)
  .height(50)
```
In your SVG file, use the **xlink:href** attribute within the **\<image>** tag to reference the local bitmap. Ensure the bitmap path is relative to the SVG file location.

```
<svg width="200" height="200">
  <image width="200" height="200" xlink:href="sky.png"></image>
</svg>
```
The following figure shows an example of the project structure.

![image path](figures/imagePath.png)

## Setting Attributes

Setting attributes for the **Image** component can spruce up the image with custom effects. The following are usage examples of common attributes. For details about all attributes, see [Image](../reference/apis-arkui/arkui-ts/ts-basic-components-image.md).

### Setting the Image Scale Mode

You can use the **objectFit** attribute to scale an image to fit it into a container whose height and width are determined.


```ts
@Entry
@Component
struct MyComponent {
  scroller: Scroller = new Scroller();

  build() {
    Scroll(this.scroller) {
      Column() {
        Row() {
          Image($r('app.media.img_2'))
            .width(200)
            .height(150)
            .border({ width: 1 })
              // The image is scaled with its aspect ratio retained for the content to be completely displayed within the display boundaries.
            .objectFit(ImageFit.Contain)
            .margin(15)
            .overlay('Contain', { align: Alignment.Bottom, offset: { x: 0, y: 20 } })
          Image($r('app.media.ic_img_2'))
            .width(200)
            .height(150)
            .border({ width: 1 })
              // The image is scaled with its aspect ratio retained for both sides to be greater than or equal to the display boundaries.
            .objectFit(ImageFit.Cover)
            .margin(15)
            .overlay('Cover', { align: Alignment.Bottom, offset: { x: 0, y: 20 } })
          Image($r('app.media.img_2'))
            .width(200)
            .height(150)
            .border({ width: 1 })
              // The image is scaled automatically to fit the display area.
            .objectFit(ImageFit.Auto)
            .margin(15)
            .overlay('Auto', { align: Alignment.Bottom, offset: { x: 0, y: 20 } })
        }

        Row() {
          Image($r('app.media.img_2'))
            .width(200)
            .height(150)
            .border({ width: 1 })
              // The image is scaled to fill the display area, and its aspect ratio is not retained.
            .objectFit(ImageFit.Fill)
            .margin(15)
            .overlay('Fill', { align: Alignment.Bottom, offset: { x: 0, y: 20 } })
          Image($r('app.media.img_2'))
            .width(200)
            .height(150)
            .border({ width: 1 })
              // The image content is displayed with its aspect ratio retained. The size is smaller than or equal to the original size.
            .objectFit(ImageFit.ScaleDown)
            .margin(15)
            .overlay('ScaleDown', { align: Alignment.Bottom, offset: { x: 0, y: 20 } })
          Image($r('app.media.img_2'))
            .width(200)
            .height(150)
            .border({ width: 1 })
              // The original size is retained.
            .objectFit(ImageFit.None)
            .margin(15)
            .overlay('None', { align: Alignment.Bottom, offset: { x: 0, y: 20 } })
        }
      }
    }
  }
}
```

![en-us_image_0000001622804833](figures/en-us_image_0000001622804833.png)


### Using Image Interpolation

An image of low resolution may suffer quality loss with aliasing when scaled up. If this is the case, you can use the **interpolation** attribute to conduct image interpolation and improve image quality.


```ts
@Entry
@Component
struct Index {
  build() {
    Column() {
      Row() {
        Image($r('app.media.grass'))
          .width('40%')
          .interpolation(ImageInterpolation.None)
          .borderWidth(1)
          .overlay("Interpolation.None", { align: Alignment.Bottom, offset: { x: 0, y: 20 } })
          .margin(10)
        Image($r('app.media.grass'))
          .width('40%')
          .interpolation(ImageInterpolation.Low)
          .borderWidth(1)
          .overlay("Interpolation.Low", { align: Alignment.Bottom, offset: { x: 0, y: 20 } })
          .margin(10)
      }.width('100%')
      .justifyContent(FlexAlign.Center)

      Row() {
        Image($r('app.media.grass'))
          .width('40%')
          .interpolation(ImageInterpolation.Medium)
          .borderWidth(1)
          .overlay("Interpolation.Medium", { align: Alignment.Bottom, offset: { x: 0, y: 20 } })
          .margin(10)
        Image($r('app.media.grass'))
          .width('40%')
          .interpolation(ImageInterpolation.High)
          .borderWidth(1)
          .overlay("Interpolation.High", { align: Alignment.Bottom, offset: { x: 0, y: 20 } })
          .margin(10)
      }.width('100%')
      .justifyContent(FlexAlign.Center)
    }
    .height('100%')
  }
}
```

![en-us_image_0000001643127365](figures/en-us_image_0000001643127365.png)


### Setting Image Repeat Pattern

You can use the **objectRepeat** attribute to set the repeat pattern of an image. For details, see [ImageRepeat](../reference/apis-arkui/arkui-ts/ts-appendix-enums.md#imagerepeat).


```ts
@Entry
@Component
struct MyComponent {
  build() {
    Column({ space: 10 }) {
      Row({ space: 5 }) {
        Image($r('app.media.ic_public_favor_filled_1'))
          .width(110)
          .height(115)
          .border({ width: 1 })
          .objectRepeat(ImageRepeat.XY)
          .objectFit(ImageFit.ScaleDown)
          // Repeat the image along both the horizontal and vertical axes.
          .overlay('ImageRepeat.XY', { align: Alignment.Bottom, offset: { x: 0, y: 20 } })
        Image($r('app.media.ic_public_favor_filled_1'))
          .width(110)
          .height(115)
          .border({ width: 1 })
          .objectRepeat(ImageRepeat.Y)
          .objectFit(ImageFit.ScaleDown)
          // Repeat the image only along the vertical axis.
          .overlay('ImageRepeat.Y', { align: Alignment.Bottom, offset: { x: 0, y: 20 } })
        Image($r('app.media.ic_public_favor_filled_1'))
          .width(110)
          .height(115)
          .border({ width: 1 })
          .objectRepeat(ImageRepeat.X)
          .objectFit(ImageFit.ScaleDown)
          // Repeat the image only along the horizontal axis.
          .overlay('ImageRepeat.X', { align: Alignment.Bottom, offset: { x: 0, y: 20 } })
      }
    }.height(150).width('100%').padding(8)
  }
}
```

![en-us_image_0000001593444112](figures/en-us_image_0000001593444112.png)


### Setting Image Rendering Mode

You can use the **renderMode** attribute to set the rendering mode of an image.


```ts
@Entry
@Component
struct MyComponent {
  build() {
    Column({ space: 10 }) {
      Row({ space: 50 }) {
        Image($r('app.media.example'))
          // Set the rendering mode to Original.
          .renderMode(ImageRenderMode.Original)
          .width(100)
          .height(100)
          .border({ width: 1 })
            // overlay is a universal attribute, which is used to add overlay text on the component.
          .overlay('Original', { align: Alignment.Bottom, offset: { x: 0, y: 20 } })
        Image($r('app.media.example'))
          // Set the rendering mode to Template.
          .renderMode(ImageRenderMode.Template)
          .width(100)
          .height(100)
          .border({ width: 1 })
          .overlay('Template', { align: Alignment.Bottom, offset: { x: 0, y: 20 } })
      }
    }.height(150).width('100%').padding({ top: 20,right: 10 })
  }
}
```

![en-us_image_0000001593293100](figures/en-us_image_0000001593293100.png)


### Setting Image Decoding Size

You can use the **sourceSize** attribute to set the image decoding size. By setting the decoding size to lower than the source size, you can decrease the image resolution.

In this example, the source image size is 1280 x 960, and the decoding sizes are 40 x 40 and 90 x 90.


```ts
@Entry
@Component
struct Index {
  build() {
    Column() {
      Row({ space: 50 }) {
        Image($r('app.media.example'))
          .sourceSize({
            width: 40,
            height: 40
          })
          .objectFit(ImageFit.ScaleDown)
          .aspectRatio(1)
          .width('25%')
          .border({ width: 1 })
          .overlay('width:40 height:40', { align: Alignment.Bottom, offset: { x: 0, y: 40 } })
        Image($r('app.media.example'))
          .sourceSize({
            width: 90,
            height: 90
          })
          .objectFit(ImageFit.ScaleDown)
          .width('25%')
          .aspectRatio(1)
          .border({ width: 1 })
          .overlay('width:90 height:90', { align: Alignment.Bottom, offset: { x: 0, y: 40 } })
      }.height(150).width('100%').padding(20)
    }
  }
}
```

![en-us_image_0000001593769844](figures/en-us_image_0000001593769844.png)


### Adding a Filter to an Image

You can use the **colorFilter** attribute to add a filter to an image.


```ts
@Entry
@Component
struct Index {
  build() {
    Column() {
      Row() {
        Image($r('app.media.example'))
          .width('40%')
          .margin(10)
        Image($r('app.media.example'))
          .width('40%')
          .colorFilter(
            [1, 1, 0, 0, 0,
             0, 1, 0, 0, 0,
             0, 0, 1, 0, 0,
             0, 0, 0, 1, 0])
          .margin(10)
      }.width('100%')
      .justifyContent(FlexAlign.Center)
    }
  }
}
```

![en-us_image_0000001643171357](figures/en-us_image_0000001643171357.png)


### Synchronously Loading Images

Generally, the image loading process is performed asynchronously to avoid blocking the main thread and to streamline UI interaction. In certain cases, however, the image may flicker when refreshed. If this occurs, you can use the **syncLoad** attribute to load the image synchronously to avoid flickering. Avoid using this attribute if the image loading may take a long time. Otherwise, the page may fail to respond.


```ts
Image($r('app.media.icon'))
  .syncLoad(true)
```


## Adding Events

By binding the **onComplete** event to the **Image** component, you can obtain necessary information about the image after the image is successfully loaded. You can also bind the **onError** event to obtain error information when the image fails to be loaded.


```ts
@Entry
@Component
struct MyComponent {
  @State widthValue: number = 0;
  @State heightValue: number = 0;
  @State componentWidth: number = 0;
  @State componentHeight: number = 0;

  build() {
    Column() {
      Row() {
        Image($r('app.media.ic_img_2'))
          .width(200)
          .height(150)
          .margin(15)
          .onComplete(msg => {
            if(msg){
              this.widthValue = msg.width;
              this.heightValue = msg.height;
              this.componentWidth = msg.componentWidth;
              this.componentHeight = msg.componentHeight;
            }
          })
            // If the image fails to be obtained, print the result.
          .onError(() => {
            console.info('load image fail')
          })
          .overlay('\nwidth: ' + String(this.widthValue) + ', height: ' + String(this.heightValue) + '\ncomponentWidth: ' + String(this.componentWidth) + '\ncomponentHeight: ' + String(this.componentHeight), {
            align: Alignment.Bottom,
            offset: { x: 0, y: 60 }
          })
      }
    }
  }
}
```

![en-us_image_0000001511740460](figures/en-us_image_0000001511740460.png)
