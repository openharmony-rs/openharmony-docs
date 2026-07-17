# NativeMediaPlayerHandler

[CreateNativeMediaPlayerCallback](arkts-arkweb-webview-createnativemediaplayercallback-t.md)回调函数的参数。应用通过该对象，将播放器的状态通知给 ArkWeb 内核。

> **说明：**  
>  
> - 本Interface首批接口从API version 12开始支持。  
>  
> - 示例效果请以真机运行为准。

**起始版本：** 12

<!--Device-webview-interface NativeMediaPlayerHandler--><!--Device-webview-interface NativeMediaPlayerHandler-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## handleBufferedEndTimeChanged

```TypeScript
handleBufferedEndTimeChanged(bufferedEndTime: number): void
```

当媒体的缓冲时长发生变化时，调用该方法将媒体的缓冲时长通知给 ArkWeb 内核。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NativeMediaPlayerHandler-handleBufferedEndTimeChanged(bufferedEndTime: number): void--><!--Device-NativeMediaPlayerHandler-handleBufferedEndTimeChanged(bufferedEndTime: number): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bufferedEndTime | number | 是 | 媒体缓冲的时长。<br>单位：秒，取值范围：[0, duration] |

## handleDurationChanged

```TypeScript
handleDurationChanged(duration: number): void
```

当播放器解析出媒体的总时长时，调用该方法将媒体的总时长通知给 ArkWeb 内核。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NativeMediaPlayerHandler-handleDurationChanged(duration: number): void--><!--Device-NativeMediaPlayerHandler-handleDurationChanged(duration: number): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| duration | number | 是 | 媒体的总时长。<br>单位：秒，取值范围：[0, +∞) |

## handleEnded

```TypeScript
handleEnded(): void
```

