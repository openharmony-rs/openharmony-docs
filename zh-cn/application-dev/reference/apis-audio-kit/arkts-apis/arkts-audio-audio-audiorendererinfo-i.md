# AudioRendererInfo

```TypeScript
interface AudioRendererInfo
```

音频渲染器信息。

**起始版本：** 8

**系统能力：** SystemCapability.Multimedia.Audio.Core

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## content

```TypeScript
content?: ContentType
```

音频内容类型。

**类型：** [ContentType](arkts-audio-audio-contenttype-e.md)

**起始版本：** 8

**废弃版本：** 10

**替代接口：** usage

**系统能力：** SystemCapability.Multimedia.Audio.Core

## rendererFlags

```TypeScript
rendererFlags: number
```

播放流行为标志。

设置为0即可。

**类型：** number

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Audio.Core

## usage

```TypeScript
usage: StreamUsage
```

音频流使用类型。

**类型：** [StreamUsage](arkts-audio-audio-streamusage-e.md)

**起始版本：** 8

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Audio.Core

## volumeMode

```TypeScript
volumeMode?: AudioVolumeMode
```

音频的音量模式。默认值为SYSTEM_GLOBAL。

**类型：** [AudioVolumeMode](arkts-audio-audio-audiovolumemode-e.md)

**起始版本：** 19

**系统能力：** SystemCapability.Multimedia.Audio.Volume
