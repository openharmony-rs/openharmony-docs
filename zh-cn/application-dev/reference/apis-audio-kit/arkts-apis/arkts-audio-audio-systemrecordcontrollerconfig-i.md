# SystemRecordControllerConfig

系统录音控制面板的配置信息。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## sourceType

```TypeScript
sourceType: SourceType
```

应用期望使用的音频源类型。系统会根据该参数确定应用的录音场景，并为用户提供匹配的降噪模式选择能力。支持的音频源类型包括SOURCE_TYPE_MIC、SOURCE_TYPE_CAMCORDER和SOURCE_TYPE_LIVE 。

**类型：** SourceType

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer
