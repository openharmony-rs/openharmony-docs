# AVTimedMetaData

描述基于时间的元数据的信息。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Multimedia.Media.Core

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

## classify

```TypeScript
classify?: string
```

基于时间的元数据的分类标签。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

## contents

```TypeScript
contents: Record<string, object>
```

基于时间的元数据对应的键值对集合。

**类型：** Record&lt;string, object&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

## duration

```TypeScript
duration: number
```

基于时间的元数据的持续时长。取值限定为整数。<br>单位：毫秒。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

## id

```TypeScript
id?: string
```

基于时间的元数据的唯一标记。该标记在视频源的数据信息中须保持唯一。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

## start

```TypeScript
start: number
```

基于时间的元数据相对整个媒体起始时间的偏移值。取值限定为整数。<br>单位：毫秒。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.Core
