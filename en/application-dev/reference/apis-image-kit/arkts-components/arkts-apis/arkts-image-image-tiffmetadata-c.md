# TiffMetadata

TIFF metadata.

**Since:** 26.0.0

**System capability:** SystemCapability.Multimedia.Image.Core

## Modules to Import

```TypeScript
import { image } from '@kit.ImageKit';
```

## artist

```TypeScript
readonly artist?: string
```

Name of the image creator or artist.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## compression

```TypeScript
readonly compression?: number
```

Compression scheme used for image data (e.g., None, LZW, JPEG, Deflate). The value should be an integer.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## copyright

```TypeScript
readonly copyright?: string
```

Copyright notice for the image.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## dateTime

```TypeScript
readonly dateTime?: string
```

Date and time associated with the image (typically last modification).

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## documentName

```TypeScript
readonly documentName?: string
```

Name of the document or image.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## hostComputer

```TypeScript
readonly hostComputer?: string
```

Host computer/system used for image processing.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## imageDescription

```TypeScript
readonly imageDescription?: string
```

Description of the image content.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## make

```TypeScript
readonly make?: string
```

Manufacturer of the capture device.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## model

```TypeScript
readonly model?: string
```

Model name/number of the capture device.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## orientation

```TypeScript
readonly orientation?: Orientation
```

Indicates image orientation for correct display rotation/flip.

**Type:** [Orientation](arkts-image-image-orientation-e.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## photometricInterpretation

```TypeScript
readonly photometricInterpretation?: number
```

Defines how pixel colors are interpreted (e.g., RGB, grayscale). The value should be an integer.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## primaryChromaticities

```TypeScript
readonly primaryChromaticities?: number[]
```

Chromaticity coordinates of the RGB primaries.

**Type:** number[]

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## resolutionUnit

```TypeScript
readonly resolutionUnit?: number
```

Unit for X/Y resolution. The value should be an integer.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## software

```TypeScript
readonly software?: string
```

Software used to create or process the image.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## tileLength

```TypeScript
readonly tileLength?: number
```

Height of each image tile in pixels. The value should be an integer.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## tileWidth

```TypeScript
readonly tileWidth?: number
```

Width of each image tile in pixels. The value should be an integer.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## transferFunction

```TypeScript
readonly transferFunction?: string
```

Tone transfer curve mapping pixel values to output intensity.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## whitePoint

```TypeScript
readonly whitePoint?: number[]
```

Chromaticity coordinates of the reference white point.

**Type:** number[]

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## xResolution

```TypeScript
readonly xResolution?: number
```

Horizontal resolution (pixels per resolution unit).

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## yResolution

```TypeScript
readonly yResolution?: number
```

Vertical resolution (pixels per resolution unit).

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core
