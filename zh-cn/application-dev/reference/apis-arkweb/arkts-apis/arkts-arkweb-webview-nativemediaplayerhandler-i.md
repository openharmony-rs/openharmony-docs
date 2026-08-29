# NativeMediaPlayerHandler

NativeMediaPlayerHandler 是[CreateNativeMediaPlayerCallback](arkts-arkweb-webview-createnativemediaplayercallback-t.md)回调函数的参数。当 应用使用[NativeMediaPlayerBridge](arkts-arkweb-webview-nativemediaplayerbridge-i.md)接管网页媒体播放时，需要通过将播放器的各种状态变化实时同步给 ArkWeb 内核，确保网页 JavaScript 能够获取正确的播放器状态，ArkWeb 内核会将这些状态转换为标准的 HTML5 Media Events，触发网页中注册的事件监听器，从而保证网页功能的正常运行。

**起始版本：** 12

**系统能力：** SystemCapability.Web.Webview.Core

## 导入模块

```TypeScript
```

## handleBufferedEndTimeChanged

```TypeScript
handleBufferedEndTimeChanged(bufferedEndTime: number): void
```

当媒体的缓冲时长发生变化时，调用该方法将媒体的缓冲时长通知给 ArkWeb 内核。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bufferedEndTime | number | 是 | 媒体缓冲的时长。 单位：秒，取值范围：[0, duration]。超出范围时，ArkWeb 内核将不会执行。 |

**示例**

完整示例代码参考onCreateNativeMediaPlayer。

## handleDurationChanged

```TypeScript
handleDurationChanged(duration: number): void
```

当播放器解析出媒体的总时长时，调用该方法将媒体的总时长通知给 ArkWeb 内核。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| duration | number | 是 | 媒体的总时长。 单位：秒，取值范围：[0, +∞)。传入负数时，ArkWeb 内核将不会执行。 |

**示例**

完整示例代码参考onCreateNativeMediaPlayer。

## handleEnded

```TypeScript
handleEnded(): void
```

当媒体播放结束时，调用该方法将播放结束事件通知给 ArkWeb 内核。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**示例**

完整示例代码参考onCreateNativeMediaPlayer。

## handleError

```TypeScript
handleError(error: MediaError, errorMessage: string): void
```

当播放器发生错误时，调用该方法将错误通知给 ArkWeb 内核。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| error | [MediaError](arkts-arkweb-webview-mediaerror-e.md) | 是 | 错误类型。 |
| errorMessage | string | 是 | 错误的详细描述。 |

**示例**

完整示例代码参考onCreateNativeMediaPlayer。

## handleFullscreenChanged

```TypeScript
handleFullscreenChanged(fullscreen: boolean): void
```

当播放器的全屏状态发生变化时，调用该方法将播放器的全屏状态通知给 ArkWeb 内核。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fullscreen | boolean | 是 | 是否全屏。 true表示全屏，false表示未全屏。 |

**示例**

完整示例代码参考onCreateNativeMediaPlayer。

## handleMutedChanged

```TypeScript
handleMutedChanged(muted: boolean): void
```

当播放器的静音状态发生变化时，调用该方法将静音状态通知给 ArkWeb 内核。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| muted | boolean | 是 | 当前播放器是否静音。 true表示当前播放器静音，false表示当前播放器未静音。 |

**示例**

完整示例代码参考onCreateNativeMediaPlayer。

## handleNetworkStateChanged

```TypeScript
handleNetworkStateChanged(state: NetworkState): void
```

当播放器的网络状态发生变化时，调用该方法将播放器的网络状态通知给 ArkWeb 内核。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| state | NetworkState | 是 | 播放器的网络状态。 |

**示例**

完整示例代码参考onCreateNativeMediaPlayer。

## handlePlaybackRateChanged

```TypeScript
handlePlaybackRateChanged(playbackRate: number): void
```

当播放器的播放速率发生变化时，调用该方法将播放速率通知给 ArkWeb 内核。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| playbackRate | number | 是 | 播放速率，取值范围：[0, +∞)。传入负数时，ArkWeb 内核将不会执行。 |

**示例**

完整示例代码参考onCreateNativeMediaPlayer。

## handleReadyStateChanged

```TypeScript
handleReadyStateChanged(state: ReadyState): void
```

当播放器的缓存状态发生变化时，调用该方法将播放器的缓存状态通知给 ArkWeb 内核。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| state | [ReadyState](arkts-arkweb-webview-readystate-e.md) | 是 | 播放器的缓存状态。 |

**示例**

完整示例代码参考onCreateNativeMediaPlayer。

## handleSeekFinished

```TypeScript
handleSeekFinished(): void
```

当播放器 seek 完成后，调用该方法将 seek 完成事件通知给 ArkWeb 内核。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**示例**

完整示例代码参考onCreateNativeMediaPlayer。

## handleSeeking

```TypeScript
handleSeeking(): void
```

当播放器进入 seek 状态时，调用该方法将 seek 进入事件通知 ArkWeb 内核。seek 完成后，应调用 handleSeekFinished 将 seek 完成事件通知 ArkWeb 内核。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**示例**

完整示例代码参考onCreateNativeMediaPlayer。

## handleStatusChanged

```TypeScript
handleStatusChanged(status: PlaybackStatus): void
```

当播放器的播放状态发生变化时，调用该方法将播放状态通知给 ArkWeb 内核。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| status | [PlaybackStatus](arkts-arkweb-webview-playbackstatus-e.md) | 是 | 播放器的播放状态。 |

**示例**

完整示例代码参考onCreateNativeMediaPlayer。

## handleTimeUpdate

```TypeScript
handleTimeUpdate(currentPlayTime: number): void
```

当媒体的播放进度发生变化时，调用该方法将媒体的播放进度通知给 ArkWeb 内核。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| currentPlayTime | number | 是 | 当前播放时间。 单位：秒，取值范围：[0, duration]。超出范围时，ArkWeb 内核将不会执行。 |

**示例**

完整示例代码参考onCreateNativeMediaPlayer。

## handleVideoSizeChanged

```TypeScript
handleVideoSizeChanged(width: number, height: number): void
```

当播放器解析出视频的尺寸时，调用该方法将视频尺寸通知给 ArkWeb 内核。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| width | number | 是 | 视频的宽，单位：像素，取值范围：[0, +∞)。传入负数时，ArkWeb 内核将忽略该值。 |
| height | number | 是 | 视频的高，单位：像素，取值范围：[0, +∞)。传入负数时，ArkWeb 内核将忽略该值。 |

**示例**

完整示例代码参考onCreateNativeMediaPlayer。

## handleVolumeChanged

```TypeScript
handleVolumeChanged(volume: number): void
```

当播放器的音量发生变化时，调用该方法将音量通知给 ArkWeb 内核。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Web.Webview.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| volume | number | 是 | 播放器的音量，取值范围：[0, 1.0]。超出范围时，ArkWeb 内核将不会执行。 |

**示例**

完整示例代码参考onCreateNativeMediaPlayer。
