# Interface (NativeMediaPlayerBridge)

<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @zhangyao75477-->
<!--Designer: @gzweioh-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=4166a00ed5bd25ff483cf28690d41e5067b0c812 translatedAt=2026-08-07T04:23:04.549Z pushedAt=2026-08-07T08:11:06.015Z -->

NativeMediaPlayerBridge is the return value type of the [CreateNativeMediaPlayerCallback](./arkts-apis-webview-t.md#createnativemediaplayercallback12) callback function. It is an interface class between the player that takes over web page media and the ArkWeb kernel. The ArkWeb kernel uses an object of this interface class to control the player created by the app to take over web page media. This interface allows the app to use a custom media player to take over media content playback in web pages. It also supports player suspension and resumption mechanisms.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 9. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The initial APIs of this interface are supported since API version 12.
>
> - The sample effect is subject to the actual device.

## updateRect<sup>12+</sup>

updateRect(x: number, y: number, width: number, height: number): void

Notifies the app of the surface position information. This method is called back by the ArkWeb kernel when the web page layout changes, the page scrolls, or the playback area changes. The app must update the position and size of the native player's rendering surface accordingly.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name| Type| Mandatory| Description|
|--------|------|------|------|
| x | number | Yes | x coordinate of the surface relative to the Web component.<br>Unit: px. |
| y | number | Yes | y coordinate of the surface relative to the Web component.<br>Unit: px. |
| width | number | Yes | Width of the surface.<br>Unit: px. |
| height | number | Yes | Height of the surface.<br>Unit: px. |

**Example**

For details about the sample code, see [onCreateNativeMediaPlayer](./arkts-apis-webview-WebviewController.md#oncreatenativemediaplayer12).

## play<sup>12+</sup>

play(): void

Plays the media.

**System capability**: SystemCapability.Web.Webview.Core

**Example**

For details about the sample code, see [onCreateNativeMediaPlayer](./arkts-apis-webview-WebviewController.md#oncreatenativemediaplayer12).

## pause<sup>12+</sup>

pause(): void

Pauses playback.

**System capability**: SystemCapability.Web.Webview.Core

**Example**

For details about the sample code, see [onCreateNativeMediaPlayer](./arkts-apis-webview-WebviewController.md#oncreatenativemediaplayer12).

## seek<sup>12+</sup>

seek(targetTime: number): void

Seeks to a specific time point in the media.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name| Type| Mandatory| Description|
|--------|------|------|------|
| targetTime | number | Yes | Target time for seek, calculated from the start of media playback.<br>Unit: seconds. |

**Example**

For details about the sample code, see [onCreateNativeMediaPlayer](./arkts-apis-webview-WebviewController.md#oncreatenativemediaplayer12).

## setVolume<sup>12+</sup>

setVolume(volume: number): void

Sets the playback volume.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name| Type| Mandatory| Description|
|--------|------|------|------|
| volume | number | Yes | Volume of the player.<br>Value range: [0, 1.0], where 0 indicates mute and 1.0 indicates the maximum volume. If the value is out of range, it is automatically corrected to the boundary value. |

**Example**

For details about the sample code, see [onCreateNativeMediaPlayer](./arkts-apis-webview-WebviewController.md#oncreatenativemediaplayer12).

## setMuted<sup>12+</sup>

setMuted(muted: boolean): void

Sets the muted status.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name| Type| Mandatory| Description|
|--------|------|------|------|
| muted | boolean | Yes| Whether to mute the player.<br>The value **true** means to mute the player, and **false** means the opposite.|

**Example**

For details about the sample code, see [onCreateNativeMediaPlayer](./arkts-apis-webview-WebviewController.md#oncreatenativemediaplayer12).

## setPlaybackRate<sup>12+</sup>

setPlaybackRate(playbackRate: number): void

Sets the playback rate.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name| Type| Mandatory| Description|
|--------|------|------|------|
| playbackRate | number | Yes | Playback rate.<br>Value range: [0, 10.0], where 1 indicates the original speed. If the value is out of range, it is automatically corrected to the boundary value. |

**Example**

For details about the sample code, see [onCreateNativeMediaPlayer](./arkts-apis-webview-WebviewController.md#oncreatenativemediaplayer12).

## release<sup>12+</sup>

release(): void

Releases this player.

**System capability**: SystemCapability.Web.Webview.Core

**Example**

For details about the sample code, see [onCreateNativeMediaPlayer](./arkts-apis-webview-WebviewController.md#oncreatenativemediaplayer12).

## enterFullscreen<sup>12+</sup>

enterFullscreen(): void

Enables the player to enter full screen mode.

**System capability**: SystemCapability.Web.Webview.Core

**Example**

For details about the sample code, see [onCreateNativeMediaPlayer](./arkts-apis-webview-WebviewController.md#oncreatenativemediaplayer12).

## exitFullscreen<sup>12+</sup>

exitFullscreen(): void

Enables the player to exit full screen mode.

**System capability**: SystemCapability.Web.Webview.Core

**Example**

For details about the sample code, see [onCreateNativeMediaPlayer](./arkts-apis-webview-WebviewController.md#oncreatenativemediaplayer12).

## resumePlayer<sup>12+</sup>

resumePlayer?(): void

Notifies the app to rebuild the player and restore its status information. This method is used only in pair with suspendPlayer.

**System capability**: SystemCapability.Web.Webview.Core

**Example**

For details about the sample code, see [onCreateNativeMediaPlayer](./arkts-apis-webview-WebviewController.md#oncreatenativemediaplayer12).

## suspendPlayer<sup>12+</sup>

suspendPlayer?(type: SuspendType): void

Notifies the app to destroy the player and save its status information. This method is used only in pair with resumePlayer.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name| Type| Mandatory| Description|
|--------|------|------|------|
| type | [SuspendType](./arkts-apis-webview-e.md#suspendtype12) | Yes | Player suspension type, which specifies how the player is suspended. Different SuspendType values correspond to different suspension scenarios. |

**Example**

For details about the sample code, see [onCreateNativeMediaPlayer](./arkts-apis-webview-WebviewController.md#oncreatenativemediaplayer12).