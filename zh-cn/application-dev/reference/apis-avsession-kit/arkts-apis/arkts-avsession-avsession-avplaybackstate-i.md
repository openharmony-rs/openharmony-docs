# AVPlaybackState

媒体播放状态的相关属性。

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## 导入模块

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

## activeItemId

```TypeScript
activeItemId?: number
```

正在播放的媒体ID。

**类型：** number

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## bufferedTime

```TypeScript
bufferedTime?: number
```

缓冲时间。

**类型：** number

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## duration

```TypeScript
duration?: number
```

当前媒体资源的时长，单位为毫秒（ms）。

**类型：** number

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## extras

```TypeScript
extras?: {[key: string]: Object}
```

自定义媒体数据。

**类型：** {[key: string]: Object}

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## isFavorite

```TypeScript
isFavorite?: boolean
```

表示是否收藏。true表示收藏，false表示不收藏。

**类型：** boolean

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## loopMode

```TypeScript
loopMode?: LoopMode
```

循环模式。

**类型：** [LoopMode](arkts-avsession-avsession-loopmode-e.md)

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## maxVolume

```TypeScript
maxVolume?: number
```

最大音量。

**类型：** number

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## muted

```TypeScript
muted?: boolean
```

当前是否是静音状态。true表示是，false表示不是。

**类型：** boolean

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## position

```TypeScript
position?: PlaybackPosition
```

播放位置。

**类型：** [PlaybackPosition](arkts-avsession-avsession-playbackposition-i.md)

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## speed

```TypeScript
speed?: number
```

播放倍速。

**类型：** number

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## state

```TypeScript
state?: PlaybackState
```

播放状态。

**类型：** PlaybackState

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## videoHeight

```TypeScript
videoHeight?: number
```

媒体资源的视频高度，单位为像素（px）。

**类型：** number

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## videoWidth

```TypeScript
videoWidth?: number
```

媒体资源的视频宽度，单位为像素（px）。

**类型：** number

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## volume

```TypeScript
volume?: number
```

正在播放的媒体音量。

**类型：** number

**起始版本：** 10

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.AVSession.Core
