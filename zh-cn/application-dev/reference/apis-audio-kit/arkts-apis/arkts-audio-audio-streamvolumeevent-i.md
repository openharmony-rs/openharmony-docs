# StreamVolumeEvent

音频流音量变化时，应用接收到的事件。

**起始版本：** 23

<!--Device-audio-interface StreamVolumeEvent--><!--Device-audio-interface StreamVolumeEvent-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
import { audioHaptic } from '@kit.AudioKit';
```

## previousVolume

```TypeScript
previousVolume?: int
```

变化前的音量值。

**类型：** int

**起始版本：** 23

<!--Device-StreamVolumeEvent-previousVolume?: int--><!--Device-StreamVolumeEvent-previousVolume?: int-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

## streamUsage

```TypeScript
streamUsage: StreamUsage
```

音量发生变化的音频流。

**类型：** [StreamUsage](arkts-audio-audio-streamusage-e.md)

**起始版本：** 23

<!--Device-StreamVolumeEvent-streamUsage: StreamUsage--><!--Device-StreamVolumeEvent-streamUsage: StreamUsage-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

## updateUi

```TypeScript
updateUi: boolean
```

是否在UI上展示音量变化。true表示展示，false表示不展示。

**类型：** boolean

**起始版本：** 23

<!--Device-StreamVolumeEvent-updateUi: boolean--><!--Device-StreamVolumeEvent-updateUi: boolean-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

## volume

```TypeScript
volume: int
```

音量值。

**类型：** int

**起始版本：** 23

<!--Device-StreamVolumeEvent-volume: int--><!--Device-StreamVolumeEvent-volume: int-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Volume

