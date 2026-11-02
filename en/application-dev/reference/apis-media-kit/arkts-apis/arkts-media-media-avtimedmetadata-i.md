# AVTimedMetaData

```TypeScript
interface AVTimedMetaData
```

Interface for defining time base metadata

**Since:** 26.0.0

<!--Device-media-interface AVTimedMetaData--><!--Device-media-interface AVTimedMetaData-End-->

**System capability:** SystemCapability.Multimedia.Media.Core

## Modules to Import

```TypeScript
import { media } from '@kit.MediaKit';
```

## classify

```TypeScript
classify?: string
```

The classification label of the time base metadata.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AVTimedMetaData-classify?: string--><!--Device-AVTimedMetaData-classify?: string-End-->

**System capability:** SystemCapability.Multimedia.Media.Core

## contents

```TypeScript
contents: Record<string, object>
```

Key-value pair set corresponding to time primitive information

**Type:** Record&lt;string, object&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AVTimedMetaData-contents: Record<string, object>--><!--Device-AVTimedMetaData-contents: Record<string, object>-End-->

**System capability:** SystemCapability.Multimedia.Media.Core

## duration

```TypeScript
duration: number
```

Duration of the time primitive information The value should be an integer. <br>Unit:milliseconds.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AVTimedMetaData-duration: int--><!--Device-AVTimedMetaData-duration: int-End-->

**System capability:** SystemCapability.Multimedia.Media.Core

## id

```TypeScript
id?: string
```

Defines the unique token of the time base metadata, The tag must be unique in other time metadata of the video source.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AVTimedMetaData-id?: string--><!--Device-AVTimedMetaData-id?: string-End-->

**System capability:** SystemCapability.Multimedia.Media.Core

## start

```TypeScript
start: number
```

Defines the offset value of the time primitive information relative to the start time of the entire media. The value should be an integer. <br>Unit:milliseconds.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-AVTimedMetaData-start: int--><!--Device-AVTimedMetaData-start: int-End-->

**System capability:** SystemCapability.Multimedia.Media.Core
