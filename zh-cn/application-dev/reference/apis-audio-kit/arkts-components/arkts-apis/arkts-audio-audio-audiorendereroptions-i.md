# AudioRendererOptions

音频渲染器选项信息。

**起始版本：** 8

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

**类型：** [AudioPrivacyType](arkts-audio-audio-audioprivacytype-e.md)

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.Audio.PlaybackCapture

## rendererInfo

```TypeScript
rendererInfo: AudioRendererInfo
```

音频渲染器信息。

SystemCapability.Multimedia.Audio.Renderer

**类型：** [AudioRendererInfo](arkts-audio-audio-audiorendererinfo-i.md)

**起始版本：** 8

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

## streamInfo

```TypeScript
streamInfo: AudioStreamInfo
```

音频流信息。

SystemCapability.Multimedia.Audio.Renderer

**类型：** [AudioStreamInfo](arkts-audio-audio-audiostreaminfo-i.md)

**起始版本：** 8

**系统能力：** SystemCapability.Multimedia.Audio.Renderer
