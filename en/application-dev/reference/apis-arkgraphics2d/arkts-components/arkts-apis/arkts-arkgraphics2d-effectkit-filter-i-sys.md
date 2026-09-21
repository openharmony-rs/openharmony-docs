# Filter

```TypeScript
interface Filter
```

An image effect class used to add a specified effect to the effect chain through chained calls. It is suitable for scenarios such as image filter processing, visual effect enhancement, and image beautification. Before calling the methods of Filter, you need to create a Filter instance via createEffect. After adding effects, you need to call getEffectPixelMap to obtain the processed image.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Image.Core

## Modules to Import

```TypeScript
import { effectKit } from '@kit.ArkGraphics2D';
```

## ellipticalGradientBlur

```TypeScript
ellipticalGradientBlur(blurRadius: number, center: EllipticalMaskCenter,
      maskRadius: EllipticalMaskRadius, fractionStops: FractionStop[]): Filter
```

Adds the elliptical gradient blur effect to the filter linked list, and returns the head node of the linked list.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| blurRadius | number | Yes | Blur radius, in pixels. The blur effect is proportional to the configured value. A larger value indicates a more obvious effect. |
| center | [EllipticalMaskCenter](arkts-arkgraphics2d-effectkit-ellipticalmaskcenter-t-sys.md) | Yes | Set the center point of the ellipse. [0, 0] represents the top-left corner of the component, and floating-point numbers are allowed. Values exceeding the boundary will be automatically truncated during implementation. |
| maskRadius | [EllipticalMaskRadius](arkts-arkgraphics2d-effectkit-ellipticalmaskradius-t-sys.md) | Yes | Set the major axis and minor axis of the ellipse. A radius of 1 is equal to the height of the component. The value range is [0, 10], and floating-point numbers are allowed. Values exceeding the boundary will be automatically truncated during implementation. |
| fractionStops | FractionStop[] | Yes | Gradient blur position and intensity array. The array length ranges from 0 to 12. It has no effect if the length is 0 or greater than 12. Both position and intensity values are between 0 and 1. Position 0 corresponds to the ellipse center, and position 1 corresponds to the ellipse boundary. Intensity 0 means no blur, while intensity 1 equals the blur effect of the input blur radius. |

**Return value:**

| Type | Description |
| --- | --- |
| [Filter](arkts-arkgraphics2d-effectkit-filter-i.md) | Final image effect. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

```TypeScript
import { image } from '@kit.ImageKit';
import { effectKit } from '@kit.ArkGraphics2D';
import { common } from '@kit.AbilityKit';
// Pass in the read image data
function ImageEllipticalGradientBlur(imageBuffer: ArrayBuffer): Promise<image.PixelMap> {
  return new Promise((resolve, reject) => {
    let imageSource = image.createImageSource(imageBuffer);
    let blurRadius:number = 25;
    let fractionStops:FractionStop[] = [[0, 0.2], [0.5, 0.7]];
    let maskRadius:effectKit.EllipticalMaskRadius = [1, 1];
    let center:effectKit.EllipticalMaskCenter = [0.5, 0.5];
    imageSource.createPixelMap().then(async (pixelMap: image.PixelMap) => {
      let headFilter = effectKit.createEffect(pixelMap);
      if (headFilter != null) {
        // Add an effect identifier to the image
        headFilter.ellipticalGradientBlur(blurRadius, center, maskRadius, fractionStops);
        // Process the image according to the added effect identifier and return the processed image data
        headFilter.getEffectPixelMap(false).then(imageData => {
          resolve(imageData);
        });
      }
    });
  });
}

@Entry
@Component
struct Index {
  @State imagePixelMap: image.PixelMap | null = null;
  private imageBuffer: ArrayBuffer | undefined = undefined;
  // Read the image file from the rawfile folder. You can also change the reading method as needed, as long as the final image data is in ArrayBuffer format.
  async getFileBuffer(): Promise<ArrayBuffer | undefined> {
    try {
      const context: Context = this.getUIContext().getHostContext() as common.UIAbilityContext;
      const fileData: Uint8Array = await context.resourceManager.getRawFileContent('image.png');
      const buffer: ArrayBuffer = fileData.buffer.slice(0);
      return buffer;
    } catch (err) {
      return undefined;
    }
  }

  async aboutToAppear(): Promise<void> {
    this.imageBuffer = await this.getFileBuffer();
    if (this.imageBuffer == undefined) {
      return;
    }
    // Image processing is an asynchronous operation. You can add await for synchronization as needed, depending on whether you need to obtain the processed image data before proceeding to the next step.
    this.imagePixelMap = await ImageEllipticalGradientBlur(this.imageBuffer);
  }

  build() {
    Column() {
      Image(this.imagePixelMap)
        .width(304)
        .height(305)
    }
    .height('100%')
    .width('100%')
  }
}
```
