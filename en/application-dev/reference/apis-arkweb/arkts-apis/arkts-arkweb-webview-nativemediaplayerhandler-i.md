# NativeMediaPlayerHandler

NativeMediaPlayerHandler is the parameter of the [CreateNativeMediaPlayerCallback](arkts-arkweb-webview-createnativemediaplayercallback-t.md) callback function. When an app uses [NativeMediaPlayerBridge](arkts-arkweb-webview-nativemediaplayerbridge-i.md) to take over web media playback, it must synchronize various player state changes to the ArkWeb kernel in real time. This ensures that the web JavaScript can obtain the correct player state. The ArkWeb kernel converts these states into standard HTML5 Media Events and triggers the event listeners registered in the web page, thereby ensuring the normal functioning of the web page.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## Modules to Import

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## handleBufferedEndTimeChanged

```TypeScript
handleBufferedEndTimeChanged(bufferedEndTime: number): void
```

Called to notify the ArkWeb engine of the buffer time when the buffer time changes.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bufferedEndTime | number | Yes | Duration of the buffered media.<br>Unit: second. Value range: [0, duration]. If the value is out of range, the ArkWeb kernel will not execute. |

## handleDurationChanged

```TypeScript
handleDurationChanged(duration: number): void
```

Called to notify the ArkWeb engine of the total duration of the media.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| duration | number | Yes | Total duration of the media.<br>Unit: second. Value range: [0, +∞). If a negative number is passed in, the ArkWeb kernel will not execute. |

## handleEnded

```TypeScript
handleEnded(): void
```

When media playback ends, this method is called to notify the ArkWeb kernel of the playback end event.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## handleError

```TypeScript
handleError(error: MediaError, errorMessage: string): void
```

When an error occurs in the player, this method is called to notify the ArkWeb kernel of the error.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| error | [MediaError](arkts-arkweb-webview-mediaerror-e.md) | Yes | Error object type. |
| errorMessage | string | Yes | Error message. |

## handleFullscreenChanged

```TypeScript
handleFullscreenChanged(fullscreen: boolean): void
```

Called to notify the ArkWeb engine of the full screen status of the player when the full screen status changes.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fullscreen | boolean | Yes | Whether the player is in full screen.<br>The value **true** means that the player is in full screen, and **false** means the opposite. |

## handleMutedChanged

```TypeScript
handleMutedChanged(muted: boolean): void
```

Called to notify the ArkWeb engine of the muted status of the player when the muted status changes.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| muted | boolean | Yes | Whether the player is muted.<br>The value **true** indicates that the player is muted, and **false** indicates the opposite. |

## handleNetworkStateChanged

```TypeScript
handleNetworkStateChanged(state: NetworkState): void
```

Called to notify the ArkWeb engine of the network status of the player when the network status changes.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| state | [NetworkState](arkts-arkweb-webview-networkstate-e.md) | Yes | Network status of the player. |

## handlePlaybackRateChanged

```TypeScript
handlePlaybackRateChanged(playbackRate: number): void
```

When the playback rate of the player changes, this method is called to notify the ArkWeb kernel of the playback rate.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| playbackRate | number | Yes | Playback rate. The value range is [0, +∞). If a negative number is passed in, the ArkWeb kernel will not execute it. |

## handleReadyStateChanged

```TypeScript
handleReadyStateChanged(state: ReadyState): void
```

Called to notify the ArkWeb engine of the cache status of the player when the cache status changes.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| state | [ReadyState](arkts-arkweb-webview-readystate-e.md) | Yes | Cache status of the player. |

## handleSeekFinished

```TypeScript
handleSeekFinished(): void
```

When the player completes seeking, this method is called to notify the ArkWeb kernel of the seek completion event.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## handleSeeking

```TypeScript
handleSeeking(): void
```

When the player enters the seek state, this method is called to notify the ArkWeb kernel of the seek entry event. After the seek is complete, handleSeekFinished should be called to notify the ArkWeb kernel of the seek completion event.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## handleStatusChanged

```TypeScript
handleStatusChanged(status: PlaybackStatus): void
```

Called to notify the ArkWeb engine of the playback status of the player when the playback status changes.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| status | [PlaybackStatus](arkts-arkweb-webview-playbackstatus-e.md) | Yes | Player status. |

## handleTimeUpdate

```TypeScript
handleTimeUpdate(currentPlayTime: number): void
```

Called to notify the ArkWeb engine of the playback progress when the playback progress changes.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| currentPlayTime | number | Yes | Current playback time.<br>Unit: second. Value range: [0, duration]. If the value is out of range, the ArkWeb kernel will not execute it. |

## handleVideoSizeChanged

```TypeScript
handleVideoSizeChanged(width: number, height: number): void
```

When the player parses the video dimensions, this method is called to notify the ArkWeb kernel of the video size.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| width | number | Yes | Width of the video, in pixels. Value range: [0, +∞). If a negative number is passed in, the ArkWeb kernel ignores this value. |
| height | number | Yes | Height of the video, in pixels. Value range: [0, +∞). If a negative number is passed in, the ArkWeb kernel ignores this value. |

## handleVolumeChanged

```TypeScript
handleVolumeChanged(volume: number): void
```

Called to notify the ArkWeb engine of the volume of the player when the volume changes.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| volume | number | Yes | Volume of the player. Value range: [0, 1.0]. If the value is out of range, the ArkWeb kernel will not execute it. |
