# AVTimedMetaData

Interface for defining time base metadata

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Multimedia.Media.Core

## classify

```TypeScript
classify?: string
```

The classification label of the time base metadata.

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

## contents

```TypeScript
contents: Record<string, object>
```

Key-value pair set corresponding to time primitive information

**类型：** Record<string, object>

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

## duration

```TypeScript
duration: number
```

Duration of the time primitive information
The value should be an integer.
<br>Unit:milliseconds.

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

## id

```TypeScript
id?: string
```

Defines the unique token of the time base metadata,
The tag must be unique in other time metadata of the video source.

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

## start

```TypeScript
start: number
```

Defines the offset value of the time primitive information relative to the start time of the entire media.
The value should be an integer.
<br>Unit:milliseconds.

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

