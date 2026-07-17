# AudioRendererOptions

音频渲染器选项信息。

**起始版本：** 8

<!--Device-audio-interface AudioRendererOptions--><!--Device-audio-interface AudioRendererOptions-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## privacyType

```TypeScript
privacyType?: AudioPrivacyType
```

表示音频流是否可以被其他应用录制，默认值为0。

**类型：** AudioPrivacyType

**起始版本：** 10

<!--Device-AudioRendererOptions-privacyType?: AudioPrivacyType--><!--Device-AudioRendererOptions-privacyType?: AudioPrivacyType-End-->

**系统能力：** SystemCapability.Multimedia.Audio.PlaybackCapture

## rendererInfo

```TypeScript
rendererInfo: AudioRendererInfo
```

音频渲染器信息。

**类型：** AudioRendererInfo

**起始版本：** 8

<!--Device-AudioRendererOptions-rendererInfo: AudioRendererInfo--><!--Device-AudioRendererOptions-rendererInfo: AudioRendererInfo-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

## streamInfo

```TypeScript
streamInfo: AudioStreamInfo
```

音频流信息。

**类型：** AudioStreamInfo

**起始版本：** 8

<!--Device-AudioRendererOptions-streamInfo: AudioStreamInfo--><!--Device-AudioRendererOptions-streamInfo: AudioStreamInfo-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

