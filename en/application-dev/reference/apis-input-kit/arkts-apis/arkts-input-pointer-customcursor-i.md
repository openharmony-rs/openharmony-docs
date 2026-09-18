# CustomCursor

Defines custom cursor resources.

**Since:** 15

**System capability:** SystemCapability.MultimodalInput.Input.Pointer

## Modules to Import

```TypeScript
import { pointer } from '@kit.InputKit';
```

## focusX

```TypeScript
focusX?: number
```

Horizontal coordinate of the custom pointer focus, in px. This coordinate is limited by the custom pointer size. The minimum value is 0, and the maximum value is the maximum width of the resource image. The default value is **0** when this parameter is omitted.

**Type:** number

**Since:** 15

**System capability:** SystemCapability.MultimodalInput.Input.Pointer

## focusY

```TypeScript
focusY?: number
```

Vertical coordinate of the custom pointer focus, in px. This coordinate is limited by the custom pointer size. The minimum value is 0, and the maximum value is the maximum width of the resource image. The default value is **0** when this parameter is omitted.

**Type:** number

**Since:** 15

**System capability:** SystemCapability.MultimodalInput.Input.Pointer

## pixelMap

```TypeScript
pixelMap: image.PixelMap
```

Pixel map. The minimum size is subject to the minimum limit of the image. The maximum size is 256 x 256 px.

**Type:** [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)

**Since:** 15

**System capability:** SystemCapability.MultimodalInput.Input.Pointer
