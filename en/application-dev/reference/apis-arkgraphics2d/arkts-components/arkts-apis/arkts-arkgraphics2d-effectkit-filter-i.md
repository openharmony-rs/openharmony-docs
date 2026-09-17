# Filter

An image effect class used to add a specified effect to the effect chain through chained calls. It is suitable for scenarios such as image filter processing, visual effect enhancement, and image beautification. Before calling the methods of Filter, you need to create a Filter instance via createEffect. After adding effects, you need to call getEffectPixelMap to obtain the processed image.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Image.Core

## Modules to Import

```TypeScript
import { effectKit } from '@kit.ArkGraphics2D';
```

## blur

```TypeScript
blur(radius: number): Filter
```

Adds the blur effect to the effect chain and returns the instance of the chain. The shader tile mode uses DECAL. To specify the tile mode, use the blur(radius: double, tileMode: TileMode) API. It is commonly used in scenarios such as background blurring, privacy information masking, frosted glass background effect, and pop-up window background blur.

> **NOTE:** 
> 
> This API provides the blur effect for static images. To provide the real-time blur effect for components, use dynamic blur.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| radius | number | Yes | Blur radius, in px. Value range: [0, +∞). A larger blur radius produces a more pronounced blur effect. Negative values produce no effect. |

**Return value:**

| Type | Description |
| --- | --- |
| [Filter](arkts-arkgraphics2d-effectkit-filter-i.md) | Returns the Filter instance with the added effects, for further adding effects or obtaining the processed image. |

**Examples**

