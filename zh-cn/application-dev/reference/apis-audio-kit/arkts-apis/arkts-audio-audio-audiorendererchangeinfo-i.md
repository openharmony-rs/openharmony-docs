# AudioRendererChangeInfo

描述音频渲染器更改信息。

**起始版本：** 9

<!--Device-audio-interface AudioRendererChangeInfo--><!--Device-audio-interface AudioRendererChangeInfo-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## deviceDescriptors

```TypeScript
readonly deviceDescriptors: AudioDeviceDescriptors
```

音频设备描述。

**类型：** AudioDeviceDescriptors

**起始版本：** 9

<!--Device-AudioRendererChangeInfo-readonly deviceDescriptors: AudioDeviceDescriptors--><!--Device-AudioRendererChangeInfo-readonly deviceDescriptors: AudioDeviceDescriptors-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

## rendererInfo

```TypeScript
readonly rendererInfo: AudioRendererInfo
```

音频渲染器信息。

**类型：** AudioRendererInfo

**起始版本：** 9

<!--Device-AudioRendererChangeInfo-readonly rendererInfo: AudioRendererInfo--><!--Device-AudioRendererChangeInfo-readonly rendererInfo: AudioRendererInfo-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

## streamId

```TypeScript
readonly streamId: number
```

音频流唯一id。

**类型：** number

**起始版本：** 9

<!--Device-AudioRendererChangeInfo-readonly streamId: int--><!--Device-AudioRendererChangeInfo-readonly streamId: int-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

