# Interface (NativeMediaPlayerHandler)

<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @zhangyao75477-->
<!--Designer: @gzweioh-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=b2db66489434139fa3bd3ae09bc9cd93d0621bd6 translatedAt=2026-08-07T04:23:54.363Z pushedAt=2026-08-07T08:11:08.058Z -->

NativeMediaPlayerHandler is the parameter of the [CreateNativeMediaPlayerCallback](./arkts-apis-webview-t.md#createnativemediaplayercallback12) callback function. When an app uses [NativeMediaPlayerBridge](./arkts-apis-webview-NativeMediaPlayerBridge.md) to take over web media playback, it must synchronize various player state changes to the ArkWeb kernel in real time. This ensures that the web JavaScript can obtain the correct player state. The ArkWeb kernel converts these states into standard HTML5 Media Events and triggers the event listeners registered in the web page, thereby ensuring the normal functioning of the web page.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 9. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The initial APIs of this interface are supported since API version 12.
>
> - The sample effect is subject to the actual device.

## handleStatusChanged<sup>12+</sup>

handleStatusChanged(status: PlaybackStatus): void

Called to notify the ArkWeb engine of the playback status of the player when the playback status changes.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name| Type| Mandatory| Description|
|--------|------|------|------|
| status | [PlaybackStatus](./arkts-apis-webview-e.md#playbackstatus12) | Yes| Player status.|

**Example**

For details about the sample code, see [onCreateNativeMediaPlayer](./arkts-apis-webview-WebviewController.md#oncreatenativemediaplayer12).

## handleVolumeChanged<sup>12+</sup>

handleVolumeChanged(volume: number): void

Called to notify the ArkWeb engine of the volume of the player when the volume changes.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name| Type| Mandatory| Description|
|--------|------|------|------|
| volume | number | Yes | Volume of the player. Value range: [0, 1.0]. If the value is out of range, the ArkWeb kernel will not execute it. |

**Example**

For details about the sample code, see [onCreateNativeMediaPlayer](./arkts-apis-webview-WebviewController.md#oncreatenativemediaplayer12).

## handleMutedChanged<sup>12+</sup>

handleMutedChanged(muted: boolean): void

Called to notify the ArkWeb engine of the muted status of the player when the muted status changes.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name| Type| Mandatory| Description|
|--------|------|------|------|
| muted | boolean | Yes| Whether the player is muted.<br>The value **true** indicates that the player is muted, and **false** indicates the opposite.|

**Example**

For details about the sample code, see [onCreateNativeMediaPlayer](./arkts-apis-webview-WebviewController.md#oncreatenativemediaplayer12).

## handlePlaybackRateChanged<sup>12+</sup>

handlePlaybackRateChanged(playbackRate: number): void

When the playback rate of the player changes, this method is called to notify the ArkWeb kernel of the playback rate.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name| Type| Mandatory| Description|
|--------|------|------|------|
| playbackRate | number | Yes | Playback rate. The value range is [0, +∞). If a negative number is passed in, the ArkWeb kernel will not execute it.|

**Example**

For details about the sample code, see [onCreateNativeMediaPlayer](./arkts-apis-webview-WebviewController.md#oncreatenativemediaplayer12).

## handleDurationChanged<sup>12+</sup>

handleDurationChanged(duration: number): void

Called to notify the ArkWeb engine of the total duration of the media.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name| Type| Mandatory| Description|
|--------|------|------|------|
| duration | number | Yes | Total duration of the media.<br>Unit: second. Value range: [0, +∞). If a negative number is passed in, the ArkWeb kernel will not execute. |

**Example**

For details about the sample code, see [onCreateNativeMediaPlayer](./arkts-apis-webview-WebviewController.md#oncreatenativemediaplayer12).

## handleTimeUpdate<sup>12+</sup>

handleTimeUpdate(currentPlayTime: number): void

Called to notify the ArkWeb engine of the playback progress when the playback progress changes.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name| Type| Mandatory| Description|
|--------|------|------|------|
| currentPlayTime | number | Yes | Current playback time.<br>Unit: second. Value range: [0, duration]. If the value is out of range, the ArkWeb kernel will not execute it. |

**Example**

For details about the sample code, see [onCreateNativeMediaPlayer](./arkts-apis-webview-WebviewController.md#oncreatenativemediaplayer12).

## handleBufferedEndTimeChanged<sup>12+</sup>

handleBufferedEndTimeChanged(bufferedEndTime: number): void

Called to notify the ArkWeb engine of the buffer time when the buffer time changes.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name| Type| Mandatory| Description|
|--------|------|------|------|
| bufferedEndTime | number | Yes | Duration of the buffered media.<br>Unit: second. Value range: [0, duration]. If the value is out of range, the ArkWeb kernel will not execute. |

**Example**

For details about the sample code, see [onCreateNativeMediaPlayer](./arkts-apis-webview-WebviewController.md#oncreatenativemediaplayer12).

## handleEnded<sup>12+</sup>

handleEnded(): void

When media playback ends, this method is called to notify the ArkWeb kernel of the playback end event.

**System capability**: SystemCapability.Web.Webview.Core

**Example**

For details about the sample code, see [onCreateNativeMediaPlayer](./arkts-apis-webview-WebviewController.md#oncreatenativemediaplayer12).

## handleNetworkStateChanged<sup>12+</sup>

handleNetworkStateChanged(state: NetworkState): void

Called to notify the ArkWeb engine of the network status of the player when the network status changes.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name| Type| Mandatory| Description|
|--------|------|------|------|
| state | [NetworkState](./arkts-apis-webview-e.md#networkstate12) | Yes| Network status of the player.|

**Example**

For details about the sample code, see [onCreateNativeMediaPlayer](./arkts-apis-webview-WebviewController.md#oncreatenativemediaplayer12).

## handleReadyStateChanged<sup>12+</sup>

handleReadyStateChanged(state: ReadyState): void

Called to notify the ArkWeb engine of the cache status of the player when the cache status changes.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name| Type| Mandatory| Description|
|--------|------|------|------|
| state | [ReadyState](./arkts-apis-webview-e.md#readystate12) | Yes| Cache status of the player.|

**Example**

For details about the sample code, see [onCreateNativeMediaPlayer](./arkts-apis-webview-WebviewController.md#oncreatenativemediaplayer12).

## handleFullscreenChanged<sup>12+</sup>

handleFullscreenChanged(fullscreen: boolean): void

Called to notify the ArkWeb engine of the full screen status of the player when the full screen status changes.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name| Type| Mandatory| Description|
|--------|------|------|------|
| fullscreen | boolean | Yes| Whether the player is in full screen.<br>The value **true** means that the player is in full screen, and **false** means the opposite.|

**Example**

For details about the sample code, see [onCreateNativeMediaPlayer](./arkts-apis-webview-WebviewController.md#oncreatenativemediaplayer12).

## handleSeeking<sup>12+</sup>

handleSeeking(): void

When the player enters the seek state, this method is called to notify the ArkWeb kernel of the seek entry event. After the seek is complete, handleSeekFinished should be called to notify the ArkWeb kernel of the seek completion event.

**System capability**: SystemCapability.Web.Webview.Core

**Example**

For details about the sample code, see [onCreateNativeMediaPlayer](./arkts-apis-webview-WebviewController.md#oncreatenativemediaplayer12).

## handleSeekFinished<sup>12+</sup>

handleSeekFinished(): void

When the player completes seeking, this method is called to notify the ArkWeb kernel of the seek completion event.

**System capability**: SystemCapability.Web.Webview.Core

**Example**

For details about the sample code, see [onCreateNativeMediaPlayer](./arkts-apis-webview-WebviewController.md#oncreatenativemediaplayer12).

## handleError<sup>12+</sup>

handleError(error: MediaError, errorMessage: string): void

When an error occurs in the player, this method is called to notify the ArkWeb kernel of the error.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name| Type| Mandatory| Description|
|--------|------|------|------|
| error | [MediaError](./arkts-apis-webview-e.md#mediaerror12) | Yes| Error object type.|
| errorMessage | string | Yes| Error message.|

**Example**

For details about the sample code, see [onCreateNativeMediaPlayer](./arkts-apis-webview-WebviewController.md#oncreatenativemediaplayer12).

## handleVideoSizeChanged<sup>12+</sup>

handleVideoSizeChanged(width: number, height: number): void

When the player parses the video dimensions, this method is called to notify the ArkWeb kernel of the video size.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name| Type| Mandatory| Description|
|--------|------|------|------|
| width | number | Yes | Width of the video, in pixels. Value range: [0, +∞). If a negative number is passed in, the ArkWeb kernel ignores this value. |
| height | number | Yes | Height of the video, in pixels. Value range: [0, +∞). If a negative number is passed in, the ArkWeb kernel ignores this value. |

**Example**

For details about the sample code, see [onCreateNativeMediaPlayer](./arkts-apis-webview-WebviewController.md#oncreatenativemediaplayer12).