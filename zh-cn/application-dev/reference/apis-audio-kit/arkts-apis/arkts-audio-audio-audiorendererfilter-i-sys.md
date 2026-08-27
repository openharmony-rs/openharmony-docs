# AudioRendererFilter（系统接口）

音频渲染器过滤条件。

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Audio.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## rendererId

```TypeScript
rendererId?: number
```

音频流唯一id。SystemCapability.Multimedia.Audio.Renderer

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**系统接口：** 此接口为系统接口。

## rendererInfo

```TypeScript
rendererInfo?: AudioRendererInfo
```

表示渲染器信息。SystemCapability.Multimedia.Audio.Renderer

**类型：** [AudioRendererInfo](arkts-audio-audio-audiorendererinfo-i.md)

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

**系统接口：** 此接口为系统接口。

## uid

```TypeScript
uid?: number
```

表示应用ID。SystemCapability.Multimedia.Audio.Core

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Audio.Core

**系统接口：** 此接口为系统接口。

**示例**

```TypeScript
import { audio } from '@kit.AudioKit';

let outputAudioRendererFilter: audio.AudioRendererFilter = {
  uid : 20010041,
  rendererInfo : {
    usage : audio.StreamUsage.STREAM_USAGE_MUSIC,
    rendererFlags : 0
  },
  rendererId : 0
};
```