当媒体播放结束时，调用该方法将播放结束事件通知给 ArkWeb 内核。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NativeMediaPlayerHandler-handleEnded(): void--><!--Device-NativeMediaPlayerHandler-handleEnded(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## handleError

```TypeScript
handleError(error: MediaError, errorMessage: string): void
```

当播放器发生错误时，调用该方法将错误通知 ArkWeb 内核。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NativeMediaPlayerHandler-handleError(error: MediaError, errorMessage: string): void--><!--Device-NativeMediaPlayerHandler-handleError(error: MediaError, errorMessage: string): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| error | [MediaError](arkts-arkweb-webview-mediaerror-e.md) | 是 | 错误类型。 |
| errorMessage | string | 是 | 错误的详细描述。 |

## handleFullscreenChanged

```TypeScript
handleFullscreenChanged(fullscreen: boolean): void
```

当播放器的全屏状态发生变化时，调用该方法将播放器的全屏状态通知给 ArkWeb 内核。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NativeMediaPlayerHandler-handleFullscreenChanged(fullscreen: boolean): void--><!--Device-NativeMediaPlayerHandler-handleFullscreenChanged(fullscreen: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fullscreen | boolean | 是 | 是否全屏。<br>true表示全屏，false表示未全屏。 |

## handleMutedChanged

```TypeScript
handleMutedChanged(muted: boolean): void
```

当播放器的静音状态发生变化时，调用该方法将静音状态通知给 ArkWeb 内核。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NativeMediaPlayerHandler-handleMutedChanged(muted: boolean): void--><!--Device-NativeMediaPlayerHandler-handleMutedChanged(muted: boolean): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| muted | boolean | 是 | 当前播放器是否静音。<br>true表示当前播放器静音，false表示当前播放器未静音。 |

## handleNetworkStateChanged

```TypeScript
handleNetworkStateChanged(state: NetworkState): void
```

当播放器的网络状态发生变化时，调用该方法将播放器的网络状态通知给 ArkWeb 内核。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NativeMediaPlayerHandler-handleNetworkStateChanged(state: NetworkState): void--><!--Device-NativeMediaPlayerHandler-handleNetworkStateChanged(state: NetworkState): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| state | [NetworkState](arkts-arkweb-webview-networkstate-e.md) | 是 | 播放器的网络状态。 |

## handlePlaybackRateChanged

```TypeScript
handlePlaybackRateChanged(playbackRate: number): void
```

当播放器的播放速率发生变化时，调用该方法将播放速率通知给 ArkWeb 内核。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NativeMediaPlayerHandler-handlePlaybackRateChanged(playbackRate: number): void--><!--Device-NativeMediaPlayerHandler-handlePlaybackRateChanged(playbackRate: number): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| playbackRate | number | 是 | 播放速率，取值范围：[0, +∞) |

## handleReadyStateChanged

```TypeScript
handleReadyStateChanged(state: ReadyState): void
```

当播放器的缓存状态发生变化时，调用该方法将播放器的缓存状态通知给 ArkWeb 内核。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NativeMediaPlayerHandler-handleReadyStateChanged(state: ReadyState): void--><!--Device-NativeMediaPlayerHandler-handleReadyStateChanged(state: ReadyState): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| state | [ReadyState](arkts-arkweb-webview-readystate-e.md) | 是 | 播放器的缓存状态。 |

## handleSeekFinished

```TypeScript
handleSeekFinished(): void
```

当播放器seek完成后，调用该方法将seek完成事件通知 ArkWeb 内核。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NativeMediaPlayerHandler-handleSeekFinished(): void--><!--Device-NativeMediaPlayerHandler-handleSeekFinished(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## handleSeeking

```TypeScript
handleSeeking(): void
```

当播放器进入seek状态时，调用该方法将seek进入事件通知 ArkWeb 内核。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NativeMediaPlayerHandler-handleSeeking(): void--><!--Device-NativeMediaPlayerHandler-handleSeeking(): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## handleStatusChanged

```TypeScript
handleStatusChanged(status: PlaybackStatus): void
```

当播放器的播放状态发生变化时，调用该方法将播放状态通知给 ArkWeb 内核。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NativeMediaPlayerHandler-handleStatusChanged(status: PlaybackStatus): void--><!--Device-NativeMediaPlayerHandler-handleStatusChanged(status: PlaybackStatus): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| status | [PlaybackStatus](arkts-arkweb-webview-playbackstatus-e.md) | 是 | 播放器的播放状态。 |

## handleTimeUpdate

```TypeScript
handleTimeUpdate(currentPlayTime: number): void
```

当媒体的播放进度发生变化时，调用该方法将媒体的播放进度通知给 ArkWeb 内核。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NativeMediaPlayerHandler-handleTimeUpdate(currentPlayTime: number): void--><!--Device-NativeMediaPlayerHandler-handleTimeUpdate(currentPlayTime: number): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| currentPlayTime | number | 是 | 当前播放时间。<br>单位：秒，取值范围：[0, duration] |

## handleVideoSizeChanged

```TypeScript
handleVideoSizeChanged(width: number, height: number): void
```

当播放器解析出视频的尺寸时， 调用该方法将视频尺寸通知 ArkWeb 内核。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NativeMediaPlayerHandler-handleVideoSizeChanged(width: number, height: number): void--><!--Device-NativeMediaPlayerHandler-handleVideoSizeChanged(width: number, height: number): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| width | number | 是 | 视频的宽，单位：像素，取值范围：[0, +∞) |
| height | number | 是 | 视频的高，单位：像素，取值范围：[0, +∞) |

## handleVolumeChanged

```TypeScript
handleVolumeChanged(volume: number): void
```

当播放器的音量发生变化时，调用该方法将音量通知给 ArkWeb 内核。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NativeMediaPlayerHandler-handleVolumeChanged(volume: number): void--><!--Device-NativeMediaPlayerHandler-handleVolumeChanged(volume: number): void-End-->

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volume | number | 是 | 播放器的音量，取值范围：[0, 1.0]。 |

