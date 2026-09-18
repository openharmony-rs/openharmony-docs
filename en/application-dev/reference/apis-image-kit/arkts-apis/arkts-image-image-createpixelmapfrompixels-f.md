# createPixelMapFromPixels

## Modules to Import

```TypeScript
import { image } from '@kit.ImageKit';
```

## createPixelMapFromPixels

```TypeScript
function createPixelMapFromPixels(pixels: ArrayBuffer, param: InitializationOptions): Promise<PixelMap>
```

Creates a PixelMap from existing pixel data. The pixel data will be copied and converted to the specified pixel format to initialize the PixelMap.

The following pixel formats are not supported for PixelMap creation: RGBA_1010102, YCBCR_P010, YCRCB_P010, ASTC_4x4.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| pixels | ArrayBuffer | Yes | The pixel data buffer used to initialize the PixelMap. The format of the pixel data can be specified by InitializationOptions.srcPixelFormat. The size of the buffer should be: image width * image height * bytes per pixel. |
| param | [InitializationOptions](arkts-image-image-initializationoptions-i.md) | Yes | Initialization options for the PixelMap. If InitializationOptions.pixelFormat is set to ASTC_4x4, it will be reset to the default value RGBA_8888. If InitializationOptions.srcPixelFormat is set to ASTC_4x4, it will be reset to the default value BGRA_8888. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[PixelMap](arkts-image-image-pixelmap-i.md)&gt; | A Promise of the new PixelMap created. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7600206](../errorcode-image.md#7600206-invalid-parameter) | Invalid parameter. Possible cause: Size of the pixel data buffer does not match InitializationOptions.size. |
| [7600207](../errorcode-image.md#7600207-unsupported-data-format) | Unsupported pixel format. |
| [7600301](../errorcode-image.md#7600301-memory-allocation-failure) | Failed to allocate memory. Possible causes: 1. The resulting PixelMap size is too large. 2. The system is out of memory. |
| [7600305](../errorcode-image.md#7600305-failed-to-create-the-pixelmap) | Failed to create the PixelMap. Possible causes: 1. Failed to perform pixel format conversion. 2. Internal data is corrupted. Please check the logs for detailed information. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function createPixelMapFromPixels() {
  const size: image.Size = {
    width: 6,
    height: 4
  };
  const pixels = new ArrayBuffer(size.width * size.height * 4); // 4 is the number of bytes per pixel for the RGBA pixel format.
  const pixelsArr = new Uint8Array(pixels);
  for (let i = 0; i < pixelsArr.length; i += 4) {
    // In RGBA_8888 format, the following array indexes correspond to the R, G, B, and A channels in sequence.
    pixelsArr[i] = 0xFF;
    pixelsArr[i + 1] = 0x00;
    pixelsArr[i + 2] = 0x00;
    pixelsArr[i + 3] = 0xFF;
  }
  const config: image.InitializationOptions = {
    size,
    srcPixelFormat: image.PixelMapFormat.RGBA_8888, // Pixel format of the source pixel data in the buffer.
    pixelFormat: image.PixelMapFormat.BGRA_8888, // Pixel format of the new PixelMap.
    editable: true
  };

  image.createPixelMapFromPixels(pixels, config)
    .then((pixelMap: image.PixelMap) => {
      console.info('Succeeded in creating the PixelMap.');
    }).catch((err: BusinessError) => {
      console.error(`Failed to create the PixelMap. Code: ${err.code}, message: ${err.message}`);
    });
}
```
