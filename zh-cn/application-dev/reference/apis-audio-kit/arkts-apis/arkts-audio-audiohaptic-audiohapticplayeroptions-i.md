# AudioHapticPlayerOptions

音振播放器选项。

**起始版本：** 11

<!--Device-audioHaptic-interface AudioHapticPlayerOptions--><!--Device-audioHaptic-interface AudioHapticPlayerOptions-End-->

**系统能力：** SystemCapability.Multimedia.AudioHaptic.Core

## 导入模块

```TypeScript
import { audioHaptic } from '@kit.AudioKit';
```

## muteAudio

```TypeScript
muteAudio?: boolean
```

是否将音频静音，true表示将音频静音，false表示正常播放声音。若不填该参数，则默认为false。

**类型：** boolean

**起始版本：** 11

<!--Device-AudioHapticPlayerOptions-muteAudio?: boolean--><!--Device-AudioHapticPlayerOptions-muteAudio?: boolean-End-->

**系统能力：** SystemCapability.Multimedia.AudioHaptic.Core

## muteHaptics

```TypeScript
muteHaptics?: boolean
```

是否禁止振动，true表示将禁止振动，false表示正常振动。若不填该参数，则默认为false。

**类型：** boolean

**起始版本：** 11

<!--Device-AudioHapticPlayerOptions-muteHaptics?: boolean--><!--Device-AudioHapticPlayerOptions-muteHaptics?: boolean-End-->

**系统能力：** SystemCapability.Multimedia.AudioHaptic.Core

