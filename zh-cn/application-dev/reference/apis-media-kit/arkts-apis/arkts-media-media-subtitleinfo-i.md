# SubtitleInfo

提供字幕信息。当订阅了字幕更新事件时，关于外部字幕的信息会通过回调返回。 可以同步到AVPlayer#timeUpdate事件报告的时间

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Media.Core

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

## duration

```TypeScript
duration?: number
```

文本显示的时间长度，以毫秒为单位。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

## startTime

```TypeScript
startTime?: number
```

显示文本的开始时间，以毫秒为单位。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

## text

```TypeScript
text?: string
```

更新事件的文本信息。

**类型：** string

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.Core
