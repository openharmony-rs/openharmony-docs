# createPixelMapFromSurfaceWithTransformation

## Modules to Import

```TypeScript
import { image } from '@kit.ImageKit';
```

## createPixelMapFromSurfaceWithTransformation

```TypeScript
function createPixelMapFromSurfaceWithTransformation(surfaceId: string, transformEnabled: boolean): Promise<PixelMap>
```

Creates a PixelMap object based on the ID of a Surface with transformation.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| surfaceId | string | Yes | ID of the Surface. |
| transformEnabled | boolean | Yes | Whether to inverse transform the PixelMap to cancel out the transformation from the Surface. If true, the PixelMap will be transformed by the same amount from the Surface but in a reversed direction; if false, the PixelMap will not be transformed. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[PixelMap](arkts-image-image-pixelmap-i.md)&gt; | A Promise of PixelMap instance if the operation is successful. Otherwise, an exception will be thrown. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7600104](../errorcode-image.md#7600104-failed-to-obtain-image-data) | Failed to get the data from Surface. |
| [7600201](../errorcode-image.md#7600201-unsupported-operation) | Unsupported operation, e.g. on cross-platform. |
| [7600206](../errorcode-image.md#7600206-invalid-parameter) | Invalid parameter. |
| [7600305](../errorcode-image.md#7600305-failed-to-create-the-pixelmap) | Failed to create the PixelMap. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function createPixelMapFromSurfaceWithTransformation(surfaceId: string, transformEnabled: boolean) {
  image.createPixelMapFromSurfaceWithTransformation(surfaceId, transformEnabled).then((pixelMap: image.PixelMap) => {
    console.info('Succeeded in creating the PixelMap from Surface.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to create the PixelMap from Surface. Code: ${err.code}, message: ${err.message}`);
  });
}
```
