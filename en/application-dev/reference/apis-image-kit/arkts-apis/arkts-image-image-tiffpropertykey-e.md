# TiffPropertyKey

```TypeScript
enum TiffPropertyKey
```

Enumerates the properties available for the metadata of a TIFF image.

> **NOTE:** 
> 
> For details about the return value type, see [TiffMetadata](arkts-image-image-tiffmetadata-c.md).

**Since:** 26.0.0

**System capability:** SystemCapability.Multimedia.Image.Core

## COMPRESSION

```TypeScript
COMPRESSION = 'TiffCompression'
```

Compression scheme used for image data (e.g., None, LZW, JPEG, Deflate).

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## PHOTOMETRIC_INTERPRETATION

```TypeScript
PHOTOMETRIC_INTERPRETATION = 'TiffPhotometricInterpretation'
```

Defines how pixel colors are interpreted (e.g., RGB, grayscale).

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## TRANSFER_FUNCTION

```TypeScript
TRANSFER_FUNCTION = 'TiffTransferFunction'
```

Tone transfer curve mapping pixel values to output intensity.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## ORIENTATION

```TypeScript
ORIENTATION = 'TiffOrientation'
```

Indicates image orientation for correct display rotation/flip.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## X_RESOLUTION

```TypeScript
X_RESOLUTION = 'TiffXResolution'
```

Horizontal resolution (pixels per resolution unit).

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## Y_RESOLUTION

```TypeScript
Y_RESOLUTION = 'TiffYResolution'
```

Vertical resolution (pixels per resolution unit).

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## RESOLUTION_UNIT

```TypeScript
RESOLUTION_UNIT = 'TiffResolutionUnit'
```

Unit for X/Y resolution.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## WHITE_POINT

```TypeScript
WHITE_POINT = 'TiffWhitePoint'
```

Chromaticity coordinates of the reference white point.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## PRIMARY_CHROMATICITIES

```TypeScript
PRIMARY_CHROMATICITIES = 'TiffPrimaryChromaticities'
```

Chromaticity coordinates of the RGB primaries.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## TILE_LENGTH

```TypeScript
TILE_LENGTH = 'TiffTileLength'
```

Height of each image tile in pixels.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## TILE_WIDTH

```TypeScript
TILE_WIDTH = 'TiffTileWidth'
```

Width of each image tile in pixels.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## DOCUMENT_NAME

```TypeScript
DOCUMENT_NAME = 'TiffDocumentName'
```

Name of the document or image.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## IMAGE_DESCRIPTION

```TypeScript
IMAGE_DESCRIPTION = 'TiffImageDescription'
```

Description of the image content.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## ARTIST

```TypeScript
ARTIST = 'TiffArtist'
```

Name of the image creator or artist.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## COPYRIGHT

```TypeScript
COPYRIGHT = 'TiffCopyright'
```

Copyright notice for the image.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## DATE_TIME

```TypeScript
DATE_TIME = 'TiffDateTime'
```

Date and time associated with the image (typically last modification).

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## MAKE

```TypeScript
MAKE = 'TiffMake'
```

Manufacturer of the capture device.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## MODEL

```TypeScript
MODEL = 'TiffModel'
```

Model name/number of the capture device.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## SOFTWARE

```TypeScript
SOFTWARE = 'TiffSoftware'
```

Software used to create or process the image.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## HOST_COMPUTER

```TypeScript
HOST_COMPUTER = 'TiffHostComputer'
```

Host computer/system used for image processing.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core
