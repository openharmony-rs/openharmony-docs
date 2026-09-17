# DecodingOptionsForThumbnail

Describes thumbnail decoding parameters.

**Since:** 26.0.0

**System capability:** SystemCapability.Multimedia.Image.ImageSource

## Modules to Import

```TypeScript
import { image } from '@kit.ImageKit';
```

## generateThumbnailIfAbsent

```TypeScript
generateThumbnailIfAbsent?: boolean
```

Flag to specify whether the thumbnail should be generated, if the image does not have a thumbnail.

<br>Default value: true.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.ImageSource

## maxGeneratedPixelDimension

```TypeScript
maxGeneratedPixelDimension?: number
```

This parameter is valid only when generateThumbnailIfAbsent is set to true. The width and height of the image cannot exceed the value of this parameter. The value should be an integer. <br>Unit:px. <br>Default value:512.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.ImageSource
