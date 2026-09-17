# PixelMapParams

Defines the format parameters of the video thumbnail to be obtained.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Media.AVImageGenerator

## Modules to Import

```TypeScript
import { media } from '@kit.MediaKit';
```

## height

```TypeScript
height?: number
```

Height of the thumbnail. Unit: px. The value must be greater than 0 and less than or equal to the height of the original video. Otherwise, the returned thumbnail will not be scaled.

**Type:** number

**Since:** 12

**System capability:** SystemCapability.Multimedia.Media.AVImageGenerator

## width

```TypeScript
width?: number
```

Width of the thumbnail. Unit: px. The value must be greater than 0 and less than or equal to the width of the original video. Otherwise, the returned thumbnail will not be scaled.

**Type:** number

**Since:** 12

**System capability:** SystemCapability.Multimedia.Media.AVImageGenerator
