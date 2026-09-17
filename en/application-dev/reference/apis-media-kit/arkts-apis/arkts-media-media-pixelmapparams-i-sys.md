# PixelMapParams

Defines the format parameters of the video thumbnail to be obtained.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Media.AVImageGenerator

## Modules to Import

```TypeScript
import { media } from '@kit.MediaKit';
```

## autoFlip

```TypeScript
autoFlip?: boolean
```

Auto flip the thumbnail when video has mirror attribute (Vertical Flip or Horizontal Flip). If the value is false, the returned thumbnail will not be flipped.

**System API**: This is a system API.

**Type:** boolean

**Since:** 21

**System capability:** SystemCapability.Multimedia.Media.AVImageGenerator

**System API:** This is a system API.

## colorFormat

```TypeScript
colorFormat?: PixelFormat
```

Color format of the thumbnail.

**System API**: This is a system API.

**Type:** [PixelFormat](arkts-media-media-pixelformat-e-sys.md)

**Since:** 11

**System capability:** SystemCapability.Multimedia.Media.AVImageGenerator

**System API:** This is a system API.
