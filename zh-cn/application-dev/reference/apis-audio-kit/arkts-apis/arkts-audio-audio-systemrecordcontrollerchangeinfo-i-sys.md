# SystemRecordControllerChangeInfo（系统接口）

定义系统记录控制器状态变化时所携带的信息。 它包括启用状态、应用程序UID和预期的音频源类型。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## enabled

```TypeScript
enabled: boolean
```

系统记录控制器面板是否启用。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

## sourceType

```TypeScript
sourceType?: SourceType
```

应用程序在启用录音控制器时配置的预期音频源类型。 用于匹配相应的录音场景和降噪模式。

**类型：** SourceType

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

## uid

```TypeScript
uid?: number
```

触发系统记录控制器状态变化的应用程序UID。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。
