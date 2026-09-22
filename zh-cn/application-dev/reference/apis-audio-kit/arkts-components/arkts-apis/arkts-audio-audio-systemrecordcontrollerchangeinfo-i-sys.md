# SystemRecordControllerChangeInfo（系统接口）

```TypeScript
interface SystemRecordControllerChangeInfo
```

系统录音控制面板状态变更时携带的信息，包含使能状态、应用UID和期望的音频源类型。用于[onSystemRecordControllerEnabledChange](../../../reference/apis-audio-kit/js-apis-audio-sys.md#onsystemrecordcontrollerenabledchange)和[offSystemRecordControllerEnabledChange](../../../reference/apis-audio-kit/js-apis-audio-sys.md#offsystemrecordcontrollerenabledchange)的回调参数。

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

系统录音控制面板是否启用。true表示启用，false表示禁用。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

## sourceType

```TypeScript
sourceType?: SourceType
```

应用启用录音控制面板时配置的期望音频源类型，用于匹配对应的录音场景和降噪模式。

**类型：** [SourceType](arkts-audio-audio-sourcetype-e.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。

## uid

```TypeScript
uid?: number
```

触发系统录音控制面板状态变更的应用UID。取值范围是所有整数。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

**系统接口：** 此接口为系统接口。
