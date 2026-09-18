# createEmptyPixelMap

## Modules to Import

```TypeScript
import { image } from '@kit.ImageKit';
```

## createEmptyPixelMap

```TypeScript
function createEmptyPixelMap(param: InitializationOptions): PixelMap
```

Creates an empty PixelMap.

The following pixel format is not supported for PixelMap creation: ASTC_4x4.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| param | [InitializationOptions](arkts-image-image-initializationoptions-i.md) | Yes | Initialization options for the PixelMap. If InitializationOptions.pixelFormat is set to ASTC_4x4, it will be reset to the default value RGBA_8888. |

**Return value:**

| Type | Description |
| --- | --- |
| [PixelMap](arkts-image-image-pixelmap-i.md) | The new PixelMap created. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7600206](../errorcode-image.md#7600206-invalid-parameter) | Invalid parameter. |
| [7600301](../errorcode-image.md#7600301-memory-allocation-failure) | Failed to allocate memory. Possible causes: 1. The resulting PixelMap size is too large. 2. The system is out of memory. |
| [7600305](../errorcode-image.md#7600305-failed-to-create-the-pixelmap) | Failed to create the PixelMap. Possible cause: Internal data is corrupted. Please check the logs for detailed information. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function createEmptyPixelMap() {
  const config: image.InitializationOptions = {
    size: { width: 6, height: 4 },
    pixelFormat: image.PixelMapFormat.RGBA_1010102, // Pixel format of the newly created PixelMap.
    editable: true
  };

  try {
    const pixelMap = image.createEmptyPixelMap(config);
    console.info('Succeeded in creating the empty PixelMap.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to create the empty PixelMap. Code: ${err.code}, message: ${err.message}`);
  }
}
```
