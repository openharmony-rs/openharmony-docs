# AVTimedMetaData

Interface for defining time base metadata

**起始版本：** 26.0.0

<!--Device-media-interface AVTimedMetaData--><!--Device-media-interface AVTimedMetaData-End-->

**系统能力：** SystemCapability.Multimedia.Media.Core

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

## classify

```TypeScript
classify?: string
```

The classification label of the time base metadata.

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVTimedMetaData-classify?: string--><!--Device-AVTimedMetaData-classify?: string-End-->

**系统能力：** SystemCapability.Multimedia.Media.Core

## contents

```TypeScript
contents: Record<string, object>
```

Key-value pair set corresponding to time primitive information

**类型：** Record<string, object>

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVTimedMetaData-contents: Record<string, object>--><!--Device-AVTimedMetaData-contents: Record<string, object>-End-->

**系统能力：** SystemCapability.Multimedia.Media.Core

## duration

```TypeScript
duration: number
```

Duration of the time primitive information The value should be an integer.<br>Unit:milliseconds.

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVTimedMetaData-duration: int--><!--Device-AVTimedMetaData-duration: int-End-->

**系统能力：** SystemCapability.Multimedia.Media.Core

## id

```TypeScript
id?: string
```

Defines the unique token of the time base metadata,The tag must be unique in other time metadata of the video source.

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVTimedMetaData-id?: string--><!--Device-AVTimedMetaData-id?: string-End-->

**系统能力：** SystemCapability.Multimedia.Media.Core

## start

```TypeScript
start: number
```

Defines the offset value of the time primitive information relative to the start time of the entire media.The value should be an integer.<br>Unit:milliseconds.

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AVTimedMetaData-start: int--><!--Device-AVTimedMetaData-start: int-End-->

**系统能力：** SystemCapability.Multimedia.Media.Core

