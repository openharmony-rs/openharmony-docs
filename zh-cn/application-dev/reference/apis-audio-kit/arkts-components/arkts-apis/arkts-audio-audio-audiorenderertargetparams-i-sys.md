# AudioRendererTargetParams（系统接口）

```TypeScript
interface AudioRendererTargetParams
```

设置音频渲染器渲染目标的选项。

> **说明：** 
> 
> - 此参数仅在渲染目标为非[RenderTarget](arkts-audio-audio-rendertarget-e-sys.md).PLAYBACK模式时生效。
> 
> - 在其他模式时，无需指定该参数，即使指定也不生效。
> 
> - uid和streamId必须同时指定。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## streamId

```TypeScript
streamId: number
```

音频流唯一ID。

指定应用ID下[SourceType](./arkts-apis-audio-e.md#sourcetype8)为`SOURCE_TYPE_VOICE_COMMUNICATION`的采集流ID，音频渲染流将注入该采集流。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**系统接口：** 此接口为系统接口。

## uid

```TypeScript
uid: number
```

应用ID。

该值应为整数。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**系统接口：** 此接口为系统接口。
