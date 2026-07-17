# SubtitleInfo

Provides subtitle information. When a subtitle update event is subscribed to, the information about the external subtitle is returned through a callback.Can be synchronized to the time reported by AVPlayer#timeUpdate event

**起始版本：** 12

<!--Device-unnamed-interface SubtitleInfo--><!--Device-unnamed-interface SubtitleInfo-End-->

**系统能力：** SystemCapability.Multimedia.Media.Core

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

## duration

```TypeScript
duration?: number
```

Duration of the text to be displayed, as milliseconds.

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SubtitleInfo-duration?: int--><!--Device-SubtitleInfo-duration?: int-End-->

**系统能力：** SystemCapability.Multimedia.Media.Core

## startTime

```TypeScript
startTime?: number
```

Display start time of the text, as milliseconds.

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SubtitleInfo-startTime?: int--><!--Device-SubtitleInfo-startTime?: int-End-->

**系统能力：** SystemCapability.Multimedia.Media.Core

## text

```TypeScript
text?: string
```

Text information of current update event.

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SubtitleInfo-text?: string--><!--Device-SubtitleInfo-text?: string-End-->

**系统能力：** SystemCapability.Multimedia.Media.Core

