# createEffect

## Modules to Import

```TypeScript
import { effectKit } from '@kit.ArkGraphics2D';
```

## createEffect

```TypeScript
function createEffect(source: image.PixelMap): Filter
```

Creates a Filter instance based on the input PixelMap. You can then add various image effects through chained calls, and finally obtain the processed image via getEffectPixelMap.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| source | [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md) | Yes | PixelMap instance created by the image module. An instance can be obtained by decoding an image or directly created. For details, see Introduction to Image Kit. |

**Return value:**

| Type | Description |
| --- | --- |
| [Filter](arkts-arkgraphics2d-effectkit-filter-i.md) | Returns a Filter instance with no effects added, or null if the operation fails. |

**Examples**

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
  // Create a Filter instance.
  let headFilter = effectKit.createEffect(pixelMap);
});
```
