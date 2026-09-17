# createPixelMapSync

## Modules to Import

```TypeScript
import { image } from '@kit.ImageKit';
```

## createPixelMapSync

```TypeScript
function createPixelMapSync(colors: ArrayBuffer, options: InitializationOptions): PixelMap
```

Create pixelmap by data buffer.

Starting from API 26.0.0, it is recommended to use [createPixelMapFromPixelsSync](arkts-image-image-createpixelmapfrompixelssync-f.md) instead for better exception handling capabilities.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| colors | ArrayBuffer | Yes | The image color buffer. |
| options | [InitializationOptions](arkts-image-image-initializationoptions-i.md) | Yes | Initialization options for pixelmap. |

**Return value:**

| Type | Description |
| --- | --- |
| [PixelMap](arkts-image-image-pixelmap-i.md) | Returns the instance if the operation is successful;Otherwise, return undefined. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function createPixelMapSync() {
  const color: ArrayBuffer = new ArrayBuffer(96); // 96 indicates the size of the pixel buffer to create. The value is calculated as follows: width × height × 4.
  let opts: image.InitializationOptions = {
    size: { height: 4, width: 6 },
    srcPixelFormat: image.PixelMapFormat.RGBA_8888, // Pixel format of the source pixel data in the buffer.
    pixelFormat: image.PixelMapFormat.BGRA_8888, // Pixel format of the new PixelMap.
    editable: true
  };
  try {
    let pixelMap: image.PixelMap = image.createPixelMapSync(color, opts);
    console.info('Succeeded in creating the PixelMap.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to create the PixelMap. Code: ${err.code}, message: ${err.message}`);
  }
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function createPixelMapSync() {
  let opts: image.InitializationOptions = { editable: true, pixelFormat: image.PixelMapFormat.RGBA_1010102, size: { height: 4, width: 6 } };
  try {
    let pixelMap: image.PixelMap = image.createPixelMapSync(opts);
    console.info('Succeeded in creating the PixelMap.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to create the PixelMap. Code: ${err.code}, message: ${err.message}`);
  }
}
```


## createPixelMapSync

```TypeScript
function createPixelMapSync(options: InitializationOptions): PixelMap
```

Create an empty pixelmap.

Starting from API 26.0.0, it is recommended to use [createEmptyPixelMap](arkts-image-image-createemptypixelmap-f.md) instead for better exception handling capabilities.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [InitializationOptions](arkts-image-image-initializationoptions-i.md) | Yes | Initialization options for pixelmap. |

**Return value:**

| Type | Description |
| --- | --- |
| [PixelMap](arkts-image-image-pixelmap-i.md) | Returns the instance if the operation is successful;Otherwise, return undefined. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function createPixelMapSync() {
  const color: ArrayBuffer = new ArrayBuffer(96); // 96 indicates the size of the pixel buffer to create. The value is calculated as follows: width × height × 4.
  let opts: image.InitializationOptions = {
    size: { height: 4, width: 6 },
    srcPixelFormat: image.PixelMapFormat.RGBA_8888, // Pixel format of the source pixel data in the buffer.
    pixelFormat: image.PixelMapFormat.BGRA_8888, // Pixel format of the new PixelMap.
    editable: true
  };
  try {
    let pixelMap: image.PixelMap = image.createPixelMapSync(color, opts);
    console.info('Succeeded in creating the PixelMap.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to create the PixelMap. Code: ${err.code}, message: ${err.message}`);
  }
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function createPixelMapSync() {
  let opts: image.InitializationOptions = { editable: true, pixelFormat: image.PixelMapFormat.RGBA_1010102, size: { height: 4, width: 6 } };
  try {
    let pixelMap: image.PixelMap = image.createPixelMapSync(opts);
    console.info('Succeeded in creating the PixelMap.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to create the PixelMap. Code: ${err.code}, message: ${err.message}`);
  }
}
```
