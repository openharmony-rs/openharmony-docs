# HdrDecomposeOptions (System API)

Describes the options for decomposing an HDR Pixelmap to a Picture containing an SDR PixelMap and a gainmap.

**Since:** 26.0.0

**System capability:** SystemCapability.Multimedia.Image.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { image } from '@kit.ImageKit';
```

## desiredPixelFormat

```TypeScript
desiredPixelFormat?: PixelMapFormat
```

Indicates the pixel format of the decomposed SDR Pixelmap and the gainmap. The formats of RGBA_8888\NV12\NV21 are supported. Default value: RGBA_8888.

**Type:** [PixelMapFormat](arkts-image-image-pixelmapformat-e.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

**System API:** This is a system API.

## isFullSizeGainmap

```TypeScript
isFullSizeGainmap?: boolean
```

Indicates generating a full-size gainmap or a 1/2 downscaled gainmap. Default value: false.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

**System API:** This is a system API.
