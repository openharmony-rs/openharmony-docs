# PixelMap

```TypeScript
interface PixelMap
```

The **PixelMap** class provides APIs to read or write image data and obtain image information. Before calling any API in PixelMap, you must use [image.createPixelMap](arkts-image-image-createpixelmap-f.md#createpixelmap-1) to create a PixelMap object. Currently, the maximum size of a serialized PixelMap is 128 MB. A larger size will cause a display failure. The size is calculated as follows: Width x Height x [Bytes per pixel](arkts-image-image-pixelmapformat-e.md). Since API version 11, PixelMap supports cross-thread calls through [Worker](../../apis-arkts/arkts-apis/arkts-arkts-worker-n.md). If a PixelMap object is invoked by another thread through [Worker](../../apis-arkts/arkts-apis/arkts-arkts-worker-n.md), all APIs of the PixelMap object cannot be called in the original thread. Otherwise, error 501 is reported, indicating that the server cannot complete the request. Before calling any API in PixelMap, you can use [image.createPixelMap](arkts-image-image-createpixelmap-f.md#createpixelmap-1) to pass pixel data to create a PixelMap object, or use [ImageSource](arkts-image-multimedia-image.md) to decode an image to a PixelMap object. To develop an atomic service, use [ImageSource](arkts-image-multimedia-image.md) to create a PixelMap object. Images occupy a large amount of memory. When you finish using a PixelMap instance, call [release](#release) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**Since:** 7

**System capability:** SystemCapability.Multimedia.Image.Core

## Modules to Import

```TypeScript
import { image } from '@kit.ImageKit';
```

## applyColorSpace

```TypeScript
applyColorSpace(targetColorSpace: colorSpaceManager.ColorSpaceManager, callback: AsyncCallback<void>): void
```

Performs color space conversion (CSC) on the image pixel color based on a given color space. This API uses an asynchronous callback to return the result.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| targetColorSpace | [colorSpaceManager.ColorSpaceManager](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-colorspacemanager-colorspacemanager-i.md) | Yes | Target color space. SRGB, DCI_P3, DISPLAY_P3, and ADOBE_RGB_1998 are supported. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [62980104](../errorcode-image.md#62980104-image-initialization-error) | Failed to initialize the internal object. |
| [62980108](../errorcode-image.md#62980108-image-color-conversion-error) | Failed to convert the color space. |
| [62980115](../errorcode-image.md#62980115-invalid-image-parameter) | Invalid image parameter. |

**Examples**

```TypeScript
import { colorSpaceManager } from '@kit.ArkGraphics2D';
import { BusinessError } from '@kit.BasicServicesKit';

function applyColorSpace(pixelMap: image.PixelMap) {
  const colorSpaceName = colorSpaceManager.ColorSpace.SRGB;
  const targetColorSpace: colorSpaceManager.ColorSpaceManager = colorSpaceManager.create(colorSpaceName);
  pixelMap.applyColorSpace(targetColorSpace, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to apply color space. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in applying color space.');
  });
}
```

<a id="applycolorspace-1"></a>

## applyColorSpace

```TypeScript
applyColorSpace(targetColorSpace: colorSpaceManager.ColorSpaceManager): Promise<void>
```

Performs Color Space Converters (CSC) on the image pixel color based on a given color space. This API uses a promise to return the result.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| targetColorSpace | [colorSpaceManager.ColorSpaceManager](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-colorspacemanager-colorspacemanager-i.md) | Yes | Target color space. SRGB, DCI_P3, DISPLAY_P3, and ADOBE_RGB_1998 are supported. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [62980104](../errorcode-image.md#62980104-image-initialization-error) | Failed to initialize the internal object. |
| [62980108](../errorcode-image.md#62980108-image-color-conversion-error) | Failed to convert the color space. |
| [62980115](../errorcode-image.md#62980115-invalid-image-parameter) | Invalid image parameter. |

**Examples**

```TypeScript
import { colorSpaceManager } from '@kit.ArkGraphics2D';
import { BusinessError } from '@kit.BasicServicesKit';

function applyColorSpace(pixelMap: image.PixelMap) {
  const colorSpaceName = colorSpaceManager.ColorSpace.SRGB;
  const targetColorSpace: colorSpaceManager.ColorSpaceManager = colorSpaceManager.create(colorSpaceName);
  pixelMap.applyColorSpace(targetColorSpace).then(() => {
    console.info('Succeeded in applying color space.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to apply color space. Code: ${err.code}, message: ${err.message}`);
  });
}
```

## applyCrop

```TypeScript
applyCrop(region: Region): Promise<void>
```

Crops the PixelMap.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| region | [Region](arkts-image-image-region-i.md) | Yes | The region to crop. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | A Promise that resolves when the operation completes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7600104](../errorcode-image.md#7600104-failed-to-obtain-image-data) | Failed to get image data. Possible cause: Internal data is corrupted. Please check the logs for detailed information. |
| [7600105](../errorcode-image.md#7600105-pixelmap-object-has-been-released) | The PixelMap has been released. |
| [7600106](../errorcode-image.md#7600106-pixelmap-has-been-passed-to-another-thread) | The PixelMap has been passed to another thread. |
| [7600201](../errorcode-image.md#7600201-unsupported-operation) | Unsupported operation because the PixelMap is locked. |
| [7600204](../errorcode-image.md#7600204-invalid-region) | The specified region is invalid or out of range. |
| [7600301](../errorcode-image.md#7600301-memory-allocation-failure) | Failed to allocate memory. Possible causes: 1. Failed to process pixel data. 2. The system is out of memory. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function applyCrop(pixelMap: image.PixelMap) {
  const currSize = pixelMap.getImageInfoSync().size;
  const region: image.Region = { // The cropping region is set to the central quarter of the image.
    x: currSize.width / 4,
    y: currSize.height / 4,
    size: {
      width: currSize.width / 2,
      height: currSize.height / 2
    }
  };

  pixelMap.applyCrop(region)
    .then(() => {
      console.info('Succeeded in cropping the PixelMap.');
    })
    .catch((err: BusinessError) => {
      console.error(`Failed to crop the PixelMap. Code: ${err.code}, message: ${err.message}`);
    });
}
```

## applyCropSync

```TypeScript
applyCropSync(region: Region): void
```

Crops the PixelMap.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| region | [Region](arkts-image-image-region-i.md) | Yes | The region to crop. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7600104](../errorcode-image.md#7600104-failed-to-obtain-image-data) | Failed to get image data. Possible cause: Internal data is corrupted. Please check the logs for detailed information. |
| [7600105](../errorcode-image.md#7600105-pixelmap-object-has-been-released) | The PixelMap has been released. |
| [7600106](../errorcode-image.md#7600106-pixelmap-has-been-passed-to-another-thread) | The PixelMap has been passed to another thread. |
| [7600201](../errorcode-image.md#7600201-unsupported-operation) | Unsupported operation because the PixelMap is locked. |
| [7600204](../errorcode-image.md#7600204-invalid-region) | The specified region is invalid or out of range. |
| [7600301](../errorcode-image.md#7600301-memory-allocation-failure) | Failed to allocate memory. Possible causes: 1. Failed to process pixel data. 2. The system is out of memory. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function applyCropSync(pixelMap: image.PixelMap) {
  const currSize = pixelMap.getImageInfoSync().size;
  const region: image.Region = { // The cropping region is set to the central quarter of the image.
    x: currSize.width / 4,
    y: currSize.height / 4,
    size: {
      width: currSize.width / 2,
      height: currSize.height / 2
    }
  };

  try {
    pixelMap.applyCropSync(region);
    console.info('Succeeded in cropping the PixelMap.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to crop the PixelMap. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## applyFlip

```TypeScript
applyFlip(horizontal: boolean, vertical: boolean): Promise<void>
```

Flips the PixelMap in the horizontal and/or vertical directions.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| horizontal | boolean | Yes | Whether to flip horizontally. |
| vertical | boolean | Yes | Whether to flip vertically. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | A Promise that resolves when the operation completes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7600104](../errorcode-image.md#7600104-failed-to-obtain-image-data) | Failed to get image data. Possible cause: Internal data is corrupted. Please check the logs for detailed information. |
| [7600105](../errorcode-image.md#7600105-pixelmap-object-has-been-released) | The PixelMap has been released. |
| [7600106](../errorcode-image.md#7600106-pixelmap-has-been-passed-to-another-thread) | The PixelMap has been passed to another thread. |
| [7600201](../errorcode-image.md#7600201-unsupported-operation) | Unsupported operation because the PixelMap is locked. |
| [7600206](../errorcode-image.md#7600206-invalid-parameter) | Invalid parameter. |
| [7600301](../errorcode-image.md#7600301-memory-allocation-failure) | Failed to allocate memory. Possible cause: The system is out of memory. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function applyFlip(pixelMap: image.PixelMap) {
  const horizontal: boolean = true;
  const vertical: boolean = false;
  pixelMap.applyFlip(horizontal, vertical)
    .then(() => {
      console.info('Succeeded in flipping the PixelMap.');
    })
    .catch((err: BusinessError) => {
      console.error(`Failed to flip the PixelMap. Code: ${err.code}, message: ${err.message}`);
    });
}
```

## applyFlipSync

```TypeScript
applyFlipSync(horizontal: boolean, vertical: boolean): void
```

Flips the PixelMap in the horizontal and/or vertical directions.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| horizontal | boolean | Yes | Whether to flip horizontally. |
| vertical | boolean | Yes | Whether to flip vertically. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7600104](../errorcode-image.md#7600104-failed-to-obtain-image-data) | Failed to get image data. Possible cause: Internal data is corrupted. Please check the logs for detailed information. |
| [7600105](../errorcode-image.md#7600105-pixelmap-object-has-been-released) | The PixelMap has been released. |
| [7600106](../errorcode-image.md#7600106-pixelmap-has-been-passed-to-another-thread) | The PixelMap has been passed to another thread. |
| [7600201](../errorcode-image.md#7600201-unsupported-operation) | Unsupported operation because the PixelMap is locked. |
| [7600206](../errorcode-image.md#7600206-invalid-parameter) | Invalid parameter. |
| [7600301](../errorcode-image.md#7600301-memory-allocation-failure) | Failed to allocate memory. Possible cause: The system is out of memory. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function applyFlipSync(pixelMap: image.PixelMap) {
  const horizontal: boolean = true;
  const vertical: boolean = false;
  try {
    pixelMap.applyFlipSync(horizontal, vertical);
    console.info('Succeeded in flipping the PixelMap.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to flip the PixelMap. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## applyRotate

```TypeScript
applyRotate(angle: number): Promise<void>
```

Rotates the PixelMap.

Note: YUV format PixelMaps only support rotation angles that are multiples of 90 degrees.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| angle | number | Yes | The rotation angle in degrees. Unit: Degree. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | A Promise that resolves when the operation completes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7600104](../errorcode-image.md#7600104-failed-to-obtain-image-data) | Failed to get image data. Possible cause: Internal data is corrupted. Please check the logs for detailed information. |
| [7600105](../errorcode-image.md#7600105-pixelmap-object-has-been-released) | The PixelMap has been released. |
| [7600106](../errorcode-image.md#7600106-pixelmap-has-been-passed-to-another-thread) | The PixelMap has been passed to another thread. |
| [7600201](../errorcode-image.md#7600201-unsupported-operation) | Unsupported operation because the PixelMap is locked. |
| [7600206](../errorcode-image.md#7600206-invalid-parameter) | Invalid parameter. |
| [7600301](../errorcode-image.md#7600301-memory-allocation-failure) | Failed to allocate memory. Possible causes: 1. The resulting PixelMap size is too large. 2. The system is out of memory. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function applyRotate(pixelMap: image.PixelMap) {
  const angle: number = 90.0;
  pixelMap.applyRotate(angle)
    .then(() => {
      console.info('Succeeded in rotating the PixelMap.');
    })
    .catch((err: BusinessError) => {
      console.error(`Failed to rotate the PixelMap. Code: ${err.code}, message: ${err.message}`);
    });
}
```

## applyRotateSync

```TypeScript
applyRotateSync(angle: number): void
```

Rotates the PixelMap.

Note: YUV format PixelMaps only support rotation angles that are multiples of 90 degrees.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| angle | number | Yes | The rotation angle in degrees. Unit: Degree. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7600104](../errorcode-image.md#7600104-failed-to-obtain-image-data) | Failed to get image data. Possible cause: Internal data is corrupted. Please check the logs for detailed information. |
| [7600105](../errorcode-image.md#7600105-pixelmap-object-has-been-released) | The PixelMap has been released. |
| [7600106](../errorcode-image.md#7600106-pixelmap-has-been-passed-to-another-thread) | The PixelMap has been passed to another thread. |
| [7600201](../errorcode-image.md#7600201-unsupported-operation) | Unsupported operation because the PixelMap is locked. |
| [7600206](../errorcode-image.md#7600206-invalid-parameter) | Invalid parameter. |
| [7600301](../errorcode-image.md#7600301-memory-allocation-failure) | Failed to allocate memory. Possible causes: 1. The resulting PixelMap size is too large. 2. The system is out of memory. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function applyRotateSync(pixelMap: image.PixelMap) {
  const angle: number = 90.0;
  try {
    pixelMap.applyRotateSync(angle);
    console.info('Succeeded in rotating the PixelMap.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to rotate the PixelMap. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## applyScale

```TypeScript
applyScale(x: number, y: number, level?: AntiAliasingLevel): Promise<void>
```

Scales the PixelMap in the horizontal and/or vertical dimensions.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | The scale ratio of width. Unit: Percentage. |
| y | number | Yes | The scale ratio of height. Unit: Percentage. |
| level | [AntiAliasingLevel](arkts-image-image-antialiasinglevel-e.md) | No | The anti-aliasing algorithm to be used. Default value: NONE. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | A Promise that resolves when the operation completes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7600104](../errorcode-image.md#7600104-failed-to-obtain-image-data) | Failed to get image data. Possible cause: Internal data is corrupted. Please check the logs for detailed information. |
| [7600105](../errorcode-image.md#7600105-pixelmap-object-has-been-released) | The PixelMap has been released. |
| [7600106](../errorcode-image.md#7600106-pixelmap-has-been-passed-to-another-thread) | The PixelMap has been passed to another thread. |
| [7600201](../errorcode-image.md#7600201-unsupported-operation) | Unsupported operation because the PixelMap is locked. |
| [7600206](../errorcode-image.md#7600206-invalid-parameter) | Invalid parameter. |
| [7600301](../errorcode-image.md#7600301-memory-allocation-failure) | Failed to allocate memory. Possible causes: 1. The resulting PixelMap size is too large. 2. The system is out of memory. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function applyScale(pixelMap: image.PixelMap) {
  const scaleX: number = 2.0;
  const scaleY: number = 1.5;
  pixelMap.applyScale(scaleX, scaleY, image.AntiAliasingLevel.LOW)
    .then(() => {
      console.info('Succeeded in scaling the PixelMap.');
    })
    .catch((err: BusinessError) => {
      console.error(`Failed to scale the PixelMap. Code: ${err.code}, message: ${err.message}`);
    });
}
```

## applyScaleSync

```TypeScript
applyScaleSync(x: number, y: number, level?: AntiAliasingLevel): void
```

Scales the PixelMap in the horizontal and/or vertical dimensions.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | The scale ratio of width. Unit: Percentage. |
| y | number | Yes | The scale ratio of height. Unit: Percentage. |
| level | [AntiAliasingLevel](arkts-image-image-antialiasinglevel-e.md) | No | The anti-aliasing algorithm to be used. Default value: NONE. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7600104](../errorcode-image.md#7600104-failed-to-obtain-image-data) | Failed to get image data. Possible cause: Internal data is corrupted. Please check the logs for detailed information. |
| [7600105](../errorcode-image.md#7600105-pixelmap-object-has-been-released) | The PixelMap has been released. |
| [7600106](../errorcode-image.md#7600106-pixelmap-has-been-passed-to-another-thread) | The PixelMap has been passed to another thread. |
| [7600201](../errorcode-image.md#7600201-unsupported-operation) | Unsupported operation because the PixelMap is locked. |
| [7600206](../errorcode-image.md#7600206-invalid-parameter) | Invalid parameter. |
| [7600301](../errorcode-image.md#7600301-memory-allocation-failure) | Failed to allocate memory. Possible causes: 1. The resulting PixelMap size is too large. 2. The system is out of memory. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function applyScaleSync(pixelMap: image.PixelMap) {
  const scaleX: number = 2.0;
  const scaleY: number = 1.5;
  try {
    pixelMap.applyScaleSync(scaleX, scaleY, image.AntiAliasingLevel.LOW);
    console.info('Succeeded in scaling the PixelMap.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to scale the PixelMap. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## applyTranslate

```TypeScript
applyTranslate(x: number, y: number): Promise<void>
```

Repositions the PixelMap in the horizontal and/or vertical directions.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | The distance in pixels to move in the horizontal direction. Unit: px. |
| y | number | Yes | The distance in pixels to move in the vertical direction. Unit: px. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | A Promise that resolves when the operation completes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7600104](../errorcode-image.md#7600104-failed-to-obtain-image-data) | Failed to get image data. Possible cause: Internal data is corrupted. Please check the logs for detailed information. |
| [7600105](../errorcode-image.md#7600105-pixelmap-object-has-been-released) | The PixelMap has been released. |
| [7600106](../errorcode-image.md#7600106-pixelmap-has-been-passed-to-another-thread) | The PixelMap has been passed to another thread. |
| [7600201](../errorcode-image.md#7600201-unsupported-operation) | Unsupported operation because the PixelMap is locked. |
| [7600206](../errorcode-image.md#7600206-invalid-parameter) | Invalid parameter. |
| [7600301](../errorcode-image.md#7600301-memory-allocation-failure) | Failed to allocate memory. Possible causes: 1. The resulting PixelMap size is too large. 2. The system is out of memory. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function applyTranslate(pixelMap: image.PixelMap) {
  const translateX: number = 50.0;
  const translateY: number = 10.0;
  pixelMap.applyTranslate(translateX, translateY)
    .then(() => {
      console.info('Succeeded in translating the PixelMap.');
    })
    .catch((err: BusinessError) => {
      console.error(`Failed to translate the PixelMap. Code: ${err.code}, message: ${err.message}`);
    });
}
```

## applyTranslateSync

```TypeScript
applyTranslateSync(x: number, y: number): void
```

Repositions the PixelMap in the horizontal and/or vertical directions.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | The distance in pixels to move in the horizontal direction. Unit: px. |
| y | number | Yes | The distance in pixels to move in the vertical direction. Unit: px. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7600104](../errorcode-image.md#7600104-failed-to-obtain-image-data) | Failed to get image data. Possible cause: Internal data is corrupted. Please check the logs for detailed information. |
| [7600105](../errorcode-image.md#7600105-pixelmap-object-has-been-released) | The PixelMap has been released. |
| [7600106](../errorcode-image.md#7600106-pixelmap-has-been-passed-to-another-thread) | The PixelMap has been passed to another thread. |
| [7600201](../errorcode-image.md#7600201-unsupported-operation) | Unsupported operation because the PixelMap is locked. |
| [7600206](../errorcode-image.md#7600206-invalid-parameter) | Invalid parameter. |
| [7600301](../errorcode-image.md#7600301-memory-allocation-failure) | Failed to allocate memory. Possible causes: 1. The resulting PixelMap size is too large. 2. The system is out of memory. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function applyTranslateSync(pixelMap: image.PixelMap) {
  const translateX: number = 50.0;
  const translateY: number = 10.0;
  try {
    pixelMap.applyTranslateSync(translateX, translateY);
    console.info('Succeeded in translating the PixelMap.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to translate the PixelMap. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## clone

```TypeScript
clone(): Promise<PixelMap>
```

Copies this PixelMap object. This API uses a promise to return the result.

**Since:** 18

**System capability:** SystemCapability.Multimedia.Image.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[PixelMap](arkts-image-image-pixelmap-i.md)&gt; | Promise used to return the PixelMap object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [501](../errorcode-image.md#501-api-call-failed) | The resource is unavailable as it is occupied by another thread. |
| [62980102](../errorcode-image.md#62980102-memory-allocation-error-for-images) | Image malloc abnormal. This status code is thrown when an error occurs during the process of copying data. |
| [62980103](../errorcode-image.md#62980103-unsupported-image-type) | Image YUV And ASTC types are not supported. |
| [62980104](../errorcode-image.md#62980104-image-initialization-error) | Image initialization abnormal. This status code is thrown when an error occurs during the process of creating empty pixelmap. |
| [62980106](../errorcode-image.md#62980106-too-large-image-data) | The image data is too large. This status code is thrown when an error occurs during the process of checking size. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function clone(pixelMap: image.PixelMap) {
  pixelMap.clone().then((clonedPixelMap: image.PixelMap) => {
    console.info('Succeeded in cloning the PixelMap.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to clone the PixelMap. Code: ${err.code}, message: ${err.message}`);
  });
}
```

## cloneSync

```TypeScript
cloneSync(): PixelMap
```

Copies this PixelMap object. This API returns the result synchronously.

**Since:** 18

**System capability:** SystemCapability.Multimedia.Image.Core

**Return value:**

| Type | Description |
| --- | --- |
| [PixelMap](arkts-image-image-pixelmap-i.md) | PixelMap object. If the operation fails, an error is thrown. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [501](../errorcode-image.md#501-api-call-failed) | The resource is unavailable as it is occupied by another thread. |
| [62980102](../errorcode-image.md#62980102-memory-allocation-error-for-images) | Image malloc abnormal. This status code is thrown when an error occurs during the process of copying data. |
| [62980103](../errorcode-image.md#62980103-unsupported-image-type) | Image YUV And ASTC types are not supported. |
| [62980104](../errorcode-image.md#62980104-image-initialization-error) | Image initialization abnormal. This status code is thrown when an error occurs during the process of creating empty pixelmap. |
| [62980106](../errorcode-image.md#62980106-too-large-image-data) | The image data is too large. This status code is thrown when an error occurs during the process of checking size. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function cloneSync(pixelMap: image.PixelMap) {
  try {
    let clonedPixelMap: image.PixelMap = pixelMap.cloneSync();
    console.info('Succeeded in cloning the PixelMap.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to clone the PixelMap. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## convertPixelFormat

```TypeScript
convertPixelFormat(targetPixelFormat: PixelMapFormat): Promise<void>
```

The method is used for the transformation of the image formats. Pixel data will be changed by calling this method.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| targetPixelFormat | [PixelMapFormat](arkts-image-image-pixelmapformat-e.md) | Yes | The pixel format for pixelmap conversion. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | A Promise instance used to return the operation result. If the operation fails, an error message is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [62980115](../errorcode-image.md#62980115-invalid-image-parameter) | Invalid input parameter. |
| [62980111](../errorcode-image.md#62980111-incomplete-image-source-data) | The image source data is incomplete. |
| [62980274](../errorcode-image.md#62980274-failed-to-convert-images) | The conversion failed. |
| [62980276](../errorcode-image.md#62980276-unsupported-image-conversion-target-type) | The type to be converted is an unsupported target pixel format. |
| [62980178](../errorcode-image.md#62980178-failure-in-creating-a-pixelmap) | Failed to create the pixelmap. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function convertPixelFormat(pixelMap: image.PixelMap) {
  // Set the target pixel format to NV12.
  let targetPixelFormat = image.PixelMapFormat.NV12;
  pixelMap.convertPixelFormat(targetPixelFormat).then(() => {
    console.info('Succeeded in converting pixel format.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to convert pixel format. Code: ${err.code}, message: ${err.message}`);
  });
}
```

## createAlphaPixelmap

```TypeScript
createAlphaPixelmap(): Promise<PixelMap>
```

Creates a PixelMap object that contains only the alpha channel information. This object can be used for the shadow effect. It is invalid for YUV images. This API uses a promise to return the result.

Starting from API 26.0.0, it is recommended to use [extractAlphaPixelMap](#extractalphapixelmap) instead for better exception handling capabilities.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[PixelMap](arkts-image-image-pixelmap-i.md)&gt; | Promise used to return the PixelMap object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function createAlphaPixelmap(pixelMap: image.PixelMap) {
  pixelMap.createAlphaPixelmap().then((alphaPixelMap: image.PixelMap) => {
    console.info('Succeeded in creating alpha PixelMap.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to create alpha PixelMap. Code: ${err.code}, message: ${err.message}`);
  });
}
```

<a id="createalphapixelmap-1"></a>

## createAlphaPixelmap

```TypeScript
createAlphaPixelmap(callback: AsyncCallback<PixelMap>): void
```

Creates a PixelMap object that contains only the alpha channel information. This object can be used for the shadow effect. It is invalid for YUV images. This API returns the result through a callback.

Starting from API 26.0.0, it is recommended to use [extractAlphaPixelMap](#extractalphapixelmap) instead for better exception handling capabilities.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[PixelMap](arkts-image-image-pixelmap-i.md)&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is undefined and **data** is the PixelMap object obtained; otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function createAlphaPixelmap(pixelMap: image.PixelMap) {
  pixelMap.createAlphaPixelmap((err: BusinessError, alphaPixelMap: image.PixelMap) => {
    if (err) {
      console.error(`Failed to create alpha PixelMap. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in creating alpha PixelMap.');
  });
}
```

## createAlphaPixelmapSync

```TypeScript
createAlphaPixelmapSync(): PixelMap
```

Creates a PixelMap object that contains only the alpha channel information. This object can be used for the shadow effect. This API returns the result synchronously. It is invalid for YUV images.

Starting from API 26.0.0, it is recommended to use [extractAlphaPixelMapSync](#extractalphapixelmapsync) instead for better exception handling capabilities.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core

**Return value:**

| Type | Description |
| --- | --- |
| [PixelMap](arkts-image-image-pixelmap-i.md) | PixelMap object. If the operation fails, an error is thrown. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Parameter verification failed. |
| [501](../errorcode-image.md#501-api-call-failed) | The resource is unavailable as it is occupied by another thread. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function createAlphaPixelmapSync(pixelMap: image.PixelMap) {
  try {
    let pixelmap: image.PixelMap = pixelMap.createAlphaPixelmapSync();
    console.info('Succeeded in creating alpha PixelMap.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to create alpha PixelMap. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## createCroppedAndScaledPixelMap

```TypeScript
createCroppedAndScaledPixelMap(region: Region, x: number, y: number, level?: AntiAliasingLevel): Promise<PixelMap>
```

Creates an image that has been cropped and resized based on the specified cropping area, scale factors of the width and height, and anti-aliasing level. This API uses a promise to return the result.

**Since:** 22

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| region | [Region](arkts-image-image-region-i.md) | Yes | Area to crop. It must be within the original image's dimension (in pixels). |
| x | number | Yes | Scale factor of the width. It must not be **0**. |
| y | number | Yes | Scale factor of the height. It must not be **0**. |
| level | [AntiAliasingLevel](arkts-image-image-antialiasinglevel-e.md) | No | Anti-aliasing level. Default value: **NONE**. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[PixelMap](arkts-image-image-pixelmap-i.md)&gt; | Promise used to return the PixelMap object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7600201](../errorcode-image.md#7600201-unsupported-operation) | The PixelMap has been released. |
| [7600204](../errorcode-image.md#7600204-invalid-region) | Invalid region. |
| [7600205](../errorcode-image.md#7600205-unsupported-format) | Unsupported memory format or pixel format. |
| [7600301](../errorcode-image.md#7600301-memory-allocation-failure) | Memory alloc failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function createCroppedAndScaledPixelMap(pixelMap: image.PixelMap) {
  const imageInfo = pixelMap.getImageInfoSync();
  const region: image.Region = {
    size: { width: imageInfo.size.width / 2, height: imageInfo.size.height / 2 },
    x: imageInfo.size.width / 4,
    y: imageInfo.size.height / 4
  };
  const scaleX: number = 2.0;
  const scaleY: number = 2.0;
  pixelMap.createCroppedAndScaledPixelMap(region, scaleX, scaleY, image.AntiAliasingLevel.HIGH)
    .then((croppedAndScaled: image.PixelMap) => {
      console.info('Succeeded in creating cropped and scaled PixelMap.');
    })
    .catch((err: BusinessError) => {
      console.error(`Failed to create cropped and scaled PixelMap. Code: ${err.code}, message: ${err.message}`);
    });
}
```

## createCroppedAndScaledPixelMapSync

```TypeScript
createCroppedAndScaledPixelMapSync(region: Region, x: number, y: number, level?: AntiAliasingLevel): PixelMap
```

Creates an image that has been cropped and resized based on the specified cropping area, scale factors of the width and height, and anti-aliasing level. This API returns the result synchronously.

**Since:** 22

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| region | [Region](arkts-image-image-region-i.md) | Yes | Area to crop. It must be within the original image's dimension (in pixels). |
| x | number | Yes | Scale factor of the width. It must not be **0**. |
| y | number | Yes | Scale factor of the height. It must not be **0**. |
| level | [AntiAliasingLevel](arkts-image-image-antialiasinglevel-e.md) | No | Anti-aliasing level. Default value: **NONE**. |

**Return value:**

| Type | Description |
| --- | --- |
| [PixelMap](arkts-image-image-pixelmap-i.md) | PixelMap object. If the operation fails, an error is thrown. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7600201](../errorcode-image.md#7600201-unsupported-operation) | The PixelMap has been released. |
| [7600204](../errorcode-image.md#7600204-invalid-region) | Invalid region. |
| [7600205](../errorcode-image.md#7600205-unsupported-format) | Unsupported memory format or pixel format. |
| [7600301](../errorcode-image.md#7600301-memory-allocation-failure) | Memory alloc failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function createCroppedAndScaledPixelMapSync(pixelMap: image.PixelMap) {
  const imageInfo = pixelMap.getImageInfoSync();
  const region: image.Region = {
    size: { width: imageInfo.size.width / 2, height: imageInfo.size.height / 2 },
    x: imageInfo.size.width / 4,
    y: imageInfo.size.height / 4
  };
  const scaleX: number = 2.0;
  const scaleY: number = 2.0;
  try {
    const croppedAndScaled = pixelMap.createCroppedAndScaledPixelMapSync(region, scaleX, scaleY, image.AntiAliasingLevel.HIGH);
    console.info('Succeeded in creating cropped and scaled PixelMap.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to create cropped and scaled PixelMap. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## createScaledPixelMap

```TypeScript
createScaledPixelMap(x: number, y: number, level?: AntiAliasingLevel): Promise<PixelMap>
```

Creates an image that has been resized based on the specified anti-aliasing level and the scale factors of the width and height. This API uses a promise to return the result.

**Since:** 18

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | Scale factor of the width. |
| y | number | Yes | Scale factor of the height. |
| level | [AntiAliasingLevel](arkts-image-image-antialiasinglevel-e.md) | No | Anti-aliasing level. The default value is **AntiAliasingLevel.NONE**. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[PixelMap](arkts-image-image-pixelmap-i.md)&gt; | Promise used to return the PixelMap object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../errorcode-image.md#501-api-call-failed) | The resource is unavailable as it is occupied by another thread. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function createScaledPixelMap(pixelMap: image.PixelMap) {
  const scaleX: number = 2.0;
  const scaleY: number = 1.0;
  pixelMap.createScaledPixelMap(scaleX, scaleY, image.AntiAliasingLevel.LOW).then((scaledPixelMap: image.PixelMap) => {
    console.info('Succeeded in creating scaled PixelMap.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to create scaled PixelMap. Code: ${err.code}, message: ${err.message}`);
  });
}
```

## createScaledPixelMapSync

```TypeScript
createScaledPixelMapSync(x: number, y: number, level?: AntiAliasingLevel): PixelMap
```

Creates an image that has been resized based on the specified anti-aliasing level and the scale factors of the width and height. This API returns the result synchronously.

**Since:** 18

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | Scale factor of the width. |
| y | number | Yes | Scale factor of the height. |
| level | [AntiAliasingLevel](arkts-image-image-antialiasinglevel-e.md) | No | Anti-aliasing level. The default value is **AntiAliasingLevel.NONE**. |

**Return value:**

| Type | Description |
| --- | --- |
| [PixelMap](arkts-image-image-pixelmap-i.md) | PixelMap object. If the operation fails, an error is thrown. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../errorcode-image.md#501-api-call-failed) | The resource is unavailable as it is occupied by another thread. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function createScaledPixelMapSync(pixelMap: image.PixelMap) {
  const scaleX: number = 2.0;
  const scaleY: number = 1.0;
  try {
    let scaledPixelMap = pixelMap.createScaledPixelMapSync(scaleX, scaleY, image.AntiAliasingLevel.LOW);
    console.info('Succeeded in creating scaled PixelMap.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to create scaled PixelMap. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## crop

```TypeScript
crop(region: Region, callback: AsyncCallback<void>): void
```

Crops this image based on a given size. This API uses an asynchronous callback to return the result.

Starting from API 26.0.0, it is recommended to use [applyCrop](#applycrop) instead for better exception handling capabilities.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| region | [Region](arkts-image-image-region-i.md) | Yes | Size of the image after cropping. The value cannot exceed the width or height of the image. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function crop(pixelMap: image.PixelMap) {
  const region: image.Region = { x: 0, y: 0, size: { height: 100, width: 100 } };
  pixelMap.crop(region, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to crop the PixelMap. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info("Succeeded in cropping the PixelMap.");
  });
}
```

<a id="crop-1"></a>

## crop

```TypeScript
crop(region: Region): Promise<void>
```

Crops a PixelMap based on a given size. This API uses a promise to return the result.

Starting from API 26.0.0, it is recommended to use [applyCrop](#applycrop) instead for better exception handling capabilities.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| region | [Region](arkts-image-image-region-i.md) | Yes | Size of the image after cropping. The value cannot exceed the width or height of the image. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function crop(pixelMap: image.PixelMap) {
  const region: image.Region = { x: 0, y: 0, size: { height: 100, width: 100 } };
  pixelMap.crop(region).then(() => {
    console.info('Succeeded in cropping the PixelMap.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to crop the PixelMap. Code: ${err.code}, message: ${err.message}`);
  });
}
```

## cropSync

```TypeScript
cropSync(region: Region): void
```

Crops this image based on a given size. This API returns the result synchronously.

Starting from API 26.0.0, it is recommended to use [applyCropSync](#applycropsync) instead for better exception handling capabilities.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| region | [Region](arkts-image-image-region-i.md) | Yes | Size of the image after cropping. The value cannot exceed the width or height of the image. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../errorcode-image.md#501-api-call-failed) | The resource is unavailable as it is occupied by another thread. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function cropSync(pixelMap: image.PixelMap) {
  const region: image.Region = { x: 0, y: 0, size: { height: 100, width: 100 } };
  try {
    pixelMap.cropSync(region);
    console.info('Succeeded in cropping the PixelMap.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to crop the PixelMap. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## extractAlphaPixelMap

```TypeScript
extractAlphaPixelMap(): Promise<PixelMap>
```

Extracts the alpha channel from the current PixelMap to create a new ALPHA_U8 format PixelMap.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Image.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[PixelMap](arkts-image-image-pixelmap-i.md)&gt; | A Promise of the new ALPHA_U8 format PixelMap. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7600104](../errorcode-image.md#7600104-failed-to-obtain-image-data) | Failed to get image data. Possible cause: Internal data is corrupted. Please check the logs for detailed information. |
| [7600105](../errorcode-image.md#7600105-pixelmap-object-has-been-released) | The current PixelMap has been released. |
| [7600106](../errorcode-image.md#7600106-pixelmap-has-been-passed-to-another-thread) | The current PixelMap has been passed across threads. |
| [7600305](../errorcode-image.md#7600305-failed-to-create-the-pixelmap) | Failed to create the PixelMap. Possible cause: Current PixelMap data is corrupted. |
| [7600306](../errorcode-image.md#7600306-data-conversion-failed) | Failed to convert the data. Possible causes: 1. Failed to perform pixel format conversion. 2. The system is out of memory. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function extractAlphaPixelMap(pixelMap: image.PixelMap) {
  pixelMap.extractAlphaPixelMap()
    .then((alphaMap: image.PixelMap) => {
      console.info('Succeeded in creating alpha PixelMap.');
    })
    .catch((err: BusinessError) => {
      console.error(`Failed to create alpha PixelMap. Code: ${err.code}, message: ${err.message}`);
    });
}
```

## extractAlphaPixelMapSync

```TypeScript
extractAlphaPixelMapSync(): PixelMap
```

Extracts the alpha channel from the current PixelMap to create a new ALPHA_U8 format PixelMap.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Image.Core

**Return value:**

| Type | Description |
| --- | --- |
| [PixelMap](arkts-image-image-pixelmap-i.md) | A new ALPHA_U8 format PixelMap. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7600104](../errorcode-image.md#7600104-failed-to-obtain-image-data) | Failed to get image data. Possible cause: Internal data is corrupted. Please check the logs for detailed information. |
| [7600105](../errorcode-image.md#7600105-pixelmap-object-has-been-released) | The current PixelMap has been released. |
| [7600106](../errorcode-image.md#7600106-pixelmap-has-been-passed-to-another-thread) | The current PixelMap has been passed across threads. |
| [7600305](../errorcode-image.md#7600305-failed-to-create-the-pixelmap) | Failed to create the PixelMap. Possible cause: Current PixelMap data is corrupted. |
| [7600306](../errorcode-image.md#7600306-data-conversion-failed) | Failed to convert the data. Possible causes: 1. Failed to perform pixel format conversion. 2. The system is out of memory. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function extractAlphaPixelMapSync(pixelMap: image.PixelMap) {
  try {
    const alphaMap = pixelMap.extractAlphaPixelMapSync();
    console.info('Succeeded in creating alpha PixelMap.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to create alpha PixelMap. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## flip

```TypeScript
flip(horizontal: boolean, vertical: boolean, callback: AsyncCallback<void>): void
```

Flips this image horizontally or vertically, or both. This API uses an asynchronous callback to return the result.

Starting from API 26.0.0, it is recommended to use [applyFlip](#applyflip) instead for better exception handling capabilities.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| horizontal | boolean | Yes | Whether to flip the image horizontally. **true** to flip the image horizontally, **false** otherwise. |
| vertical | boolean | Yes | Whether to flip the image vertically. **true** to flip the image vertically, **false** otherwise. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function flip(pixelMap: image.PixelMap) {
  const horizontal: boolean = true;
  const vertical: boolean = false;
  pixelMap.flip(horizontal, vertical, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to flip the PixelMap. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info("Succeeded in flipping the PixelMap.");
  });
}
```

<a id="flip-1"></a>

## flip

```TypeScript
flip(horizontal: boolean, vertical: boolean): Promise<void>
```

Flips a PixelMap based on a given angle. This API uses a promise to return the result.

Starting from API 26.0.0, it is recommended to use [applyFlip](#applyflip) instead for better exception handling capabilities.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| horizontal | boolean | Yes | Whether to flip the image horizontally. **true** to flip the image horizontally, **false** otherwise. |
| vertical | boolean | Yes | Whether to flip the image vertically. **true** to flip the image vertically, **false** otherwise. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function flip(pixelMap: image.PixelMap) {
  const horizontal: boolean = true;
  const vertical: boolean = false;
  pixelMap.flip(horizontal, vertical).then(() => {
    console.info('Succeeded in flipping the PixelMap.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to flip the PixelMap. Code: ${err.code}, message: ${err.message}`);
  });
}
```

## flipSync

```TypeScript
flipSync(horizontal: boolean, vertical: boolean): void
```

Flips this image horizontally or vertically, or both. This API returns the result synchronously.

Starting from API 26.0.0, it is recommended to use [applyFlipSync](#applyflipsync) instead for better exception handling capabilities.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| horizontal | boolean | Yes | Whether to flip the image horizontally. **true** to flip the image horizontally, **false** otherwise. |
| vertical | boolean | Yes | Whether to flip the image vertically. **true** to flip the image vertically, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../errorcode-image.md#501-api-call-failed) | The resource is unavailable as it is occupied by another thread. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function flipSync(pixelMap: image.PixelMap) {
  const horizontal: boolean = true;
  const vertical: boolean = false;
  try {
    pixelMap.flipSync(horizontal, vertical);
    console.info('Succeeded in flipping the PixelMap.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to flip the PixelMap. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## getBytesNumberPerRow

```TypeScript
getBytesNumberPerRow(): number
```

Obtains the number of bytes per row of this image. Unit: bytes.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core

**Return value:**

| Type | Description |
| --- | --- |
| number | Number of bytes per row. |

**Examples**

```TypeScript
function getBytesNumberPerRow(pixelMap: image.PixelMap) {
  let rowBytes: number = pixelMap.getBytesNumberPerRow();
}
```

## getColorSpace

```TypeScript
getColorSpace(): colorSpaceManager.ColorSpaceManager
```

Obtains the color space of this image.

**Since:** 10

**System capability:** SystemCapability.Multimedia.Image.Core

**Return value:**

| Type | Description |
| --- | --- |
| [colorSpaceManager.ColorSpaceManager](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-colorspacemanager-colorspacemanager-i.md) | Color space obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [62980101](../errorcode-image.md#62980101-incorrect-input-image-data) | The image data is abnormal. |
| [62980103](../errorcode-image.md#62980103-unsupported-image-type) | The image data is not supported. |
| [62980115](../errorcode-image.md#62980115-invalid-image-parameter) | Invalid image parameter. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function getColorSpace(pixelMap: image.PixelMap) {
  try {
    const csm = pixelMap.getColorSpace();
    console.info(`Succeeded in getting color space: ${csm.getColorSpaceName()}.`);
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to get color space. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## getDensity

```TypeScript
getDensity(): number
```

Obtains the pixel density of this image. Unit: ppi (pixels/inch)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core

**Return value:**

| Type | Description |
| --- | --- |
| number | Pixel density, in ppi. |

**Examples**

```TypeScript
function getDensity(pixelMap: image.PixelMap) {
  let density: number = pixelMap.getDensity();
}
```

## getImageInfo

```TypeScript
getImageInfo(): Promise<ImageInfo>
```

Obtains the image information of a PixelMap. This API uses a promise to return the result.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ImageInfo](arkts-image-image-imageinfo-i.md)&gt; | Promise used to return the image information. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function getImageInfo(pixelMap: image.PixelMap) {
  pixelMap.getImageInfo().then((imageInfo: image.ImageInfo) => {
    console.info(`Succeeded in obtaining information of the PixelMap with size ${imageInfo.size} and pixel format ${imageInfo.pixelFormat}.`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to obtain information of the PixelMap. Code: ${err.code}, message: ${err.message}`);
  });
}
```

<a id="getimageinfo-1"></a>

## getImageInfo

```TypeScript
getImageInfo(callback: AsyncCallback<ImageInfo>): void
```

Obtains the image information. This API uses an asynchronous callback to return the result.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[ImageInfo](arkts-image-image-imageinfo-i.md)&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the image information obtained; otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function getImageInfo(pixelMap: image.PixelMap) {
  pixelMap.getImageInfo((err: BusinessError, imageInfo: image.ImageInfo) => {
    if (err) {
      console.error(`Failed to obtain information of the PixelMap. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in obtaining information of the PixelMap with size ${imageInfo.size} and pixel format ${imageInfo.pixelFormat}.`);
  });
}
```

## getImageInfoSync

```TypeScript
getImageInfoSync(): ImageInfo
```

Obtains the image information. This API returns the result synchronously.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.ImageSource

**Return value:**

| Type | Description |
| --- | --- |
| [ImageInfo](arkts-image-image-imageinfo-i.md) | Image information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [501](../errorcode-image.md#501-api-call-failed) | The resource is unavailable as it is occupied by another thread. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function getImageInfoSync(pixelMap: image.PixelMap) {
  try {
    let imageInfo: image.ImageInfo = pixelMap.getImageInfoSync();
    console.info(`Succeeded in obtaining information of the PixelMap with size ${imageInfo.size} and pixel format ${imageInfo.pixelFormat}.`);
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to obtain information of the PixelMap. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## getMetadata

```TypeScript
getMetadata(key: HdrMetadataKey): HdrMetadataValue
```

Obtains the value of the metadata with a given key in this PixelMap.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | [HdrMetadataKey](arkts-image-image-hdrmetadatakey-e.md) | Yes | Key of the HDR metadata. |

**Return value:**

| Type | Description |
| --- | --- |
| [HdrMetadataValue](arkts-image-image-hdrmetadatavalue-t.md) | Value of the metadata with the given key. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../errorcode-image.md#501-api-call-failed) | The resource is unavailable as it is occupied by another thread. |
| [62980173](../errorcode-image.md#62980173-dma-memory-space-error) | The DMA memory does not exist. |
| [62980302](../errorcode-image.md#62980302-memory-copy-failed) | Memory copy failed. Possibly caused by invalid metadata value. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function getMetadata(context: Context) {
  // Replace app.media.startIcon with a local HDR image.
  let img = context.resourceManager.getMediaContentSync($r('app.media.startIcon').id);
  let imageSource = image.createImageSource(img.buffer.slice(0));
  let decodingOptions: image.DecodingOptions = {
    desiredDynamicRange: image.DecodingDynamicRange.AUTO
  };
  let pixelMap = imageSource.createPixelMapSync(decodingOptions);
  if (pixelMap != undefined) {
    console.info('Succeeded in creating the PixelMap object.');
    try {
      let staticMetadata = pixelMap.getMetadata(image.HdrMetadataKey.HDR_STATIC_METADATA);
      console.info('Succeeded in getting the metadata.');
    } catch (e) {
      const err = e as BusinessError;
      console.error(`Failed to get the metadata. Code: ${err.code}, message: ${err.message}`);
    }
  } else {
    console.error('Failed to create the PixelMap.');
  }
}
```

## getPixelBytesNumber

```TypeScript
getPixelBytesNumber(): number
```

Obtains the total number of bytes of this image. Unit: bytes.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core

**Return value:**

| Type | Description |
| --- | --- |
| number | Total number of bytes. |

**Examples**

```TypeScript
function getPixelBytesNumber(pixelMap: image.PixelMap) {
  let pixelBytesNumber: number = pixelMap.getPixelBytesNumber();
}
```

## getUniqueId

```TypeScript
getUniqueId(): number
```

Obtains the unique ID of this PixelMap.

**Since:** 22

**System capability:** SystemCapability.Multimedia.Image.Core

**Return value:**

| Type | Description |
| --- | --- |
| number | Unique ID. The value is a positive integer. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7600201](../errorcode-image.md#7600201-unsupported-operation) | The PixelMap has been released. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function getUniqueId(pixelMap: image.PixelMap) {
  try {
    const uniqueId: number = pixelMap.getUniqueId();
    console.info(`Succeeded in getting the unique ID: ${uniqueId}.`);
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to get the unique ID. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## isReleased

```TypeScript
isReleased(): boolean
```

Checks whether this PixelMap object is released. If released, any attempt to access the internal data of this object will fail.

> **NOTE:** 
> 
> Release occurs when an ArkTS object relinquishes control over its associated native object. The memory occupied
> by the native object is reclaimed only after all managing ArkTS objects have relinquished their control.

**Since:** 22

**System capability:** SystemCapability.Multimedia.Image.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result for whether the PixelMap object is released. **true** if released; **false** otherwise. |

**Examples**

## marshalling

```TypeScript
marshalling(sequence: rpc.MessageSequence): void
```

Marshals this PixelMap object and writes it to a MessageSequence object.

**Since:** 10

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sequence | [rpc.MessageSequence](../../apis-ipc-kit/arkts-apis/arkts-ipc-rpc-messagesequence-c.md) | Yes | MessageSequence object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [62980115](../errorcode-image.md#62980115-invalid-image-parameter) | Invalid image parameter. |
| [62980097](../errorcode-image.md#62980097-pixelmap-serialization-failed) | IPC error. Possible cause: 1.IPC communication failed. 2. Image upload exception. 3. Decode process exception. 4. Insufficient memory. |

**Examples**

```TypeScript
// EntryAbility.ets
import { rpc } from '@kit.IPCKit';

class MySequence implements rpc.Parcelable {
  pixelMap: image.PixelMap;
  constructor(pixelMap: image.PixelMap) {
    this.pixelMap = pixelMap;
  }
  marshalling(messageSequence: rpc.MessageSequence) {
    this.pixelMap.marshalling(messageSequence);
    console.info('Marshalled the PixelMap.');
    return true;
  }
  unmarshalling(messageSequence: rpc.MessageSequence) {
    image.createPixelMap(new ArrayBuffer(96), {size: { height: 4, width: 6 }}).then((pixelParcel: image.PixelMap) => {
      pixelParcel.unmarshalling(messageSequence).then(async (pixelMap: image.PixelMap) => {
        this.pixelMap = pixelMap;
        pixelMap.getImageInfo().then((imageInfo: image.ImageInfo) => {
          console.info(`Unmarshalled information: height = ${imageInfo.size.height}, width = ${imageInfo.size.width}.`);
        });
      });
    });
    return true;
  }
}

async function marshal() {
  const color: ArrayBuffer = new ArrayBuffer(96);
  let bufferArr: Uint8Array = new Uint8Array(color);
  for (let i = 0; i < bufferArr.length; i++) {
    bufferArr[i] = 0x80;
  }
  let opts: image.InitializationOptions = {
    editable: true,
    pixelFormat: image.PixelMapFormat.BGRA_8888,
    size: { height: 4, width: 6 },
    alphaType: image.AlphaType.UNPREMUL
  };
  let pixelMap: image.PixelMap | undefined = undefined;
  await image.createPixelMap(color, opts).then((srcPixelMap: image.PixelMap) => {
    pixelMap = srcPixelMap;
  })
  if (pixelMap != undefined) {
    // Implement serialization.
    let parcelable: MySequence = new MySequence(pixelMap);
    let data: rpc.MessageSequence = rpc.MessageSequence.create();
    data.writeParcelable(parcelable);

    // Implement deserialization to obtain data through the RPC.
    let seq: MySequence = new MySequence(pixelMap);
    data.readParcelable(seq);
  }
}
```

## opacity

```TypeScript
opacity(rate: number, callback: AsyncCallback<void>): void
```

Sets an opacity rate for this image. This API uses an asynchronous callback to return the result. It is invalid for YUV images.

Starting from API 26.0.0, it is recommended to use [setOpacity](#setopacity) instead for better exception handling capabilities.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rate | number | Yes | Opacity rate. The value range is (0,1]. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function opacity(pixelMap: image.PixelMap) {
  const rate: number = 0.5;
  pixelMap.opacity(rate, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to set opacity. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info("Succeeded in setting opacity.");
  });
}
```

<a id="opacity-1"></a>

## opacity

```TypeScript
opacity(rate: number): Promise<void>
```

Sets an opacity rate for this image. It is invalid for YUV images. This API uses a promise to return the result.

Starting from API 26.0.0, it is recommended to use [setOpacity](#setopacity) instead for better exception handling capabilities.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rate | number | Yes | Opacity rate. The value range is (0,1]. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function opacity(pixelMap: image.PixelMap) {
  const rate: number = 0.5;
  pixelMap.opacity(rate).then(() => {
    console.info('Succeeded in setting opacity.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to set opacity. Code: ${err.code}, message: ${err.message}`);
  });
}
```

## opacitySync

```TypeScript
opacitySync(rate: number): void
```

Sets an opacity rate for this image. This API returns the result synchronously. It is invalid for YUV images.

Starting from API 26.0.0, it is recommended to use [setOpacitySync](#setopacitysync) instead for better exception handling capabilities.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rate | number | Yes | Opacity rate. The value range is (0,1]. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../errorcode-image.md#501-api-call-failed) | The resource is unavailable as it is occupied by another thread. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function opacitySync(pixelMap: image.PixelMap) {
  const rate: number = 0.5;
  try {
    pixelMap.opacitySync(rate);
    console.info('Succeeded in setting opacity.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to set opacity. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## readAllPixelsToBuffer

```TypeScript
readAllPixelsToBuffer(dst: ArrayBuffer): Promise<void>
```

Reads all the pixel data from the PixelMap and writes the data to a buffer. The resulting data will be in the same pixel format as the PixelMap.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| dst | ArrayBuffer | Yes | The buffer to receive the pixel data from the PixelMap. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | A Promise that resolves when the operation completes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7600104](../errorcode-image.md#7600104-failed-to-obtain-image-data) | Failed to get image data. Possible cause: Internal data is corrupted. Please check the logs for detailed information. |
| [7600105](../errorcode-image.md#7600105-pixelmap-object-has-been-released) | The PixelMap has been released. |
| [7600106](../errorcode-image.md#7600106-pixelmap-has-been-passed-to-another-thread) | The PixelMap has been passed to another thread. |
| [7600206](../errorcode-image.md#7600206-invalid-parameter) | Invalid parameter. Possible cause: Size of the buffer is too small. |
| [7600302](../errorcode-image.md#7600302-memory-copy-failure) | Failed to copy the memory. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function readAllPixelsToBuffer(pixelMap: image.PixelMap) {
  const readBuffer = new ArrayBuffer(pixelMap.getPixelBytesNumber());

  pixelMap.readAllPixelsToBuffer(readBuffer)
    .then(() => {
      console.info('Succeeded in reading pixel data from the PixelMap to readBuffer.');
    })
    .catch((err: BusinessError) => {
      console.error(`Failed to read pixel data. Code: ${err.code}, message: ${err.message}`);
    });
}
```

## readAllPixelsToBufferSync

```TypeScript
readAllPixelsToBufferSync(dst: ArrayBuffer): void
```

Reads all the pixel data from the PixelMap and writes the data to a buffer. The resulting data will be in the same pixel format as the PixelMap.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| dst | ArrayBuffer | Yes | The buffer to receive the pixel data from the PixelMap. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7600104](../errorcode-image.md#7600104-failed-to-obtain-image-data) | Failed to get image data. Possible cause: Internal data is corrupted. Please check the logs for detailed information. |
| [7600105](../errorcode-image.md#7600105-pixelmap-object-has-been-released) | The PixelMap has been released. |
| [7600106](../errorcode-image.md#7600106-pixelmap-has-been-passed-to-another-thread) | The PixelMap has been passed to another thread. |
| [7600206](../errorcode-image.md#7600206-invalid-parameter) | Invalid parameter. Possible cause: Size of the buffer is too small. |
| [7600302](../errorcode-image.md#7600302-memory-copy-failure) | Failed to copy the memory. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function readAllPixelsToBufferSync(pixelMap: image.PixelMap) {
  const readBuffer = new ArrayBuffer(pixelMap.getPixelBytesNumber());

  try {
    pixelMap.readAllPixelsToBufferSync(readBuffer);
    console.info('Succeeded in reading pixel data from the PixelMap to readBuffer.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to read pixel data. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## readPixels

```TypeScript
readPixels(area: PositionArea): Promise<void>
```

Reads the pixels in the area specified by [PositionArea](arkts-image-image-positionarea-i.md).region of this PixelMap object in the BGRA_8888 format and writes the data to the [PositionArea](arkts-image-image-positionarea-i.md).pixels buffer. This API uses a promise to return the result. You can use a formula to calculate the size of the memory to be applied for based on **PositionArea**. YUV region calculation formula: region to read (region.size{width * height}) * 1.5 (1 * Y component + 0.25 * U component + 0.25 * V component) RGBA region calculation formula: region to read (region.size{width * height}) * 4 (1 * R component + 1 * G component + 1 * B component + 1 * A component)

Starting from API 26.0.0, it is recommended to use [readPixelsToArea](#readpixelstoarea) instead for better exception handling capabilities.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| area | [PositionArea](arkts-image-image-positionarea-i.md) | Yes | Area from which the pixels will be read. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function readPixelsRGBA(pixelMap: image.PixelMap) {
  const area: image.PositionArea = {
    pixels: new ArrayBuffer(8), // 8 indicates the size of the pixel buffer to create. The value is calculated as follows: width × height × 4.
    offset: 0,
    stride: 8,
    region: { size: { height: 1, width: 2 }, x: 0, y: 0 }
  };
  pixelMap.readPixels(area).then(() => {
    console.info('Succeeded in reading the image data in the area from the specified area.');
    console.info('BGRA data: ', new Uint8Array(area.pixels));
  }).catch((err: BusinessError) => {
    console.error(`Failed to read the image data from the specified area. Code: ${err.code}, message: ${err.message}`);
  });
}

function readPixelsYUV(pixelMap: image.PixelMap) {
  const area: image.PositionArea = {
    pixels: new ArrayBuffer(6), // 6 indicates the size of the pixel buffer to create. The value is calculated as follows: width × height × 1.5.
    offset: 0,
    stride: 8,
    region: { size: { height: 2, width: 2 }, x: 0, y: 0 }
  };
  pixelMap.readPixels(area).then(() => {
    console.info('Succeeded in reading the image data in the area from the specified area.');
    console.info('YUV data: ', new Uint8Array(area.pixels));
  }).catch((err: BusinessError) => {
    console.error(`Failed to read the image data from the specified area. Code: ${err.code}, message: ${err.message}`);
  });
}
```

<a id="readpixels-1"></a>

## readPixels

```TypeScript
readPixels(area: PositionArea, callback: AsyncCallback<void>): void
```

Reads the pixels in the area specified by [PositionArea](arkts-image-image-positionarea-i.md).region of this PixelMap object in the BGRA_8888 format and writes the data to the [PositionArea](arkts-image-image-positionarea-i.md).pixels buffer. This API uses an asynchronous callback to return the result. You can use a formula to calculate the size of the memory to be applied for based on **PositionArea**. YUV region calculation formula: region to read (region.size{width * height}) * 1.5 (1 * Y component + 0.25 * U component + 0.25 * V component) RGBA region calculation formula: region to read (region.size{width * height}) * 4 (1 * R component + 1 * G component + 1 * B component + 1 * A component)

Starting from API 26.0.0, it is recommended to use [readPixelsToArea](#readpixelstoarea) instead for better exception handling capabilities.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| area | [PositionArea](arkts-image-image-positionarea-i.md) | Yes | Area from which the pixels will be read. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function readPixelsRGBA(pixelMap: image.PixelMap) {
  const area: image.PositionArea = {
    pixels: new ArrayBuffer(8), // 8 indicates the size of the pixel buffer to create. The value is calculated as follows: width × height × 4.
    offset: 0,
    stride: 8,
    region: { size: { height: 1, width: 2 }, x: 0, y: 0 }
  };
  pixelMap.readPixels(area, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to read the image data from the specified area. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in reading the image data from the specified area.');
    console.info('BGRA data: ', new Uint8Array(area.pixels));
  });
}

function readPixelsYUV(pixelMap: image.PixelMap) {
  const area: image.PositionArea = {
    pixels: new ArrayBuffer(6), // 6 indicates the size of the pixel buffer to create. The value is calculated as follows: width × height × 1.5.
    offset: 0,
    stride: 8,
    region: { size: { height: 2, width: 2 }, x: 0, y: 0 }
  };
  pixelMap.readPixels(area, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to read the image data from the specified area. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in reading the image data from the specified area.');
    console.info('YUV data: ', new Uint8Array(area.pixels));
  });
}
```

## readPixelsSync

```TypeScript
readPixelsSync(area: PositionArea): void
```

Reads the pixels in the area specified by [PositionArea](arkts-image-image-positionarea-i.md).region of this PixelMap object in the BGRA_8888 format and writes the data to the [PositionArea](arkts-image-image-positionarea-i.md).pixels buffer. This API returns the result synchronously.

Starting from API 26.0.0, it is recommended to use [readPixelsToAreaSync](#readpixelstoareasync) instead for better exception handling capabilities.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| area | [PositionArea](arkts-image-image-positionarea-i.md) | Yes | Area from which the pixels will be read. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../errorcode-image.md#501-api-call-failed) | The resource is unavailable as it is occupied by another thread. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function readPixelsSync(pixelMap: image.PixelMap) {
  const area: image.PositionArea = {
    pixels: new ArrayBuffer(8),
    offset: 0,
    stride: 8,
    region: { size: { height: 1, width: 2 }, x: 0, y: 0 }
  };
  try {
    pixelMap.readPixelsSync(area);
    console.info('Succeeded in reading the image data from the specified area.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to read the image data from the specified area. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## readPixelsToArea

```TypeScript
readPixelsToArea(area: PositionArea): Promise<void>
```

Reads pixel data from a certain area of the PixelMap to a buffer. The resulting data will be in BGRA_8888 format.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| area | [PositionArea](arkts-image-image-positionarea-i.md) | Yes | Area of the PixelMap to read the data. Data will be read from the PixelMap and copied into PositionArea.pixels. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | A Promise that resolves when the operation completes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7600104](../errorcode-image.md#7600104-failed-to-obtain-image-data) | Failed to get image data. Possible cause: Internal data is corrupted. Please check the logs for detailed information. |
| [7600105](../errorcode-image.md#7600105-pixelmap-object-has-been-released) | The PixelMap has been released. |
| [7600106](../errorcode-image.md#7600106-pixelmap-has-been-passed-to-another-thread) | The PixelMap has been passed to another thread. |
| [7600206](../errorcode-image.md#7600206-invalid-parameter) | Invalid parameter. Possible causes: 1. PositionArea.pixels is too small. 2. PositionArea.region is out of range. |
| [7600302](../errorcode-image.md#7600302-memory-copy-failure) | Failed to copy the memory. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function readPixelsToAreaRGBA(pixelMap: image.PixelMap) {
  const area: image.PositionArea = {
    pixels: new ArrayBuffer(24), // 24 indicates the size of the pixel buffer to create. The value is calculated as follows: width × height × 4.
    offset: 0,
    stride: 8, // Stride, that is, the number of bytes occupied by pixels in each row. If no padding byte is added at the end of a row, the value is width × 4.
    region: {
      size: { width: 2, height: 3 },
      x: 0,
      y: 0
    }
  };

  pixelMap.readPixelsToArea(area)
    .then(() => {
      console.info('Succeeded in reading pixel data from the specified area of the PixelMap to area.pixels.');
      console.info('BGRA data: ', new Uint8Array(area.pixels));
    })
    .catch((err: BusinessError) => {
      console.error(`Failed to read pixel data. Code: ${err.code}, message: ${err.message}`);
    });
}

function readPixelsToAreaYUV(pixelMap: image.PixelMap) {
  const area: image.PositionArea = {
    pixels: new ArrayBuffer(9), // 9 indicates the size of the pixel buffer to create. The value is calculated as follows: width × height × 1.5.
    offset: 0,
    stride: 2, // Stride, that is, the number of bytes occupied by pixels in each row. If no padding byte is added at the end of a row, the value is width × 1 (indicating 1 times the Y component).
    region: {
      size: { width: 2, height: 3 },
      x: 0,
      y: 0
    }
  };

  pixelMap.readPixelsToArea(area)
    .then(() => {
      console.info('Succeeded in reading pixel data from the specified area of the PixelMap to area.pixels.');
      console.info('YUV data: ', new Uint8Array(area.pixels));
    })
    .catch((err: BusinessError) => {
      console.error(`Failed to read pixel data. Code: ${err.code}, message: ${err.message}`);
    });
}
```

## readPixelsToAreaSync

```TypeScript
readPixelsToAreaSync(area: PositionArea): void
```

Reads pixel data from a certain area of the PixelMap to a buffer. The resulting data will be in BGRA_8888 format.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| area | [PositionArea](arkts-image-image-positionarea-i.md) | Yes | Area of the PixelMap to read the data. Data will be read from the PixelMap and copied into PositionArea.pixels. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7600104](../errorcode-image.md#7600104-failed-to-obtain-image-data) | Failed to get image data. Possible cause: Internal data is corrupted. Please check the logs for detailed information. |
| [7600105](../errorcode-image.md#7600105-pixelmap-object-has-been-released) | The PixelMap has been released. |
| [7600106](../errorcode-image.md#7600106-pixelmap-has-been-passed-to-another-thread) | The PixelMap has been passed to another thread. |
| [7600206](../errorcode-image.md#7600206-invalid-parameter) | Invalid parameter. Possible causes: 1. PositionArea.pixels is too small. 2. PositionArea.region is out of range. |
| [7600302](../errorcode-image.md#7600302-memory-copy-failure) | Failed to copy the memory. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function readPixelsToAreaSyncRGBA(pixelMap: image.PixelMap) {
  const area: image.PositionArea = {
    pixels: new ArrayBuffer(24), // 24 indicates the size of the pixel buffer to create. The value is calculated as follows: width × height × 4.
    offset: 0,
    stride: 8, // Stride, that is, the number of bytes occupied by pixels in each row. If no padding byte is added at the end of a row, the value is width × 4.
    region: {
      size: { width: 2, height: 3 },
      x: 0,
      y: 0
    }
  };

  try {
    pixelMap.readPixelsToAreaSync(area);
    console.info('Succeeded in reading pixel data from the specified area of the PixelMap to area.pixels.');
    console.info('BGRA data: ', new Uint8Array(area.pixels));
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to read pixel data. Code: ${err.code}, message: ${err.message}`);
  }
}

function readPixelsToAreaSyncYUV(pixelMap: image.PixelMap) {
  const area: image.PositionArea = {
    pixels: new ArrayBuffer(9), // 9 indicates the size of the pixel buffer to create. The value is calculated as follows: width × height × 1.5.
    offset: 0,
    stride: 2, // Stride, that is, the number of bytes occupied by pixels in each row. If no padding byte is added at the end of a row, the value is width × 1 (indicating 1 times the Y component).
    region: {
      size: { width: 2, height: 3 },
      x: 0,
      y: 0
    }
  };

  try {
    pixelMap.readPixelsToAreaSync(area);
    console.info('Succeeded in reading pixel data from the specified area of the PixelMap to area.pixels.');
    console.info('YUV data: ', new Uint8Array(area.pixels));
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to read pixel data. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## readPixelsToBuffer

```TypeScript
readPixelsToBuffer(dst: ArrayBuffer): Promise<void>
```

Reads the pixels of this PixelMap object based on the PixelMap's pixel format and writes the data to the buffer. This API uses a promise to return the result.

Starting from API 26.0.0, it is recommended to use [readAllPixelsToBuffer](#readallpixelstobuffer) instead for better exception handling capabilities.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| dst | ArrayBuffer | Yes | Buffer to which the pixels will be written. The buffer size is obtained by calling [getPixelBytesNumber](#getpixelbytesnumber). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function readPixelsToBuffer(pixelMap: image.PixelMap) {
  const readBuffer: ArrayBuffer = new ArrayBuffer(pixelMap.getPixelBytesNumber());
  pixelMap.readPixelsToBuffer(readBuffer).then(() => {
    console.info('Succeeded in reading image pixel data.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to read image pixel data. Code: ${err.code}, message: ${err.message}`);
  });
}
```

<a id="readpixelstobuffer-1"></a>

## readPixelsToBuffer

```TypeScript
readPixelsToBuffer(dst: ArrayBuffer, callback: AsyncCallback<void>): void
```

Reads the pixels of this PixelMap object based on the PixelMap's pixel format and writes the data to the buffer. This API uses an asynchronous callback to return the result.

Starting from API 26.0.0, it is recommended to use [readAllPixelsToBuffer](#readallpixelstobuffer) instead for better exception handling capabilities.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| dst | ArrayBuffer | Yes | Buffer to which the pixels will be written. The buffer size is obtained by calling [getPixelBytesNumber](#getpixelbytesnumber). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function readPixelsToBuffer(pixelMap: image.PixelMap) {
  const readBuffer: ArrayBuffer = new ArrayBuffer(pixelMap.getPixelBytesNumber());
  pixelMap.readPixelsToBuffer(readBuffer, (err: BusinessError, res: void) => {
    if (err) {
      console.error(`Failed to read image pixel data. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in reading image pixel data.');
  });
}
```

## readPixelsToBufferSync

```TypeScript
readPixelsToBufferSync(dst: ArrayBuffer): void
```

Reads the pixels of this PixelMap object based on the PixelMap's pixel format and writes the data to the buffer. This API returns the result synchronously.

Starting from API 26.0.0, it is recommended to use [readAllPixelsToBufferSync](#readallpixelstobuffersync) instead for better exception handling capabilities.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| dst | ArrayBuffer | Yes | Buffer to which the pixels will be written. The buffer size is obtained by calling [getPixelBytesNumber](#getpixelbytesnumber). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../errorcode-image.md#501-api-call-failed) | The resource is unavailable as it is occupied by another thread. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function readPixelsToBufferSync(pixelMap: image.PixelMap) {
  const readBuffer = new ArrayBuffer(pixelMap.getPixelBytesNumber());
  try {
    pixelMap.readPixelsToBufferSync(readBuffer);
    console.info('Succeeded in reading image pixel data.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to read image pixel data. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## release

```TypeScript
release(callback: AsyncCallback<void>): void
```

Releases this PixelMap instance. After the release, any attempt to access the internal data of this object will fail. This API uses an asynchronous callback to return the result. Images occupy a large amount of memory. When you finish using a PixelMap instance, call this API to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

> **NOTE:** 
> 
> Release occurs when an ArkTS object relinquishes control over its associated native object. The memory occupied
> by the native object is reclaimed only after all managing ArkTS objects have relinquished their control.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function release(pixelMap: image.PixelMap) {
  pixelMap.release((err: BusinessError) => {
    if (err) {
      console.error(`Failed to release the PixelMap object. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in releasing the PixelMap object.');
  });
}
```

<a id="release-1"></a>

## release

```TypeScript
release(): Promise<void>
```

Releases this PixelMap instance. After the release, any attempt to access the internal data of this object will fail. This API uses a promise to return the result. Images occupy a large amount of memory. When you finish using a PixelMap instance, call this API to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

> **NOTE:** 
> 
> Release occurs when an ArkTS object relinquishes control over its associated native object. The memory occupied
> by the native object is reclaimed only after all managing ArkTS objects have relinquished their control.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function release(pixelMap: image.PixelMap) {
  pixelMap.release().then(() => {
    console.info('Succeeded in releasing the PixelMap object.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to release the PixelMap object. Code: ${err.code}, message: ${err.message}`);
  });
}
```

## rotate

```TypeScript
rotate(angle: number, callback: AsyncCallback<void>): void
```

Rotates this image based on a given angle. This API uses an asynchronous callback to return the result.

Starting from API 26.0.0, it is recommended to use [applyRotate](#applyrotate) instead for better exception handling capabilities.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| angle | number | Yes | Angle to rotate. Unit: degrees. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function rotate(pixelMap: image.PixelMap) {
  const angle: number = 90.0;
  pixelMap.rotate(angle, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to rotate the PixelMap. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info("Succeeded in rotating the PixelMap.");
  });
}
```

<a id="rotate-1"></a>

## rotate

```TypeScript
rotate(angle: number): Promise<void>
```

Rotates a PixelMap based on a given angle. This API uses a promise to return the result.

Starting from API 26.0.0, it is recommended to use [applyRotate](#applyrotate) instead for better exception handling capabilities.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| angle | number | Yes | Angle to rotate. Unit: degrees. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function rotate(pixelMap: image.PixelMap) {
  const angle: number = 90.0;
  pixelMap.rotate(angle).then(() => {
    console.info('Succeeded in rotating the PixelMap.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to rotate the PixelMap. Code: ${err.code}, message: ${err.message}`);
  });
}
```

## rotateSync

```TypeScript
rotateSync(angle: number): void
```

Rotates this image based on a given angle. This API returns the result synchronously.

Starting from API 26.0.0, it is recommended to use [applyRotateSync](#applyrotatesync) instead for better exception handling capabilities.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| angle | number | Yes | Angle to rotate. Unit: degrees. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../errorcode-image.md#501-api-call-failed) | The resource is unavailable as it is occupied by another thread. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function rotateSync(pixelMap: image.PixelMap) {
  const angle: number = 90.0;
  try {
    pixelMap.rotateSync(angle);
    console.info('Succeeded in rotating the PixelMap.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to rotate the PixelMap. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## scale

```TypeScript
scale(x: number, y: number, callback: AsyncCallback<void>): void
```

Scales this image based on the scale factors of the width and height. This API uses an asynchronous callback to return the result.

Starting from API 26.0.0, it is recommended to use [applyScale](#applyscale) instead for better exception handling capabilities.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | Scale factor of the width. |
| y | number | Yes | Scale factor of the height. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function scale(pixelMap: image.PixelMap) {
  const scaleX: number = 2.0;
  const scaleY: number = 1.0;
  pixelMap.scale(scaleX, scaleY, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to scale the PixelMap. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info("Succeeded in scaling the PixelMap.");
  });
}
```

<a id="scale-1"></a>

## scale

```TypeScript
scale(x: number, y: number): Promise<void>
```

Scales this image based on the scale factors of the width and height. This API uses a promise to return the result.

Starting from API 26.0.0, it is recommended to use [applyScale](#applyscale) instead for better exception handling capabilities.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | Scale factor of the width. |
| y | number | Yes | Scale factor of the height. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function scale(pixelMap: image.PixelMap) {
  const scaleX: number = 2.0;
  const scaleY: number = 1.0;
  pixelMap.scale(scaleX, scaleY).then(() => {
    console.info('Succeeded in scaling the PixelMap.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to scale the PixelMap. Code: ${err.code}, message: ${err.message}`);
  });
}
```

<a id="scale-2"></a>

## scale

```TypeScript
scale(x: number, y: number, level: AntiAliasingLevel): Promise<void>
```

Scales this image based on the specified anti-aliasing level and the scale factors for the width and height. This API uses a promise to return the result.

Starting from API 26.0.0, it is recommended to use [applyScale](#applyscale) instead for better exception handling capabilities.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | Scale factor of the width. |
| y | number | Yes | Scale factor of the height. |
| level | [AntiAliasingLevel](arkts-image-image-antialiasinglevel-e.md) | Yes | Anti-aliasing level. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../errorcode-image.md#501-api-call-failed) | The resource is unavailable as it is occupied by another thread. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function scaleSync(pixelMap: image.PixelMap) {
  const scaleX: number = 2.0;
  const scaleY: number = 1.0;
  pixelMap.scale(scaleX, scaleY, image.AntiAliasingLevel.LOW).then(() => {
    console.info('Succeeded in scaling the PixelMap.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to scale the PixelMap. Code: ${err.code}, message: ${err.message}`);
  });
}
```

## scaleSync

```TypeScript
scaleSync(x: number, y: number): void
```

Scales this image based on the scale factors of the width and height. This API returns the result synchronously.

Starting from API 26.0.0, it is recommended to use [applyScaleSync](#applyscalesync) instead for better exception handling capabilities.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | Scale factor of the width. |
| y | number | Yes | Scale factor of the height. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../errorcode-image.md#501-api-call-failed) | The resource is unavailable as it is occupied by another thread. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function scaleSync(pixelMap: image.PixelMap) {
  const scaleX: number = 2.0;
  const scaleY: number = 1.0;
  try {
    pixelMap.scaleSync(scaleX, scaleY);
    console.info('Succeeded in scaling the PixelMap.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to scale the PixelMap. Code: ${err.code}, message: ${err.message}`);
  }
}
```

<a id="scalesync-1"></a>

## scaleSync

```TypeScript
scaleSync(x: number, y: number, level: AntiAliasingLevel): void
```

Scales this image based on the specified anti-aliasing level and the scale factors for the width and height. This API returns the result synchronously.

Starting from API 26.0.0, it is recommended to use [applyScaleSync](#applyscalesync) instead for better exception handling capabilities.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | Scale factor of the width. |
| y | number | Yes | Scale factor of the height. |
| level | [AntiAliasingLevel](arkts-image-image-antialiasinglevel-e.md) | Yes | Anti-aliasing level. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../errorcode-image.md#501-api-call-failed) | The resource is unavailable as it is occupied by another thread. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function scaleSync(pixelMap: image.PixelMap) {
  const scaleX: number = 2.0;
  const scaleY: number = 1.0;
  try {
    pixelMap.scaleSync(scaleX, scaleY, image.AntiAliasingLevel.LOW);
    console.info('Succeeded in scaling the PixelMap.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to scale the PixelMap. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## setColorSpace

```TypeScript
setColorSpace(colorSpace: colorSpaceManager.ColorSpaceManager): void
```

Set color space of pixel map.

This method is only used to set the colorspace property of pixelmap, while all pixel data remains the same after calling this method. If you want to change colorspace for all pixels, use method {@Link #applyColorSpace(colorSpaceManager.ColorSpaceManager)} or {@Link #applyColorSpace(colorSpaceManager.ColorSpaceManager, AsyncCallback&lt;void&gt;)}.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| colorSpace | [colorSpaceManager.ColorSpaceManager](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-colorspacemanager-colorspacemanager-i.md) | Yes | The color space for pixel map. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [62980111](../errorcode-image.md#62980111-incomplete-image-source-data) | The image source data is incomplete. |
| [62980115](../errorcode-image.md#62980115-invalid-image-parameter) | If the image parameter invalid. |

**Examples**

```TypeScript
import { colorSpaceManager } from '@kit.ArkGraphics2D';
import { BusinessError } from '@kit.BasicServicesKit';

function setColorSpace(pixelMap: image.PixelMap) {
  const colorSpaceName = colorSpaceManager.ColorSpace.SRGB;
  const csm: colorSpaceManager.ColorSpaceManager = colorSpaceManager.create(colorSpaceName);
  try {
    pixelMap.setColorSpace(csm);
    console.info('Succeeded in setting color space.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to set color space. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## setMemoryNameSync

```TypeScript
setMemoryNameSync(name: string): void
```

Sets a memory name for this PixelMap.

**Since:** 13

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Memory name, which can be set only for a PixelMap with the DMA or ASHMEM memory format. The name length for DMA memory settings should be within the range of 1 to 255 bytes. For ASHMEM memory settings, the name length should be within the range of 1 to 244 bytes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.The length of the input parameter is too long. 2.Parameter verification failed. |
| [501](../errorcode-image.md#501-api-call-failed) | The resource is unavailable as it is occupied by another thread. |
| [62980286](../errorcode-image.md#62980286-failed-to-set-a-memory-identifier-for-a-pixelmap) | Memory format not supported. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function setMemoryNameSync(pixelMap: image.PixelMap) {
  try {
    pixelMap.setMemoryNameSync("PixelMapName Test");
    console.info('Succeeded in setting memory name.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to set memory name. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## setMetadata

```TypeScript
setMetadata(key: HdrMetadataKey, value: HdrMetadataValue): Promise<void>
```

Sets the value for the metadata with a given key in this PixelMap. This API uses a promise to return the result.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | [HdrMetadataKey](arkts-image-image-hdrmetadatakey-e.md) | Yes | Key of the HDR metadata. |
| value | [HdrMetadataValue](arkts-image-image-hdrmetadatavalue-t.md) | Yes | Value of the metadata. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../errorcode-image.md#501-api-call-failed) | The resource is unavailable as it is occupied by another thread. |
| [62980173](../errorcode-image.md#62980173-dma-memory-space-error) | The DMA memory does not exist. |
| [62980302](../errorcode-image.md#62980302-memory-copy-failed) | Memory copy failed. Possibly caused by invalid metadata value. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function setMetadata(pixelMap: image.PixelMap) { // The input parameter pixelMap must be of the DMA_ALLOC memory type. For details about how to create a PixelMap with DMA_ALLOC memory, see the preceding link.
  let staticMetadata: image.HdrStaticMetadata = {
    displayPrimariesX: [1.1, 1.1, 1.1],
    displayPrimariesY: [1.2, 1.2, 1.2],
    whitePointX: 1.1,
    whitePointY: 1.2,
    maxLuminance: 2.1,
    minLuminance: 1.0,
    maxContentLightLevel: 2.1,
    maxFrameAverageLightLevel: 2.1,
  };
  pixelMap.setMetadata(image.HdrMetadataKey.HDR_STATIC_METADATA, staticMetadata).then(() => {
    console.info('Succeeded in setting the metadata.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to set the metadata. Code: ${err.code}, message: ${err.message}`);
  });
}
```

## setOpacity

```TypeScript
setOpacity(value: number): Promise<void>
```

Sets opacity of the PixelMap. Every pixel will be set to the same opacity value.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | The target opacity value to be set. Unit: Percentage, Value range: (0,1]. The valid range is (0.0, 1.0] where 1.0 is fully opaque and becoming transparent as it approaches 0.0. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | A Promise that resolves when the operation completes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7600104](../errorcode-image.md#7600104-failed-to-obtain-image-data) | Failed to get image data. Possible cause: Internal data is corrupted. Please check the logs for detailed information. |
| [7600105](../errorcode-image.md#7600105-pixelmap-object-has-been-released) | The PixelMap has been released. |
| [7600106](../errorcode-image.md#7600106-pixelmap-has-been-passed-to-another-thread) | The PixelMap has been passed to another thread. |
| [7600201](../errorcode-image.md#7600201-unsupported-operation) | Unsupported operation because the PixelMap is locked. |
| [7600206](../errorcode-image.md#7600206-invalid-parameter) | Invalid parameter. Possible cause: The specified value is out of range. |
| [7600207](../errorcode-image.md#7600207-unsupported-data-format) | Unsupported data format. Possible cause: Alpha type is not supported. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function setOpacity(pixelMap: image.PixelMap) {
  const opacity: number = 0.5;
  pixelMap.setOpacity(opacity)
    .then(() => {
      console.info('Succeeded in setting opacity.');
    })
    .catch((err: BusinessError) => {
      console.error(`Failed to set opacity. Code: ${err.code}, message: ${err.message}`);
    });
}
```

## setOpacitySync

```TypeScript
setOpacitySync(value: number): void
```

Sets opacity of the PixelMap. Every pixel will be set to the same opacity value.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | The target opacity value to be set. Unit: Percentage, Value range: (0,1]. The valid range is (0.0, 1.0] where 1.0 is fully opaque and becoming transparent as it approaches 0.0. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7600104](../errorcode-image.md#7600104-failed-to-obtain-image-data) | Failed to get image data. Possible cause: Internal data is corrupted. Please check the logs for detailed information. |
| [7600105](../errorcode-image.md#7600105-pixelmap-object-has-been-released) | The PixelMap has been released. |
| [7600106](../errorcode-image.md#7600106-pixelmap-has-been-passed-to-another-thread) | The PixelMap has been passed to another thread. |
| [7600201](../errorcode-image.md#7600201-unsupported-operation) | Unsupported operation because the PixelMap is locked. |
| [7600206](../errorcode-image.md#7600206-invalid-parameter) | Invalid parameter. Possible cause: The specified value is out of range. |
| [7600207](../errorcode-image.md#7600207-unsupported-data-format) | Unsupported data format. Possible cause: Alpha type is not supported. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function setOpacitySync(pixelMap: image.PixelMap) {
  const opacity: number = 0.5;
  try {
    pixelMap.setOpacitySync(opacity);
    console.info('Succeeded in setting opacity.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to set opacity. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## setTransferDetached

```TypeScript
setTransferDetached(detached: boolean): void
```

Sets whether to detach from the original thread when this PixelMap is transmitted across threads. This API applies to the scenario where the PixelMap needs to be released immediately.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| detached | boolean | Yes | Whether to detach from the original thread. **true** to detach, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [501](../errorcode-image.md#501-api-call-failed) | The resource is unavailable as it is occupied by another thread. |

**Examples**

```TypeScript
// EntryAbility.ets
import { common } from '@kit.AbilityKit';
import { taskpool } from '@kit.ArkTS';

@Concurrent
// Child thread method.
async function loadPixelMap(rawFileDescriptor: number): Promise<image.PixelMap> {
  // Create an ImageSource.
  const imageSource = image.createImageSource(rawFileDescriptor);
  // Create a PixelMap.
  const pixelMap = imageSource.createPixelMapSync();
  // Release the ImageSource.
  imageSource.release();
  // Makes the PixelMap detach from the original thread reference after cross-thread transfer is complete.
  pixelMap.setTransferDetached(true);
  // Return the PixelMap to the main thread.
  return pixelMap;
}

@Entry
@Component
struct Demo {
  @State pixelMap: image.PixelMap | undefined = undefined;
  // Main thread method.
  private loadImageFromThread(): void {
    let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
    const resourceMgr = context.resourceManager;
    // 'example.jpg' is only an example. Replace it with the actual one in use. Otherwise, the creation fails, and subsequent operations cannot be performed.
    resourceMgr.getRawFd('example.jpg').then(rawFileDescriptor => {
      taskpool.execute(loadPixelMap, rawFileDescriptor).then(pixelMap => {
        if (pixelMap) {
          this.pixelMap = pixelMap as image.PixelMap;
          console.info('Succeeded in creating the PixelMap.');
          // The main thread releases the pixel map. Since setTransferDetached(true) has been called before the child thread returns the PixelMap, the PixelMap can be released immediately without waiting for the child thread to be destroyed.
          this.pixelMap.release();
        } else {
          console.error('Failed to create the PixelMap.');
        }
      });
    });
  }
  build() {
    // ...
  }
}
```

## toSdr

```TypeScript
toSdr(): Promise<void>
```

Convert pixelmap to standard dynamic range.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | A Promise instance used to return the operation result. If the operation fails, an error message is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [62980137](../errorcode-image.md#62980137-invalid-image-operation) | Invalid image operation. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function toSdr(context: Context) {
  // Replace app.media.startIcon with a local HDR image.
  let img = context.resourceManager.getMediaContentSync($r('app.media.startIcon').id);
  let imageSource = image.createImageSource(img.buffer.slice(0));
  let decodingOptions: image.DecodingOptions = {
    desiredDynamicRange: image.DecodingDynamicRange.AUTO
  };
  let pixelmap = imageSource.createPixelMapSync(decodingOptions);
  if (pixelmap != undefined) {
    console.info('Succeeded in creating the PixelMap object.');
    pixelmap.toSdr().then(() => {
      let imageInfo = pixelmap.getImageInfoSync();
      console.info("Succeeded in converting to SDR. imageInfo.isHdr: " + imageInfo.isHdr);
    }).catch((err: BusinessError) => {
      console.error(`Failed to convert to SDR. Code: ${err.code}, message: ${err.message}`);
    });
  } else {
    console.error('Failed to create the PixelMap.');
  }
}
```

## translate

```TypeScript
translate(x: number, y: number, callback: AsyncCallback<void>): void
```

Translates this image based on given coordinates. This API uses an asynchronous callback to return the result. The size of the translated image is changed to width+X and height+Y. It is recommended that the new width and height not exceed the width and height of the screen.

Starting from API 26.0.0, it is recommended to use [applyTranslate](#applytranslate) instead for better exception handling capabilities.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | X coordinate to translate, in px. |
| y | number | Yes | Y coordinate to translate, in px. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function translate(pixelMap: image.PixelMap) {
  const translateX: number = 50.0;
  const translateY: number = 10.0;
  pixelMap.translate(translateX, translateY, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to translate the PixelMap. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info("Succeeded in translating the PixelMap.");
  });
}
```

<a id="translate-1"></a>

## translate

```TypeScript
translate(x: number, y: number): Promise<void>
```

Translates a PixelMap based on given coordinates. This API uses a promise to return the result. The size of the translated image is changed to width+X and height+Y. It is recommended that the new width and height not exceed the width and height of the screen.

Starting from API 26.0.0, it is recommended to use [applyTranslate](#applytranslate) instead for better exception handling capabilities.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | X coordinate to translate, in px. |
| y | number | Yes | Y coordinate to translate, in px. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function translate(pixelMap: image.PixelMap) {
  const translateX: number = 50.0;
  const translateY: number = 10.0;
  pixelMap.translate(translateX, translateY).then(() => {
    console.info('Succeeded in translating the PixelMap.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to translate the PixelMap. Code: ${err.code}, message: ${err.message}`);
  });
}
```

## translateSync

```TypeScript
translateSync(x: number, y: number): void
```

Translates this image based on given coordinates. This API returns the result synchronously. The size of the translated image is changed to width+X and height+Y. It is recommended that the new width and height not exceed the width and height of the screen.

Starting from API 26.0.0, it is recommended to use [applyTranslateSync](#applytranslatesync) instead for better exception handling capabilities.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | X coordinate to translate, in px. |
| y | number | Yes | Y coordinate to translate, in px. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../errorcode-image.md#501-api-call-failed) | The resource is unavailable as it is occupied by another thread. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function translateSync(pixelMap: image.PixelMap) {
  const translateX: number = 50.0;
  const translateY: number = 10.0;
  try {
    pixelMap.translateSync(translateX, translateY);
    console.info('Succeeded in translating the PixelMap.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to translate the PixelMap. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## unmarshalling

```TypeScript
unmarshalling(sequence: rpc.MessageSequence): Promise<PixelMap>
```

Unmarshals a MessageSequence object to obtain a PixelMap object. To create a PixelMap object in synchronous mode, use [createPixelMapFromParcel](arkts-image-image-createpixelmapfromparcel-f.md).

**Since:** 10

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sequence | [rpc.MessageSequence](../../apis-ipc-kit/arkts-apis/arkts-ipc-rpc-messagesequence-c.md) | Yes | MessageSequence object that stores the PixelMap information. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[PixelMap](arkts-image-image-pixelmap-i.md)&gt; | Promise used to return the PixelMap object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [62980115](../errorcode-image.md#62980115-invalid-image-parameter) | Invalid image parameter. |
| [62980097](../errorcode-image.md#62980097-pixelmap-serialization-failed) | IPC error. Possible cause: 1.IPC communication failed. 2. Image upload exception. 3. Decode process exception. 4. Insufficient memory. |
| [62980096](../errorcode-image.md#62980096-operation-failed) | The operation failed. Possible cause: 1.Image upload exception. 2. Decoding process exception. 3. Insufficient memory. |

**Examples**

```TypeScript
// EntryAbility.ets
import { rpc } from '@kit.IPCKit';

class MySequence implements rpc.Parcelable {
  pixelMap: image.PixelMap;
  constructor(pixelMap: image.PixelMap) {
    this.pixelMap = pixelMap;
  }
  marshalling(messageSequence: rpc.MessageSequence) {
    this.pixelMap.marshalling(messageSequence);
    console.info('Marshalled the PixelMap.');
    return true;
  }
  unmarshalling(messageSequence: rpc.MessageSequence) {
    image.createPixelMap(new ArrayBuffer(96), {size: { height: 4, width: 6 }}).then((pixelParcel: image.PixelMap) => {
      pixelParcel.unmarshalling(messageSequence).then(async (pixelMap: image.PixelMap) => {
        this.pixelMap = pixelMap;
        pixelMap.getImageInfo().then((imageInfo: image.ImageInfo) => {
          console.info(`Unmarshalled information: height = ${imageInfo.size.height}, width = ${imageInfo.size.width}.`);
        });
      });
    });
    return true;
  }
}

async function unmarshal() {
  const color: ArrayBuffer = new ArrayBuffer(96);
  let bufferArr: Uint8Array = new Uint8Array(color);
  for (let i = 0; i < bufferArr.length; i++) {
    bufferArr[i] = 0x80;
  }
  let opts: image.InitializationOptions = {
    editable: true,
    pixelFormat: image.PixelMapFormat.BGRA_8888,
    size: { height: 4, width: 6 },
    alphaType: image.AlphaType.UNPREMUL
  };
  let pixelMap: image.PixelMap | undefined = undefined;
  await image.createPixelMap(color, opts).then((srcPixelMap: image.PixelMap) => {
    pixelMap = srcPixelMap;
  })
  if (pixelMap != undefined) {
    // Implement serialization.
    let parcelable: MySequence = new MySequence(pixelMap);
    let data: rpc.MessageSequence = rpc.MessageSequence.create();
    data.writeParcelable(parcelable);

    // Implement deserialization to obtain data through the RPC.
    let seq: MySequence = new MySequence(pixelMap);
    data.readParcelable(seq);
  }
}
```

## writeAllPixelsFromBuffer

```TypeScript
writeAllPixelsFromBuffer(src: ArrayBuffer): Promise<void>
```

Reads the pixel data from a buffer and writes the data to the PixelMap. The source data must be in the same pixel format as the PixelMap.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| src | ArrayBuffer | Yes | The buffer that contains pixel data to be written to the PixelMap. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | A Promise that resolves when the operation completes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7600104](../errorcode-image.md#7600104-failed-to-obtain-image-data) | Failed to get image data. Possible cause: Internal data is corrupted. Please check the logs for detailed information. |
| [7600105](../errorcode-image.md#7600105-pixelmap-object-has-been-released) | The PixelMap has been released. |
| [7600106](../errorcode-image.md#7600106-pixelmap-has-been-passed-to-another-thread) | The PixelMap has been passed to another thread. |
| [7600201](../errorcode-image.md#7600201-unsupported-operation) | Unsupported operation because the PixelMap is not editable or is locked. |
| [7600206](../errorcode-image.md#7600206-invalid-parameter) | Invalid parameter. Possible cause: Size of the buffer is too small. |
| [7600302](../errorcode-image.md#7600302-memory-copy-failure) | Failed to copy the memory. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function writeAllPixelsFromBuffer(pixelMap: image.PixelMap) {
  const writeBuffer = new ArrayBuffer(pixelMap.getPixelBytesNumber());
  const bufferArr = new Uint8Array(writeBuffer);
  for (let i = 0; i < bufferArr.length; i += 4) {
    // Assuming the pixel format of pixelMap is RGBA_8888, the array indices are in the following order: R channel, G channel, B channel, A channel.
    bufferArr[i] = 0xFF;
    bufferArr[i + 1] = 0x00;
    bufferArr[i + 2] = 0x00;
    bufferArr[i + 3] = 0xFF;
  }

  pixelMap.writeAllPixelsFromBuffer(writeBuffer)
    .then(() => {
      console.info('Succeeded in writing pixel data from writeBuffer to the PixelMap.');
    })
    .catch((err: BusinessError) => {
      console.error(`Failed to write pixel data. Code: ${err.code}, message: ${err.message}`);
    });
}
```

## writeAllPixelsFromBufferSync

```TypeScript
writeAllPixelsFromBufferSync(src: ArrayBuffer): void
```

Reads the pixel data from a buffer and writes the data to the PixelMap. The source data must be in the same pixel format as the PixelMap.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| src | ArrayBuffer | Yes | The buffer that contains pixel data to be written to the PixelMap. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7600104](../errorcode-image.md#7600104-failed-to-obtain-image-data) | Failed to get image data. Possible cause: Internal data is corrupted. Please check the logs for detailed information. |
| [7600105](../errorcode-image.md#7600105-pixelmap-object-has-been-released) | The PixelMap has been released. |
| [7600106](../errorcode-image.md#7600106-pixelmap-has-been-passed-to-another-thread) | The PixelMap has been passed to another thread. |
| [7600201](../errorcode-image.md#7600201-unsupported-operation) | Unsupported operation because the PixelMap is not editable or is locked. |
| [7600206](../errorcode-image.md#7600206-invalid-parameter) | Invalid parameter. Possible cause: Size of the buffer is too small. |
| [7600302](../errorcode-image.md#7600302-memory-copy-failure) | Failed to copy the memory. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function writeAllPixelsFromBufferSync(pixelMap: image.PixelMap) {
  const writeBuffer = new ArrayBuffer(pixelMap.getPixelBytesNumber());
  const bufferArr = new Uint8Array(writeBuffer);
  for (let i = 0; i < bufferArr.length; i += 4) {
    // Assuming the pixel format of pixelMap is RGBA_8888, the array indices are in the following order: R channel, G channel, B channel, A channel.
    bufferArr[i] = 0xFF;
    bufferArr[i + 1] = 0x00;
    bufferArr[i + 2] = 0x00;
    bufferArr[i + 3] = 0xFF;
  }

  try {
    pixelMap.writeAllPixelsFromBufferSync(writeBuffer);
    console.info('Succeeded in writing pixel data from writeBuffer to the PixelMap.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to write pixel data. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## writeBufferToPixels

```TypeScript
writeBufferToPixels(src: ArrayBuffer): Promise<void>
```

Reads the pixels in the buffer based on the PixelMap's pixel format and writes the data to this PixelMap object. This API uses a promise to return the result.

Starting from API 26.0.0, it is recommended to use [writeAllPixelsFromBuffer](#writeallpixelsfrombuffer) instead for better exception handling capabilities.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| src | ArrayBuffer | Yes | Buffer from which the pixels are read. The buffer size is obtained by calling [getPixelBytesNumber](#getpixelbytesnumber). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function writeBufferToPixels(pixelMap: image.PixelMap) {
  const color: ArrayBuffer = new ArrayBuffer(pixelMap.getPixelBytesNumber());
  let bufferArr: Uint8Array = new Uint8Array(color);
  for (let i = 0; i < bufferArr.length; i++) {
    bufferArr[i] = i + 1;
  }
  pixelMap.writeBufferToPixels(color).then(() => {
    console.info('Succeeded in writing data from the buffer to the PixelMap.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to write data from the buffer to the PixelMap. Code: ${err.code}, message: ${err.message}`);
  });
}
```

<a id="writebuffertopixels-1"></a>

## writeBufferToPixels

```TypeScript
writeBufferToPixels(src: ArrayBuffer, callback: AsyncCallback<void>): void
```

Reads the pixels in the buffer based on the PixelMap's pixel format and writes the data to this PixelMap object. This API uses an asynchronous callback to return the result.

Starting from API 26.0.0, it is recommended to use [writeAllPixelsFromBuffer](#writeallpixelsfrombuffer) instead for better exception handling capabilities.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| src | ArrayBuffer | Yes | Buffer from which the pixels are read. The buffer size is obtained by calling [getPixelBytesNumber](#getpixelbytesnumber). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the pixels in the buffer are successfully written to the PixelMap, **err** is **undefined**; otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function writeBufferToPixels(pixelMap: image.PixelMap) {
  const color: ArrayBuffer = new ArrayBuffer(pixelMap.getPixelBytesNumber());
  let bufferArr: Uint8Array = new Uint8Array(color);
  for (let i = 0; i < bufferArr.length; i++) {
    bufferArr[i] = i + 1;
  }
  pixelMap.writeBufferToPixels(color, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to write data from the buffer to the PixelMap. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in writing data from the buffer to the PixelMap.');
  });
}
```

## writeBufferToPixelsSync

```TypeScript
writeBufferToPixelsSync(src: ArrayBuffer): void
```

Reads the pixels in the buffer based on the PixelMap's pixel format and writes the data to this PixelMap object. This API returns the result synchronously.

Starting from API 26.0.0, it is recommended to use [writeAllPixelsFromBufferSync](#writeallpixelsfrombuffersync) instead for better exception handling capabilities.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| src | ArrayBuffer | Yes | Buffer from which the pixels are read. The buffer size is obtained by calling [getPixelBytesNumber](#getpixelbytesnumber). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../errorcode-image.md#501-api-call-failed) | The resource is unavailable as it is occupied by another thread. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function writeBufferToPixelsSync(pixelMap: image.PixelMap) {
  const color: ArrayBuffer = new ArrayBuffer(pixelMap.getPixelBytesNumber());
  let bufferArr: Uint8Array = new Uint8Array(color);
  for (let i = 0; i < bufferArr.length; i++) {
    bufferArr[i] = i + 1;
  }
  try {
    pixelMap.writeBufferToPixelsSync(color);
    console.info('Succeeded in writing data from the buffer to the PixelMap.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to write data from the buffer to the PixelMap. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## writePixels

```TypeScript
writePixels(area: PositionArea): Promise<void>
```

Reads the pixels in the [PositionArea](arkts-image-image-positionarea-i.md).region buffer in the BGRA_8888 format and writes the data to the area specified by [PositionArea](arkts-image-image-positionarea-i.md).pixels in this PixelMap object. This API uses a promise to return the result. You can use a formula to calculate the size of the memory to be applied for based on **PositionArea**. YUV region calculation formula: region to read (region.size{width * height}) * 1.5 (1 * Y component + 0.25 * U component + 0.25 * V component) RGBA region calculation formula: region to read (region.size{width * height}) * 4 (1 * R component + 1 * G component + 1 * B component + 1 * A component)

Starting from API 26.0.0, it is recommended to use [writePixelsFromArea](#writepixelsfromarea) instead for better exception handling capabilities.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| area | [PositionArea](arkts-image-image-positionarea-i.md) | Yes | Area to which the pixels will be written. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function writePixelsRGBA(pixelMap: image.PixelMap) {
  const area: image.PositionArea = {
    pixels: new ArrayBuffer(8), // 8 indicates the size of the pixel buffer to create. The value is calculated as follows: width × height × 4.
    offset: 0,
    stride: 8,
    region: { size: { height: 1, width: 2 }, x: 0, y: 0 }
  };
  let bufferArr: Uint8Array = new Uint8Array(area.pixels);
  for (let i = 0; i < bufferArr.length; i++) {
    bufferArr[i] = i + 1;
  }
  pixelMap.writePixels(area).then(() => {
    console.info('Succeeded in writing pixels into the specified area.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to write pixels into the specified area. Code: ${err.code}, message: ${err.message}`);
  });
}

function writePixelsYUV(pixelMap: image.PixelMap) {
  const area: image.PositionArea = {
    pixels: new ArrayBuffer(6), // 6 indicates the size of the pixel buffer to create. The value is calculated as follows: width × height × 1.5.
    offset: 0,
    stride: 8, // This variable is not used by the writePixels function when the PixelMap is in YUV format.
    region: { size: { height: 2, width: 2 }, x: 0, y: 0 }
  };
  let bufferArr: Uint8Array = new Uint8Array(area.pixels);
  for (let i = 0; i < bufferArr.length; i++) {
    bufferArr[i] = i + 1;
  }
  pixelMap.writePixels(area).then(() => {
    console.info('Succeeded in writing pixels into the specified area.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to write pixels into the specified area. Code: ${err.code}, message: ${err.message}`);
  });
}
```

<a id="writepixels-1"></a>

## writePixels

```TypeScript
writePixels(area: PositionArea, callback: AsyncCallback<void>): void
```

Reads the pixels in the [PositionArea](arkts-image-image-positionarea-i.md).region buffer in the BGRA_8888 format and writes the data to the area specified by [PositionArea](arkts-image-image-positionarea-i.md).pixels in this PixelMap object. This API uses an asynchronous callback to return the result. You can use a formula to calculate the size of the memory to be applied for based on **PositionArea**. YUV region calculation formula: region to read (region.size{width * height}) * 1.5 (1 * Y component + 0.25 * U component + 0.25 * V component) RGBA region calculation formula: region to read (region.size{width * height}) * 4 (1 * R component + 1 * G component + 1 * B component + 1 * A component)

Starting from API 26.0.0, it is recommended to use [writePixelsFromArea](#writepixelsfromarea) instead for better exception handling capabilities.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| area | [PositionArea](arkts-image-image-positionarea-i.md) | Yes | Area to which the pixels will be written. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function writePixelsRGBA(pixelMap: image.PixelMap) {
  const area: image.PositionArea = {
    pixels: new ArrayBuffer(8), // 8 indicates the size of the pixel buffer to create. The value is calculated as follows: width × height × 4.
    offset: 0,
    stride: 8,
    region: { size: { height: 1, width: 2 }, x: 0, y: 0 }
  };
  let bufferArr: Uint8Array = new Uint8Array(area.pixels);
  for (let i = 0; i < bufferArr.length; i++) {
    bufferArr[i] = i + 1;
  }
  pixelMap.writePixels(area, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to write pixels into the specified area. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in writing pixels into the specified area.');
  });
}

function writePixelsYUV(pixelMap: image.PixelMap) {
  const area: image.PositionArea = {
    pixels: new ArrayBuffer(6), // 6 indicates the size of the pixel buffer to create. The value is calculated as follows: width × height × 1.5.
    offset: 0,
    stride: 8, // This variable is not used by the writePixels function when the PixelMap is in YUV format.
    region: { size: { height: 2, width: 2 }, x: 0, y: 0 }
  };
  let bufferArr: Uint8Array = new Uint8Array(area.pixels);
  for (let i = 0; i < bufferArr.length; i++) {
    bufferArr[i] = i + 1;
  }
  pixelMap.writePixels(area, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to write pixels into the specified area. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in writing pixels into the specified area.');
  });
}
```

## writePixelsFromArea

```TypeScript
writePixelsFromArea(area: PositionArea): Promise<void>
```

Writes data from a buffer to a certain area of the PixelMap. The source data must be in BGRA_8888 format.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| area | [PositionArea](arkts-image-image-positionarea-i.md) | Yes | Area of the PixelMap to write the data. Data will be copied from PositionArea.pixels to the PixelMap. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | A Promise that resolves when the operation completes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7600104](../errorcode-image.md#7600104-failed-to-obtain-image-data) | Failed to get image data. Possible cause: Internal data is corrupted. Please check the logs for detailed information. |
| [7600105](../errorcode-image.md#7600105-pixelmap-object-has-been-released) | The PixelMap has been released. |
| [7600106](../errorcode-image.md#7600106-pixelmap-has-been-passed-to-another-thread) | The PixelMap has been passed to another thread. |
| [7600201](../errorcode-image.md#7600201-unsupported-operation) | Unsupported operation because the PixelMap is not editable or is locked. |
| [7600206](../errorcode-image.md#7600206-invalid-parameter) | Invalid parameter. Possible causes: 1. PositionArea.pixels is too small. 2. PositionArea.region is out of range. |
| [7600302](../errorcode-image.md#7600302-memory-copy-failure) | Failed to copy the memory. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function writePixelsFromAreaRGBA(pixelMap: image.PixelMap) {
  const area: image.PositionArea = {
    pixels: new ArrayBuffer(24), // 24 indicates the size of the pixel buffer to create. The value is calculated as follows: width × height × 4.
    offset: 0,
    stride: 8, // Stride, that is, the number of bytes occupied by pixels in each row. If no padding byte is added at the end of a row, the value is width × 4.
    region: {
      size: { width: 2, height: 3 },
      x: 0,
      y: 0
    }
  };
  const bufferArr = new Uint8Array(area.pixels);
  for (let i = 0; i < bufferArr.length; i += 4) {
    // The data source format must be BGRA_8888. The array indices are in the following order: B channel, G channel, R channel, A channel.
    bufferArr[i] = 0xFF;
    bufferArr[i + 1] = 0x00;
    bufferArr[i + 2] = 0x00;
    bufferArr[i + 3] = 0xFF;
  }

  pixelMap.writePixelsFromArea(area)
    .then(() => {
      console.info('Succeeded in writing pixel data from area.pixels to the specified area of the PixelMap.');
    })
    .catch((err: BusinessError) => {
      console.error(`Failed to write pixel data. Code: ${err.code}, message: ${err.message}`);
    });
}

function writePixelsFromAreaYUV(pixelMap: image.PixelMap) {
  const area: image.PositionArea = {
    pixels: new ArrayBuffer(9), // 9 indicates the size of the pixel buffer to create. The value is calculated as follows: width × height × 1.5.
    offset: 0,
    stride: 2, // This variable is not used by the writePixelsFromArea function when the PixelMap is in YUV format.
    region: {
      size: { width: 2, height: 3 },
      x: 0,
      y: 0
    }
  };
  const bufferArr = new Uint8Array(area.pixels);
  const ySize = area.region.size.width * area.region.size.height;
  for (let i = 0; i < ySize; i++) { // Y plane.
    bufferArr[i] = 0xFF;
  }
  for (let i = ySize; i < bufferArr.length; i++) { // UV interleaved plane.
    bufferArr[i] = 0x80;
  }

  pixelMap.writePixelsFromArea(area)
    .then(() => {
      console.info('Succeeded in writing pixel data from area.pixels to the specified area of the PixelMap.');
    })
    .catch((err: BusinessError) => {
      console.error(`Failed to write pixel data. Code: ${err.code}, message: ${err.message}`);
    });
}
```

## writePixelsFromAreaSync

```TypeScript
writePixelsFromAreaSync(area: PositionArea): void
```

Writes data from a buffer to a certain area of the PixelMap. The source data must be in BGRA_8888 format.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| area | [PositionArea](arkts-image-image-positionarea-i.md) | Yes | Area of the PixelMap to write the data. Data will be copied from PositionArea.pixels to the PixelMap. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7600104](../errorcode-image.md#7600104-failed-to-obtain-image-data) | Failed to get image data. Possible cause: Internal data is corrupted. Please check the logs for detailed information. |
| [7600105](../errorcode-image.md#7600105-pixelmap-object-has-been-released) | The PixelMap has been released. |
| [7600106](../errorcode-image.md#7600106-pixelmap-has-been-passed-to-another-thread) | The PixelMap has been passed to another thread. |
| [7600201](../errorcode-image.md#7600201-unsupported-operation) | Unsupported operation because the PixelMap is not editable or is locked. |
| [7600206](../errorcode-image.md#7600206-invalid-parameter) | Invalid parameter. Possible causes: 1. PositionArea.pixels is too small. 2. PositionArea.region is out of range. |
| [7600302](../errorcode-image.md#7600302-memory-copy-failure) | Failed to copy the memory. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function writePixelsFromAreaSyncRGBA(pixelMap: image.PixelMap) {
  const area: image.PositionArea = {
    pixels: new ArrayBuffer(24), // 24 indicates the size of the pixel buffer to create. The value is calculated as follows: width × height × 4.
    offset: 0,
    stride: 8, // Stride, that is, the number of bytes occupied by pixels in each row. If no padding byte is added at the end of a row, the value is width × 4.
    region: {
      size: { width: 2, height: 3 },
      x: 0,
      y: 0
    }
  };
  const bufferArr = new Uint8Array(area.pixels);
  for (let i = 0; i < bufferArr.length; i += 4) {
    // The data source format must be BGRA_8888. The array indices are in the following order: B channel, G channel, R channel, A channel.
    bufferArr[i] = 0xFF;
    bufferArr[i + 1] = 0x00;
    bufferArr[i + 2] = 0x00;
    bufferArr[i + 3] = 0xFF;
  }

  try {
    pixelMap.writePixelsFromAreaSync(area);
    console.info('Succeeded in writing pixel data from area.pixels to the specified area of the PixelMap.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to write pixel data. Code: ${err.code}, message: ${err.message}`);
  }
}

function writePixelsFromAreaSyncYUV(pixelMap: image.PixelMap) {
  const area: image.PositionArea = {
    pixels: new ArrayBuffer(9), // 9 indicates the size of the pixel buffer to create. The value is calculated as follows: width × height × 1.5.
    offset: 0,
    stride: 2, // This variable is not used by the writePixelsFromAreaSync function when the PixelMap is in YUV format.
    region: {
      size: { width: 2, height: 3 },
      x: 0,
      y: 0
    }
  };
  const bufferArr = new Uint8Array(area.pixels);
  const ySize = area.region.size.width * area.region.size.height;
  for (let i = 0; i < ySize; i++) { // Y plane.
    bufferArr[i] = 0xFF;
  }
  for (let i = ySize; i < bufferArr.length; i++) { // UV interleaved plane.
    bufferArr[i] = 0x80;
  }

  try {
    pixelMap.writePixelsFromAreaSync(area);
    console.info('Succeeded in writing pixel data from area.pixels to the specified area of the PixelMap.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to write pixel data. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## writePixelsSync

```TypeScript
writePixelsSync(area: PositionArea): void
```

Reads the pixels in the [PositionArea](arkts-image-image-positionarea-i.md).region buffer in the BGRA_8888 format and writes the data to the area specified by [PositionArea](arkts-image-image-positionarea-i.md).pixels in this PixelMap object. This API returns the result synchronously.

Starting from API 26.0.0, it is recommended to use [writePixelsFromAreaSync](#writepixelsfromareasync) instead for better exception handling capabilities.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| area | [PositionArea](arkts-image-image-positionarea-i.md) | Yes | Area to which the pixels will be written. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [501](../errorcode-image.md#501-api-call-failed) | The resource is unavailable as it is occupied by another thread. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function writePixelsSync(pixelMap: image.PixelMap) {
  const area: image.PositionArea = {
    pixels: new ArrayBuffer(8),
    offset: 0,
    stride: 8,
    region: { size: { height: 1, width: 2 }, x: 0, y: 0 }
  };
  let bufferArr: Uint8Array = new Uint8Array(area.pixels);
  for (let i = 0; i < bufferArr.length; i++) {
    bufferArr[i] = i + 1;
  }
  try {
    pixelMap.writePixelsSync(area);
    console.info('Succeeded in writing pixels into the specified area.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to write pixels into the specified area. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## isEditable

```TypeScript
readonly isEditable: boolean
```

Whether the image pixels are editable. **true** if editable, **false** otherwise. The value **false** provides better image rendering and transmission performance.<br> This API can be used in atomic services since API version 11.<br> This API can be used in ArkTS widgets since API version 12.

**Type:** boolean

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core

## isStrideAlignment

```TypeScript
readonly isStrideAlignment: boolean
```

Whether the row data of the image is memory aligned. The value **true** means that the row data is memory-aligned, and there may be blank bytes padded at the end of each row to meet alignment requirements. The value **false** means that the row data is not memory-aligned, and rows are packed contiguously with no padding bytes at the end.

**Type:** boolean

**Since:** 11

**System capability:** SystemCapability.Multimedia.Image.Core
