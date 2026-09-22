# AudioRendererOptions

```TypeScript
interface AudioRendererOptions
```

音频渲染器选项信息。

**起始版本：** 8

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## originalAppIdInfo

```TypeScript
originalAppIdInfo?: AppIdInfo
```

表示音频流的原始应用ID信息，用于系统应用代理其他应用播放音频时设置音频流的归属身份。不传此参数时不设置原始应用ID信息。

**类型：** [AppIdInfo](arkts-audio-audio-appidinfo-i-sys.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**系统接口：** 此接口为系统接口。
