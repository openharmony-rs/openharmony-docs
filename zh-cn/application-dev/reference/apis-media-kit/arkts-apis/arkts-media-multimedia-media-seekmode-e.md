# SeekMode

视频播放的Seek模式枚举，可通过seek方法作为参数传递下去。

**起始版本：** 8

<!--Device-unnamed-enum SeekMode--><!--Device-unnamed-enum SeekMode-End-->

**系统能力：** SystemCapability.Multimedia.Media.Core

## SEEK_NEXT_SYNC

```TypeScript
SEEK_NEXT_SYNC = 0
```

表示跳转到指定时间点的下一个关键帧，建议向后快进的时候用这个枚举值。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SeekMode-SEEK_NEXT_SYNC = 0--><!--Device-SeekMode-SEEK_NEXT_SYNC = 0-End-->

**系统能力：** SystemCapability.Multimedia.Media.Core

## SEEK_PREV_SYNC

```TypeScript
SEEK_PREV_SYNC = 1
```

表示跳转到指定时间点的上一个关键帧，建议向前快进的时候用这个枚举值。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SeekMode-SEEK_PREV_SYNC = 1--><!--Device-SeekMode-SEEK_PREV_SYNC = 1-End-->

**系统能力：** SystemCapability.Multimedia.Media.Core

## SEEK_CLOSEST

```TypeScript
SEEK_CLOSEST = 2
```

表示跳转到距离指定时间点最近的帧，建议精准跳转进度的时候用这个枚举值。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SeekMode-SEEK_CLOSEST = 2--><!--Device-SeekMode-SEEK_CLOSEST = 2-End-->

**系统能力：** SystemCapability.Multimedia.Media.Core

## SEEK_CONTINUOUS

```TypeScript
SEEK_CONTINUOUS = 3
```

该模式提供了一种画面平滑流畅变化的Seek体验，应用可以结合进度条控件持续调用Seek方法，AVPlayer根据Seek调用持续流畅地更新画面。

应用可以调用[isSeekContinuousSupported](@ohos.multimedia.media:media.AVPlayer.isSeekContinuousSupported)方法根据返回结果感知视频源是否支持该模式Seek。

对于不支持该Seek模式的视频源调用该模式Seek时，会上报AVERR_SEEK_CONTINUOUS_UNSUPPORTED错误(参考[AVErrorCode](arkts-media-media-averrorcode-e.md))，同时画面更新的流畅性会降低。

该Seek模式不会触发[on('seekDone')](@ohos.multimedia.media:media.AVPlayer.on(type: 'seekDone', callback: Callback<int>))事件。

当应用需要退出该模式下的Seek时，需要调用`seek(-1, SeekMode.SEEK_CONTINUOUS)`来结束该模式下的Seek。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SeekMode-SEEK_CONTINUOUS = 3--><!--Device-SeekMode-SEEK_CONTINUOUS = 3-End-->

**系统能力：** SystemCapability.Multimedia.Media.Core

