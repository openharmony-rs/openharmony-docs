# ImageSpan

As a child of the [Text](arkts-arkui-text-comp.md#text) and [ContainerSpan](arkts-arkui-containerspan-comp-attribute.md#containerspanattribute) components, the **ImageSpan** component is used to display inline images.

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
| value | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) &#124; [PixelMap](arkts-arkui-common-comp-pixelmap-t.md) | Yes | Image source. Both local and network images are supported.<br>When using an image referenced using a relative path, for example, **ImageSpan("common/test.jpg")**, the **ImageSpan** component cannot be called across bundles or modules. Therefore, you are advised to use **$r** to reference image resources that need to be used globally.<br>- The supported formats include PNG, JPG, BMP, SVG, GIF, and HEIF.<br>- Base64 strings are supported. The value format is data:image/[png&#124;jpeg&#124;bmp&#124;webp&#124;heif];base64, [base64 data], where *[base64 data]* is a Base64 string.<br>- Character string prefixed with file://data/ storage, which is used to read image resources in the file folder in the application installation directory. Ensure that the application has the read permission to the files in the specified path. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [ImageLoadResult](arkts-arkui-imagespan-comp-imageloadresult-i.md) | Describes the object returned after the callback is triggered when an image is successfully loaded or decoded. |

### Types

| Name | Description |
| --- | --- |
| [ImageCompleteCallback](arkts-arkui-imagespan-comp-imagecompletecallback-t.md) | Defines the callback triggered when the image is successfully loaded or decoded. |

## Examples

### Example 1: Setting the Alignment Mode

