# InitializationOptions

Defines PixelMap initialization options.

**Since:** 8

**System capability:** SystemCapability.Multimedia.Image.Core

## Modules to Import

```TypeScript
import { image } from '@kit.ImageKit';
```

## alphaType

```TypeScript
alphaType?: AlphaType
```

Alpha type. The default value is **IMAGE_ALPHA_TYPE_PREMUL**.

**Type:** [AlphaType](arkts-image-image-alphatype-e.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core

## editable

```TypeScript
editable?: boolean
```

Whether the image pixels are editable. **true** if editable, **false** otherwise. The value **false** provides better image rendering and transmission performance. The default value is **false**.

**Type:** boolean

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core

## pixelFormat

```TypeScript
pixelFormat?: PixelMapFormat
```

Pixel format of the generated PixelMap. The default value is **RGBA_8888**.

**Type:** [PixelMapFormat](arkts-image-image-pixelmapformat-e.md)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core

## scaleMode

```TypeScript
scaleMode?: ScaleMode
```

Scale mode. The default value is **0**.

**Type:** [ScaleMode](arkts-image-image-scalemode-e.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core

## size

```TypeScript
size: Size
```

Image size.

**Type:** Size

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core

## srcPixelFormat

```TypeScript
srcPixelFormat?: PixelMapFormat
```

Pixel format of the passed-in buffer data. The default value is **BGRA_8888**.

**Type:** [PixelMapFormat](arkts-image-image-pixelmapformat-e.md)

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core
