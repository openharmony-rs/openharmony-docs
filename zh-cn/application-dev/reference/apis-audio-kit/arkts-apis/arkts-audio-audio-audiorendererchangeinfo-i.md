# AudioRendererChangeInfo

描述音频渲染器更改信息。

**起始版本：** 23

<!--Device-audio-interface AudioRendererChangeInfo--><!--Device-audio-interface AudioRendererChangeInfo-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
import { audioHaptic } from '@kit.AudioKit';
```

## deviceDescriptors

```TypeScript
readonly deviceDescriptors: AudioDeviceDescriptors
```

音频设备描述。

**类型：** [AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md)

**起始版本：** 23

<!--Device-AudioRendererChangeInfo-readonly deviceDescriptors: AudioDeviceDescriptors--><!--Device-AudioRendererChangeInfo-readonly deviceDescriptors: AudioDeviceDescriptors-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

## rendererInfo

```TypeScript
readonly rendererInfo: AudioRendererInfo
```

音频渲染器信息。

**类型：** [AudioRendererInfo](arkts-audio-audio-audiorendererinfo-i.md)

**起始版本：** 23

<!--Device-AudioRendererChangeInfo-readonly rendererInfo: AudioRendererInfo--><!--Device-AudioRendererChangeInfo-readonly rendererInfo: AudioRendererInfo-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

## streamId

```TypeScript
readonly streamId: int
```

音频流唯一id。

**类型：** int

**起始版本：** 23

<!--Device-AudioRendererChangeInfo-readonly streamId: int--><!--Device-AudioRendererChangeInfo-readonly streamId: int-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

