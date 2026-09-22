# ImageProcessor

```TypeScript
interface ImageProcessor
```

Provides the ImageProcessor type, including the processing function. @typedef ImageProcessor

**Since:** 18

**System capability:** SystemCapability.Multimedia.VideoProcessingEngine

## Modules to Import

```TypeScript
import { videoProcessingEngine } from '@kit.ImageKit';
```

## enhanceDetail

```TypeScript
enhanceDetail(sourceImage: image.PixelMap, width: number, height: number, level?: QualityLevel): Promise<image.PixelMap>
```

The function generate the destinationImage from sourceImage with necessary scaling operation <br>according to width and height. Different levels of scaling methods are provided to <br>balance performance and image quality. This method uses a promise to return the result.

**Since:** 18

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

**System capability:** SystemCapability.Multimedia.VideoProcessingEngine

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sourceImage | [image.PixelMap](arkts-image-image-pixelmap-i.md) | Yes | The source pixelmap. |
| width | number | Yes | The zoom value of width. |
| height | number | Yes | The zoom value of height. |
| level | [QualityLevel](arkts-image-videoprocessingengine-qualitylevel-e.md) | No | The quality level. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[image.PixelMap](arkts-image-image-pixelmap-i.md)&gt; | A Promise instance used to return the PixelMap object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Function enhanceDetail can not work correctly due to<br>limited device capabilities. |
| [29200007](../errorcode-videoprocessingengine.md#29200007-insufficient-memory) | Out of memory. |
| [29200009](../errorcode-videoprocessingengine.md#29200009-invalid-value) | Input value is invalid. This error is returned for<br>all of the following error conditions: <br>1 - Invalid input or output image buffer - The image buffer width(height) <br>is too large or colorspace is incorrect. <br>2 - Invalid parameter - The parameter does not contain valid information, <br>such as detail enhancer level is incorrect. |

**Examples**

```TypeScript
import { image, videoProcessingEngine } from '@kit.ImageKit';

async function enhanceDetail(sourceImage: image.PixelMap, width: number, height: number) {
  videoProcessingEngine.initializeEnvironment();
  let imageProcessor = videoProcessingEngine.create() as videoProcessingEngine.ImageProcessor;
  // Example: The width can be set to 1024, and the height can be set to 1280.
  let enhancedPixelmap: Promise<image.PixelMap> =
    imageProcessor.enhanceDetail(sourceImage, width, height, videoProcessingEngine.QualityLevel.HIGH);
}
```

<a id="enhancedetail-1"></a>

## enhanceDetail

```TypeScript
enhanceDetail(sourceImage: image.PixelMap, scale: number, level?: QualityLevel): Promise<image.PixelMap>
```

The function generate the destinationImage from sourceImage with necessary scaling operation <br>according to the zoom ratio. Different levels of scaling methods are provided to <br>balance performance and image quality. This method uses a promise to return the result.

**Since:** 18

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

**System capability:** SystemCapability.Multimedia.VideoProcessingEngine

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sourceImage | [image.PixelMap](arkts-image-image-pixelmap-i.md) | Yes | The source pixelmap. |
| scale | number | Yes | The zoom ratio. |
| level | [QualityLevel](arkts-image-videoprocessingengine-qualitylevel-e.md) | No | The quality level. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[image.PixelMap](arkts-image-image-pixelmap-i.md)&gt; | A Promise instance used to return the PixelMap object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Function enhanceDetail can not work correctly due to<br>limited device capabilities. |
| [29200007](../errorcode-videoprocessingengine.md#29200007-insufficient-memory) | Out of memory. |
| [29200009](../errorcode-videoprocessingengine.md#29200009-invalid-value) | Input value is invalid. This error is returned for<br>all of the following error conditions: <br>1 - Invalid input or output image buffer - The image buffer width(height) <br>is too large or colorspace is incorrect. <br>2 - Invalid parameter - The parameter does not contain valid information, <br>such as detail enhancer level is incorrect. |

**Examples**

```TypeScript
import { image, videoProcessingEngine } from '@kit.ImageKit';

async function enhanceDetail(sourceImage: image.PixelMap, scale: number) {
  videoProcessingEngine.initializeEnvironment();
  let imageProcessor = videoProcessingEngine.create() as videoProcessingEngine.ImageProcessor;
  // Example: The scale can be set to 2.0.
  let enhancedPixelmap: Promise<image.PixelMap> =
    imageProcessor.enhanceDetail(sourceImage, scale, videoProcessingEngine.QualityLevel.HIGH);
}
```

## enhanceDetailSync

```TypeScript
enhanceDetailSync(sourceImage: image.PixelMap, width: number, height: number, level?: QualityLevel): image.PixelMap
```

The function generate the destinationImage from sourceImage with necessary scaling operation <br>according to width and height. Different levels of scaling methods are provided to <br>balance performance and image quality.

**Since:** 18

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

**System capability:** SystemCapability.Multimedia.VideoProcessingEngine

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sourceImage | [image.PixelMap](arkts-image-image-pixelmap-i.md) | Yes | The source pixelmap. |
| width | number | Yes | The zoom value of width. |
| height | number | Yes | The zoom value of height. |
| level | [QualityLevel](arkts-image-videoprocessingengine-qualitylevel-e.md) | No | The quality level. |

**Return value:**

| Type | Description |
| --- | --- |
| [image.PixelMap](arkts-image-image-pixelmap-i.md) | Returns the destination pixelmap instance .<br>if the operation is successful; Otherwise, return undefined. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Function enhanceDetailSync can not work correctly due<br>to limited device capabilities. |
| [29200004](../errorcode-videoprocessingengine.md#29200004-processing-failure) | Failed to process image buffer. For example, the processing times out. |
| [29200007](../errorcode-videoprocessingengine.md#29200007-insufficient-memory) | Out of memory. |
| [29200009](../errorcode-videoprocessingengine.md#29200009-invalid-value) | Input value is invalid. This error is returned for<br>all of the following error conditions: <br>1 - Invalid input or output image buffer - The image buffer width(height) <br>is too large or colorspace is incorrect. <br>2 - Invalid parameter - The parameter does not contain valid information, <br>such as detail enhancer level is incorrect. |

**Examples**

```TypeScript
import { image, videoProcessingEngine } from '@kit.ImageKit';

async function enhanceDetailSync(sourceImage: image.PixelMap, width: number, height: number) {
  videoProcessingEngine.initializeEnvironment();
  let imageProcessor = videoProcessingEngine.create() as videoProcessingEngine.ImageProcessor;
  // Example: The width can be set to 1024, and the height can be set to 1280.
  let enhancedPixelmap: image.PixelMap = imageProcessor.enhanceDetailSync(
    sourceImage, width, height, videoProcessingEngine.QualityLevel.HIGH);
}
```

<a id="enhancedetailsync-1"></a>

## enhanceDetailSync

```TypeScript
enhanceDetailSync(sourceImage: image.PixelMap, scale: number, level?: QualityLevel): image.PixelMap
```

The function generate the destinationImage from sourceImage with necessary scaling operation <br>according to the zoom ratio. Different levels of scaling methods are provided to <br>balance performance and image quality.

**Since:** 18

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

**System capability:** SystemCapability.Multimedia.VideoProcessingEngine

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sourceImage | [image.PixelMap](arkts-image-image-pixelmap-i.md) | Yes | The source pixelmap. |
| scale | number | Yes | The zoom ratio. |
| level | [QualityLevel](arkts-image-videoprocessingengine-qualitylevel-e.md) | No | The quality level. |

**Return value:**

| Type | Description |
| --- | --- |
| [image.PixelMap](arkts-image-image-pixelmap-i.md) | Returns the destination pixelmap instance<br>if the operation is successful; Otherwise, return undefined. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Function enhanceDetailSync can not work correctly due<br>to limited device capabilities. |
| [29200004](../errorcode-videoprocessingengine.md#29200004-processing-failure) | Failed to process image buffer. For example, the processing times out. |
| [29200007](../errorcode-videoprocessingengine.md#29200007-insufficient-memory) | Out of memory. |
| [29200009](../errorcode-videoprocessingengine.md#29200009-invalid-value) | Input value is invalid. This error is returned for<br>all of the following error conditions: <br>1 - Invalid input or output image buffer - The image buffer width(height) <br>is too large or colorspace is incorrect. <br>2 - Invalid parameter - The parameter does not contain valid information, <br>such as detail enhancer level is incorrect. |

**Examples**

```TypeScript
import { image, videoProcessingEngine } from '@kit.ImageKit';

async function enhanceDetailSync(sourceImage: image.PixelMap, scale: number) {
  videoProcessingEngine.initializeEnvironment();
  let imageProcessor = videoProcessingEngine.create() as videoProcessingEngine.ImageProcessor;
  // Example: The scale can be set to 2.0.
  let enhancedPixelmap: image.PixelMap = imageProcessor.enhanceDetailSync(
    sourceImage, scale, videoProcessingEngine.QualityLevel.HIGH);
}
```
