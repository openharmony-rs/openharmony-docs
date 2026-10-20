# AudioSeparationEffectAvailableStatus（系统接口）

```TypeScript
interface AudioSeparationEffectAvailableStatus
```

音频分离效果可用状态。

**起始版本：** 26.0.1

<!--Device-audio-interface AudioSeparationEffectAvailableStatus--><!--Device-audio-interface AudioSeparationEffectAvailableStatus-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## appUid

```TypeScript
appUid?: number
```

可用状态对应的应用uid。通常为当前播控应用中显示的应用。取值限定为整数。

**类型：** number

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioSeparationEffectAvailableStatus-appUid?: int--><!--Device-AudioSeparationEffectAvailableStatus-appUid?: int-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

**系统接口：** 此接口为系统接口。

## available

```TypeScript
available: boolean
```

可用状态。播控应用可根据此状态决定是否显示音频分离开关按钮。

**类型：** boolean

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AudioSeparationEffectAvailableStatus-available: boolean--><!--Device-AudioSeparationEffectAvailableStatus-available: boolean-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

**系统接口：** 此接口为系统接口。