```TypeScript
import { image } from '@kit.ImageKit';
import { effectKit } from '@kit.ArkGraphics2D';
import { common } from '@kit.AbilityKit';
// Pass the image data to be read.
function imageBlur(imageBuffer: ArrayBuffer): Promise<image.PixelMap> {
  return new Promise(async (resolve) => {
    // Create an image source.
    let imageSource = image.createImageSource(imageBuffer);
    await imageSource.createPixelMap().then(async (pixelMap: image.PixelMap) => {
      // Set the blur radius.
      let radius = 5;
      // Create a Filter instance.
      let headFilter = effectKit.createEffect(pixelMap);
      if (headFilter != null) {
        // Add a blur effect to the image.
        headFilter.blur(radius);
        // Process the image based on the added effect identifiers and return the processed image data.
        headFilter.getEffectPixelMap().then(imageData => {
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
  // Read the image file in the rawfile folder. You can also change the read mode as required to ensure that the image data in ArrayBuffer format is obtained.
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
    // Image processing is an asynchronous operation. You can perform the next step based on whether the processed image data needs to be obtained. Add await as required for synchronization.
    this.imagePixelMap = await imageBlur(this.imageBuffer);
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

```TypeScript
import { image } from '@kit.ImageKit';
import { effectKit } from '@kit.ArkGraphics2D';
import { common } from '@kit.AbilityKit';
// Pass the image data to be read.
function imageBlur(imageBuffer: ArrayBuffer): Promise<image.PixelMap> {
  return new Promise(async (resolve) => {
    // Create the image source.
    let imageSource = image.createImageSource(imageBuffer);
    await imageSource.createPixelMap().then(async (pixelMap: image.PixelMap) => {
      // Set the blur radius.
      let radius = 30;
      // Create a Filter instance.
      let headFilter = effectKit.createEffect(pixelMap);
      if (headFilter != null) {
        // Add a blur effect to the image and set the tile mode.
        headFilter.blur(radius, effectKit.TileMode.DECAL);
        // Process the image based on the added effect identifier and return the processed image data.
        headFilter.getEffectPixelMap().then(imageData => {
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
  // Read the image file in the rawfile folder. You can also change the read mode as required to ensure that the image data in ArrayBuffer format is obtained.
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
    // Image processing is an asynchronous operation. You can perform the next step based on whether the processed image data needs to be obtained. Add await as required for synchronization.
    this.imagePixelMap = await imageBlur(this.imageBuffer);
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

## blur

```TypeScript
blur(radius: number, tileMode: TileMode): Filter
```

Adds the blur effect to the effect chain and returns the instance of the chain. It supports selecting the shader effect tile mode. It is commonly used in scenarios such as background blurring, privacy information masking, frosted glass background effect, and pop-up window background blur.

> **NOTE:** 
> 
> This API provides the blur effect for static images. To provide the real-time blur effect for components, use dynamic blur.

**Since:** 14

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| radius | number | Yes | Blur radius, in px. Value range: [0, +∞). A larger blur radius produces a more pronounced blur effect. No effect is applied when a negative value is passed in. |
| tileMode | [TileMode](arkts-arkgraphics2d-effectkit-tilemode-e.md) | Yes | Shader tile mode, which affects the blur effect at the image edges. |

**Return value:**

| Type | Description |
| --- | --- |
| [Filter](arkts-arkgraphics2d-effectkit-filter-i.md) | Returns a Filter instance with the added effects, for continuing to add effects or obtaining the processed image. |

**Examples**

See [blur](#blur)

## brightness

```TypeScript
brightness(bright: number): Filter
```

Adds the brightness effect to the effect chain and returns the instance of the chain. This method achieves a brightness effect by adjusting the image brightness. It is commonly used in scenarios such as dark image brightening, image preview brightness enhancement, and night mode image adaptation.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bright | number | Yes | Brightness level. The value range is [0, 1]. The value 0 means the image remains unchanged, and 1 means the image brightness is increased to the maximum. If the value is out of range, it is automatically corrected to 0. |

**Return value:**

| Type | Description |
| --- | --- |
| [Filter](arkts-arkgraphics2d-effectkit-filter-i.md) | Returns the Filter instance with the added effects, for further adding effects or obtaining the processed image. |

**Examples**

```TypeScript
import { image } from '@kit.ImageKit';
import { effectKit } from '@kit.ArkGraphics2D';
import { common } from '@kit.AbilityKit';
// Pass the image data to be read.
function imageBrightness(imageBuffer: ArrayBuffer): Promise<image.PixelMap> {
  return new Promise(async (resolve) => {
    // Create the image source.
    let imageSource = image.createImageSource(imageBuffer);
    await imageSource.createPixelMap().then(async (pixelMap: image.PixelMap) => {
      // Set the brightness value.
      let bright = 0.5;
      // Create a Filter instance.
      let headFilter = effectKit.createEffect(pixelMap);
      if (headFilter != null) {
        // Add a highlight effect to the image.
        headFilter.brightness(bright);
        // Process the image based on the added effect identifier and return the processed image data.
        headFilter.getEffectPixelMap().then(imageData => {
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
  // Read the image file in the rawfile folder. You can also change the read mode as required to ensure that the image data in ArrayBuffer format is obtained.
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
    // Image processing is an asynchronous operation. You can perform the next step based on whether the processed image data needs to be obtained. Add await as required for synchronization.
    this.imagePixelMap = await imageBrightness(this.imageBuffer);
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

## getEffectPixelMap

```TypeScript
getEffectPixelMap(): Promise<image.PixelMap>
```

Obtains image.PixelMap of the source image to which the effect chain has been added. CPU rendering is used by default. This API uses a promise to return the result. To specify the rendering mode, use the getEffectPixelMap(useCpuRender: boolean) API. It is commonly used in scenarios where the processed image needs to be saved or displayed.

> **NOTE:** 
> 
> This method uses CPU rendering by default. The shader tile mode supports only DECAL, and other modes (CLAMP, REPEAT, MIRROR) are not supported. To use GPU rendering or learn about the impact of rendering modes on TileMode, see TileMode and getEffectPixelMap(useCpuRender: boolean).

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)&gt; | Promise used to return the image.PixelMap of the source image with the effect chain applied. |

**Examples**

```TypeScript
import { image } from '@kit.ImageKit';
import { effectKit } from '@kit.ArkGraphics2D';

// Create a buffer for image effects.
const colorBuffer = new ArrayBuffer(96);
// Set image initialization options.
let opts: image.InitializationOptions = {
  editable: true,
  pixelFormat: 3,
  size: {
    height: 4,
    width: 6
  }
};
// Create a PixelMap instance.
image.createPixelMap(colorBuffer, opts).then((pixelMap) => {
  // Create a Filter instance.
  let headFilter = effectKit.createEffect(pixelMap);
  if (headFilter != null) {
    // Add a grayscale effect and obtain the processed PixelMap.
    headFilter.grayscale().getEffectPixelMap().then(data => {
      console.info('getPixelBytesNumber = ', data.getPixelBytesNumber());
    });
  }
});
```

```TypeScript
import { image } from '@kit.ImageKit';
import { effectKit } from '@kit.ArkGraphics2D';

// Create a buffer for the image effect.
const colorBuffer = new ArrayBuffer(96);
// Set the image initialization options.
let opts: image.InitializationOptions = {
  editable: true,
  pixelFormat: 3,
  size: {
    height: 4,
    width: 6
  }
};
// Create a PixelMap instance.
image.createPixelMap(colorBuffer, opts).then((pixelMap) => {
  // Create a Filter instance, add a grayscale effect, and obtain the processed PixelMap.
  effectKit.createEffect(pixelMap).grayscale().getEffectPixelMap(false).then(data => {
    console.info('getPixelBytesNumber = ', data.getPixelBytesNumber());
  });
});
```

## getEffectPixelMap

```TypeScript
getEffectPixelMap(useCpuRender : boolean): Promise<image.PixelMap>
```

Obtains image.PixelMap of the source image with the linked list effect. The rendering mode (CPU rendering or GPU rendering) can be specified. This API uses a promise to return the result.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**Widget capability:** This API can be used in ArkTS widgets since API version 20.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| useCpuRender | boolean | Yes | Specifies the rendering mode. The value true means CPU rendering, and false means GPU rendering. When GPU rendering is used, the support scope of the shader effect tile mode TileMode differs from that of CPU rendering. For details, see TileMode. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)&gt; | Promise used to return image.PixelMap of the source image. |

**Examples**

See [getEffectPixelMap](#geteffectpixelmap)

## getPixelMap

```TypeScript
getPixelMap(): image.PixelMap
```

Obtains image.PixelMap of the source image to which the effect chain has been added. It is commonly used in scenarios where the processed image needs to be saved or displayed.

> **NOTE:** 
> 
> This API is supported since API version 9 and deprecated since API version 11. Use getEffectPixelMap instead.

**Since:** 9

**Deprecated since:** 11

**Substitutes:** [getEffectPixelMap](#geteffectpixelmap)

**System capability:** SystemCapability.Multimedia.Image.Core

**Return value:**

| Type | Description |
| --- | --- |
| [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md) | [image.PixelMap of the source image with the effect chain applied.](../../apis-image-kit/arkts-apis/arkts-image-multimedia-image.md) |

**Examples**

```TypeScript
import { image } from '@kit.ImageKit';
import { effectKit } from '@kit.ArkGraphics2D';

const colorBuffer = new ArrayBuffer(96);
let opts: image.InitializationOptions = {
  editable: true,
  pixelFormat: 3,
  size: {
    height: 4,
    width: 6
  }
};
image.createPixelMap(colorBuffer, opts).then((pixelMap) => {
  let pixel = effectKit.createEffect(pixelMap).grayscale().getPixelMap();
  console.info('getPixelBytesNumber = ', pixel.getPixelBytesNumber());
});
```

## grayscale

```TypeScript
grayscale(): Filter
```

Adds the grayscale effect to the effect chain and returns the instance of the chain. This method converts a color image into a grayscale image by calculating the grayscale value through weighted RGB values. It is commonly used in scenarios such as black-and-white style photo generation, image preprocessing decolorization, and grayscale icon creation.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core

**Return value:**

| Type | Description |
| --- | --- |
| [Filter](arkts-arkgraphics2d-effectkit-filter-i.md) | Returns the Filter instance with the added effects, which can be used to continue adding effects or obtain the processed image. |

**Examples**

```TypeScript
import { image } from '@kit.ImageKit';
import { effectKit } from '@kit.ArkGraphics2D';
import { common } from '@kit.AbilityKit';
// Pass the image data to be read.
function imageGrayscale(imageBuffer: ArrayBuffer): Promise<image.PixelMap> {
  return new Promise(async (resolve) => {
    // Create the image source.
    let imageSource = image.createImageSource(imageBuffer);
    await imageSource.createPixelMap().then(async (pixelMap: image.PixelMap) => {
      // Create a Filter instance.
      let headFilter = effectKit.createEffect(pixelMap);
      if (headFilter != null) {
        // Add a grayscale effect to the image.
        headFilter.grayscale();
        // Process the image based on the added effect identifier and return the processed image data.
        headFilter.getEffectPixelMap().then(imageData => {
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
  // Read the image file in the rawfile folder. You can also change the read mode as required to ensure that the image data in ArrayBuffer format is obtained.
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
    // Image processing is an asynchronous operation. You can perform the next step based on whether the processed image data needs to be obtained. Add await as required for synchronization.
    this.imagePixelMap = await imageGrayscale(this.imageBuffer);
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

## invert

```TypeScript
invert(): Filter
```

Adds the invert effect to the effect chain and returns the instance of the chain. This method inverts the RGB color values of the image. It is commonly used in scenarios such as negative film effect, image artistic processing, and night mode adaptation.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

**Return value:**

| Type | Description |
| --- | --- |
| [Filter](arkts-arkgraphics2d-effectkit-filter-i.md) | Returns the Filter instance with the added effects, which can be used to continue adding effects or obtain the processed image. |

**Examples**

```TypeScript
import { image } from '@kit.ImageKit';
import { effectKit } from '@kit.ArkGraphics2D';
import { common } from '@kit.AbilityKit';
// Pass the image data to be read.
function imageInvert(imageBuffer: ArrayBuffer): Promise<image.PixelMap> {
  return new Promise(async (resolve) => {
    // Create the image source.
    let imageSource = image.createImageSource(imageBuffer);
    await imageSource.createPixelMap().then(async (pixelMap: image.PixelMap) => {
      // Create a Filter instance.
      let headFilter = effectKit.createEffect(pixelMap);
      if (headFilter != null) {
        // Add an inversion effect to the image.
        headFilter.invert();
        // Process the image based on the added effect identifiers and return the processed image data.
        headFilter.getEffectPixelMap().then(imageData => {
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
  // Read the image file in the rawfile folder. You can also change the read mode as required to ensure that the image data in ArrayBuffer format is obtained.
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
    // Image processing is an asynchronous operation. You can perform the next step based on whether the processed image data needs to be obtained. Add await as required for synchronization.
    this.imagePixelMap = await imageInvert(this.imageBuffer);
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

## setColorMatrix

```TypeScript
setColorMatrix(colorMatrix: Array<number>): Filter
```

Performs color transformation on the image using a custom color matrix, adds the effect to the effect chain, and returns the instance of the chain. It is commonly used in scenarios such as implementing custom color effects not supported by preset filters, such as vintage tones and warm/cool tone adjustments.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| colorMatrix | Array&lt;number&gt; | Yes | Custom color matrix. A 4x5 matrix used to create an effect filter. The array length must be 20. The first four columns correspond to the transformation coefficients of the R, G, B, and A channels, and the fifth column is the constant offset value. It is recommended that the element values be in the range [-1, 1]. Values outside this range may cause color value overflow or unexpected effects. If the array length is not 20, null is returned. |

**Return value:**

| Type | Description |
| --- | --- |
| [Filter](arkts-arkgraphics2d-effectkit-filter-i.md) | Filter instance with effects added, which can be used to add more effects or obtain the processed image. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Input parameter error. |

**Examples**

```TypeScript
import { image } from '@kit.ImageKit';
import { effectKit } from '@kit.ArkGraphics2D';
import { common } from '@kit.AbilityKit';
// Pass the image data to be read.
function imageColorFilter(imageBuffer: ArrayBuffer): Promise<image.PixelMap> {
  return new Promise(async (resolve) => {
    // Create the image source.
    let imageSource = image.createImageSource(imageBuffer);
    await imageSource.createPixelMap().then(async (pixelMap: image.PixelMap) => {
      // Define the color matrix.
      let colorMatrix: Array<number> = [
        0.2126, 0.7152, 0.0722, 0, 0,
        0.2126, 0.7152, 0.0722, 0, 0,
        0.2126, 0.7152, 0.0722, 0, 0,
        0, 0, 0, 1, 0
      ];
      // Create a Filter instance.
      let headFilter = effectKit.createEffect(pixelMap);
      if (headFilter != null) {
        // Apply a custom color matrix effect to the image.
        headFilter.setColorMatrix(colorMatrix);
        // Process the image based on the added effect identifier and return the processed image data.
        headFilter.getEffectPixelMap().then(imageData => {
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
  // Read the image file in the rawfile folder. You can also change the read mode as required to ensure that the image data in ArrayBuffer format is obtained.
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
    // Image processing is an asynchronous operation. You can perform the next step based on whether the processed image data needs to be obtained. Add await as required for synchronization.
    this.imagePixelMap = await imageColorFilter(this.imageBuffer);
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
