# AVPlaybackState

媒体播放状态的相关属性。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-avSession-interface AVPlaybackState--><!--Device-avSession-interface AVPlaybackState-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## activeItemId

```TypeScript
activeItemId?: int
```

正在播放的媒体ID。

**类型：** int

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVPlaybackState-activeItemId?: int--><!--Device-AVPlaybackState-activeItemId?: int-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## bufferedTime

```TypeScript
bufferedTime?: long
```

缓冲时间。

**类型：** long

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVPlaybackState-bufferedTime?: long--><!--Device-AVPlaybackState-bufferedTime?: long-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## duration

```TypeScript
duration?: int
```

当前媒体资源的时长，单位为毫秒（ms）。

**类型：** int

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-AVPlaybackState-duration?: int--><!--Device-AVPlaybackState-duration?: int-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## extras

```TypeScript
extras?: {[key: string]: Object}
```

自定义媒体数据。

**类型：** {[key: string]: Object}

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVPlaybackState-extras?: {[key: string]: Object}--><!--Device-AVPlaybackState-extras?: {[key: string]: Object}-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## isFavorite

```TypeScript
isFavorite?: boolean
```

表示是否收藏。true表示收藏，false表示不收藏。

**类型：** boolean

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVPlaybackState-isFavorite?: boolean--><!--Device-AVPlaybackState-isFavorite?: boolean-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## loopMode

```TypeScript
loopMode?: LoopMode
```

循环模式。

**类型：** LoopMode

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVPlaybackState-loopMode?: LoopMode--><!--Device-AVPlaybackState-loopMode?: LoopMode-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## maxVolume

```TypeScript
maxVolume?: int
```

最大音量。

**类型：** int

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVPlaybackState-maxVolume?: int--><!--Device-AVPlaybackState-maxVolume?: int-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## muted

```TypeScript
muted?: boolean
```

当前是否是静音状态。true表示是，false表示不是。

**类型：** boolean

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVPlaybackState-muted?: boolean--><!--Device-AVPlaybackState-muted?: boolean-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## position

```TypeScript
position?: PlaybackPosition
```

播放位置。

**类型：** PlaybackPosition

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVPlaybackState-position?: PlaybackPosition--><!--Device-AVPlaybackState-position?: PlaybackPosition-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## speed

```TypeScript
speed?: double
```

播放倍速。

**类型：** double

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVPlaybackState-speed?: double--><!--Device-AVPlaybackState-speed?: double-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## state

```TypeScript
state?: PlaybackState
```

播放状态。

**类型：** PlaybackState

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVPlaybackState-state?: PlaybackState--><!--Device-AVPlaybackState-state?: PlaybackState-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## videoHeight

```TypeScript
videoHeight?: int
```

媒体资源的视频高度，单位为像素（px）。

**类型：** int

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVPlaybackState-videoHeight?: int--><!--Device-AVPlaybackState-videoHeight?: int-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## videoWidth

```TypeScript
videoWidth?: int
```

媒体资源的视频宽度，单位为像素（px）。

**类型：** int

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVPlaybackState-videoWidth?: int--><!--Device-AVPlaybackState-videoWidth?: int-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

## volume

```TypeScript
volume?: int
```

正在播放的媒体音量。

**类型：** int

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVPlaybackState-volume?: int--><!--Device-AVPlaybackState-volume?: int-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