This example demonstrates the alignment and scaling effects of the ImageSpan component using the [verticalAlign](#verticalalign) and [objectFit](#objectfit) attributes, available since API version 10.



```TypeScript
// xxx.ets
@Entry
@Component
struct SpanExample {
  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Text() {
        Span('This is the Span and ImageSpan component').fontSize(25).textCase(TextCase.Normal)
          .decoration({ type: TextDecorationType.None, color: Color.Pink })
      }.width('100%').textAlign(TextAlign.Center)

      Text() {
        // Replace $r('app.media.app_icon') with the image resource file you use.
        ImageSpan($r('app.media.app_icon'))
          .width('200px')
          .height('200px')
          .objectFit(ImageFit.Fill)
          .verticalAlign(ImageSpanAlignment.CENTER)
        Span('I am LineThrough-span')
          .decoration({ type: TextDecorationType.LineThrough, color: Color.Red }).fontSize(25)
        ImageSpan($r('app.media.app_icon'))
          .width('50px')
          .height('50px')
          .verticalAlign(ImageSpanAlignment.TOP)
        Span('I am Underline-span')
          .decoration({ type: TextDecorationType.Underline, color: Color.Red }).fontSize(25)
        ImageSpan($r('app.media.app_icon'))
          .size({ width: '100px', height: '100px' })
          .verticalAlign(ImageSpanAlignment.BASELINE)
        Span('I am Underline-span')
          .decoration({ type: TextDecorationType.Underline, color: Color.Red }).fontSize(25)
        ImageSpan($r('app.media.app_icon'))
          .width('70px')
          .height('70px')
          .verticalAlign(ImageSpanAlignment.BOTTOM)
        Span('I am Underline-span')
          .decoration({ type: TextDecorationType.Underline, color: Color.Red }).fontSize(50)
      }
      .width('100%')
      .textIndent(50)
    }.width('100%').height('100%').padding({ left: 0, right: 0, top: 0 })
  }
}
```

### Example 2: Setting the Background Style

This example demonstrates how to set the background style for text using the [textBackgroundStyle](ts-basic-components-span.md#textbackgroundstyle11) attribute, available since API version 11.



```TypeScript
// xxx.ets
@Component
@Entry
struct Index {
  build() {
    Row() {
      Column() {
        Text() {
          // Replace $r('app.media.sky') with the image resource file you use.
          ImageSpan($r('app.media.sky'))
            .width('60vp')
            .height('60vp')
            .verticalAlign(ImageSpanAlignment.CENTER)
            .borderRadius(20)
            .textBackgroundStyle({ color: '#7F007DFF', radius: '5vp' })
        }
      }.width('100%')
    }.height('100%')
  }
}
```

### Example 3: Adding Events to an Image

This example demonstrates how to add load success and load error events to the ImageSpan component using [onComplete](#oncomplete12) and [onError](#onerror12), available since API version 12.

```TypeScript
// xxx.ets
@Entry
@Component
struct Index {
  // Replace $r('app.media.app_icon') with the image resource file you use.
  @State src: ResourceStr = $r('app.media.app_icon');

  build() {
    Column() {
      Text() {
        ImageSpan(this.src)
          .width(100).height(100)
          .onError((err) => {
            console.error(`Failed to load image. Code: ${err.error?.code}, message: ${err.message}`);
          })
          .onComplete((event) => {
            console.info('onComplete: ' + event.loadingStatus);
          })
      }
    }.width('100%').height('100%')
  }
}
```

### Example 4: Setting the Color Filter

This example demonstrates the effect of setting a color filter for the ImageSpan component using the [colorFilter](#colorfilter14) attribute, available since API version 14.



```TypeScript
// xxx.ets
import { drawing } from '@kit.ArkGraphics2D';

@Entry
@Component
struct SpanExample {
  private colorFilterMatrix: number[] = [0.239, 0, 0, 0, 0, 0, 0.616, 0, 0, 0, 0, 0, 0.706, 0, 0, 0, 0, 0, 1, 0];
  @State drawingColorFilterFirst: ColorFilter | undefined = new ColorFilter(this.colorFilterMatrix);

  build() {
    Row() {
      Column({ space: 10 }) {
        // Create a ColorFilter object to set a color filter for the image.
        Text() {
          // Replace $r('app.media.sky') with the image resource file you use.
          ImageSpan($r('app.media.sky'))
            .width('60vp')
            .height('60vp')
            .colorFilter(this.drawingColorFilterFirst)
        }

        // Set a color filter for the image through drawing.ColorFilter.
        Text() {
          // Replace $r('app.media.sky') with the image resource file you use.
          ImageSpan($r('app.media.sky'))
            .width('60vp')
            .height('60vp')
            .colorFilter(drawing.ColorFilter.createBlendModeColorFilter({
              alpha: 255,
              red: 112,
              green: 112,
              blue: 112
            }, drawing.BlendMode.SRC))
        }
      }.width('100%')
    }.height('100%')
  }
}
```

### Example 5: Setting a Placeholder Image

This example demonstrates how to use the [alt](#alt12) attribute to display a placeholder image in the ImageSpan component while loading a network image, available since API version 12.

When using a network image, you need to apply for the ohos.permission.INTERNET permission. For details about how to apply for the permission, see [Declaring Permissions](../../../security/AccessToken/declare-permissions.md).



```TypeScript
// xxx.ets
import { http } from '@kit.NetworkKit';
import { image } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct SpanExample {
  @State imageAlt: PixelMap | undefined = undefined;

  httpRequest() {
    // Enter an image URL.
    http.createHttp().request('https://www.example.com/xxx.png', (error: BusinessError, data: http.HttpResponse) => {
      if (error) {
        console.error(`http request failed with. Code: ${error.code}, message: ${error.message}`);
      } else {
        console.info('http request success');
        let imageData: ArrayBuffer = data.result as ArrayBuffer;
        let imageSource: image.ImageSource = image.createImageSource(imageData);

        class ImageSize {
          height: number = 100;
          width: number = 100;
        }

        let option: Record<string, number | boolean | ImageSize> = {
          'alphaType': 0, // Alpha type.
          'editable': false, // Whether the image is editable.
          'pixelFormat': 3, // Pixel format.
          'scaleMode': 1, // Scale mode.
          'size': { height: 100, width: 100 }
        };
        // Create a PixelMap object through ImageSource.
        imageSource.createPixelMap(option).then((pixelMap: PixelMap) => {
          console.info('image createPixelMap success');
          this.imageAlt = pixelMap;
          imageSource.release();
        }).catch(() => {
          imageSource.release();
        })
      }
    })
  }

  build() {
    Column() {
      Button('Obtain Network Image')
        .onClick(() => {
          this.httpRequest();
        })

      Text() {
        // Enter an image URL to load the image.
        ImageSpan('https://www.example.com/xxx.png')
          .alt(this.imageAlt)
          .width(300)
          .height(300)
      }

    }.width('100%').height(250).padding({ left: 35, right: 35, top: 35 })
  }
}
```

### Example 6: Displaying an SVG Image Using the supportSvg2 Property

This example shows how to make the [SVG usability improvement capability](ts-image-svg2-capabilities.md#improved-svg-usability) of the [SVG tag parsing enhancement feature](ts-image-svg2-capabilities.md) take effect by configuring the [supportSvg2](#supportsvg222) attribute, available since API version 22.



```TypeScript
import { drawing } from '@kit.ArkGraphics2D';
@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Text('Styled string with supportSvg2: false')
        // Replace $r('app.media.ice') with the image resource file you use.
        Text() {
          ImageSpan($r('app.media.ice'))
            .width(50)
            .height(50)
            .colorFilter(drawing.ColorFilter.createBlendModeColorFilter(
              drawing.Tool.makeColorFromResourceColor(Color.Blue), drawing.BlendMode.SRC_IN))
        }
        Text('Styled string with supportSvg2: true')
        // Replace $r('app.media.ice') with the image resource file you use.
        Text() {
          ImageSpan($r('app.media.ice'))
            .width(50)
            .height(50)
            .supportSvg2(true)
            .colorFilter(drawing.ColorFilter.createBlendModeColorFilter(
              drawing.Tool.makeColorFromResourceColor(Color.Blue), drawing.BlendMode.SRC_IN))
        }
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### Example 7: Setting Image Stretching

This example shows how to stretch the ImageSpan image in different directions using the slice option of the [resizable](#resizable) attribute.

Since API version 26.1.0, the resizable attribute is added.

```TypeScript
@Entry
@Component
struct ImageSpanResizablePage {
  build() {
    Column({ space: 20 }) {
      Text('ImageSpan resizable Demo')
        .fontSize(28)
        .fontWeight(FontWeight.Bold)

      Text('Use Text + ImageSpan and set the slice attribute of resizable to implement nine-grid stretching:')
        .fontSize(28)
        .fontColor('#666666')
        .width('90%')

      Text() {
        Span('Original image\n')
          .fontSize(28)
        ImageSpan($r('app.media.landscape'))
          .width(200)
          .height(200)
        Span('\nAfter setting Resizable\n')
          .fontSize(28)
        ImageSpan($r('app.media.landscape'))
          .width(260)
          .height(260)
          .resizable({
            slice: {
              left: '200px',
              top: '200px',
              right: '20px',
              bottom: '20px'
            }
          })
      }
      .width('90%')
      .textAlign(TextAlign.Center)
      .margin({ top: 10 })
    }
    .width('100%')
    .height('100%')
    .padding(20)
    .alignItems(HorizontalAlign.Center)
  }
}
```
