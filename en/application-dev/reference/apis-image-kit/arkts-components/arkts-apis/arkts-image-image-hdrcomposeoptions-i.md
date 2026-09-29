# HdrComposeOptions

```TypeScript
interface HdrComposeOptions
```

Describes compose parameters.

@typedef HdrComposeOptions

**Since:** 23

<!--Device-image-interface HdrComposeOptions--><!--Device-image-interface HdrComposeOptions-End-->

**System capability:** SystemCapability.Multimedia.Image.Core

## Modules to Import

```TypeScript
import { image } from '@kit.ImageKit';
```

## desiredPixelFormat

```TypeScript
desiredPixelFormat?: PixelMapFormat
```

Pixel format used for composite image, RGBA_1010102\YCBCR_P010\YCRCB_P010 are supported.

**Type:** [PixelMapFormat](arkts-image-image-pixelmapformat-e.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-HdrComposeOptions-desiredPixelFormat?: PixelMapFormat--><!--Device-HdrComposeOptions-desiredPixelFormat?: PixelMapFormat-End-->

**System capability:** SystemCapability.Multimedia.Image.Core
