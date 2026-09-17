# PackingOptionsForSequence

Defines the options for encoding animated images.

**Since:** 18

**System capability:** SystemCapability.Multimedia.Image.ImagePacker

## Modules to Import

```TypeScript
import { image } from '@kit.ImageKit';
```

## delayTimeList

```TypeScript
delayTimeList: Array<number>
```

Delay time of each frame in GIF encoding. The value must be greater than 0.

The unit is 10 milliseconds. For example, if this parameter is set to 10, the actual delay per frame is 100 ms.

If the array length is less than **frameCount**, the last value in the array will be used for the remaining frames.

**Type:** Array&lt;number&gt;

**Since:** 18

**System capability:** SystemCapability.Multimedia.Image.ImagePacker

## disposalTypes

```TypeScript
disposalTypes?: Array<number>
```

Array that defines how each image frame transitions. If the array length is less than **frameCount**, the last value in the array will be used for the remaining frames. The values can be:

- **0**: No operation is required.  
- **1**: Keeps the image unchanged.  
- **2**: Restores the background color.  
- **3**: Restores to the previous state.

**Type:** Array&lt;number&gt;

**Since:** 18

**System capability:** SystemCapability.Multimedia.Image.ImagePacker

## frameCount

```TypeScript
frameCount: number
```

Number of frames specified in GIF encoding.

**Type:** number

**Since:** 18

**System capability:** SystemCapability.Multimedia.Image.ImagePacker

## loopCount

```TypeScript
loopCount?: number
```

Number of times that the output image in GIF encoding loops. The value range is [0, 65535].

The value **0** means an infinite loop. If this field is not carried, loop playback is not performed.

**Type:** number

**Since:** 18

**System capability:** SystemCapability.Multimedia.Image.ImagePacker
