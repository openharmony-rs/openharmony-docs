# ImageReceiverOptions

Describes the initialization options for ImageReceiver.

**Since:** 23

**System capability:** SystemCapability.Multimedia.Image.ImageReceiver

## Modules to Import

```TypeScript
import { image } from '@kit.ImageKit';
```

## capacity

```TypeScript
capacity?: number
```

Maximum number of images that can be accessed simultaneously. The value range is all integers, The value must be a positive integer less than or equal to 64.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.ImageReceiver

## size

```TypeScript
size?: Size
```

Image size, with both the width and height greater than 0.

**Type:** Size

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.ImageReceiver
