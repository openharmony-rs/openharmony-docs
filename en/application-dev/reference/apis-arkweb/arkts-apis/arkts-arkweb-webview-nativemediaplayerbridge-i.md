# NativeMediaPlayerBridge

NativeMediaPlayerBridge is the return value type of the [CreateNativeMediaPlayerCallback](arkts-arkweb-webview-createnativemediaplayercallback-t.md) callback function. It is an interface class between the player that takes over web page media and the ArkWeb kernel. The ArkWeb kernel uses an object of this interface class to control the player created by the app to take over web page media. This interface allows the app to use a custom media player to take over media content playback in web pages. It also supports player suspension and resumption mechanisms.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## Modules to Import

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## enterFullscreen

```TypeScript
enterFullscreen(): void
```

Enables the player to enter full screen mode.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## exitFullscreen

```TypeScript
exitFullscreen(): void
```

Enables the player to exit full screen mode.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## pause

```TypeScript
pause(): void
```

Pauses playback.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## play

```TypeScript
play(): void
```

Plays the media.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## release

```TypeScript
release(): void
```

Releases this player.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## resumePlayer

```TypeScript
resumePlayer?(): void
```

Notifies the app to rebuild the player and restore its status information. This method is used only in pair with suspendPlayer.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## seek

```TypeScript
seek(targetTime: number): void
```

Seeks to a specific time point in the media.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| targetTime | number | Yes | Target time for seek, calculated from the start of media playback.<br>Unit: seconds. |

## setMuted

```TypeScript
setMuted(muted: boolean): void
```

Sets the muted status.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| muted | boolean | Yes | Whether to mute the player.<br>The value **true** means to mute the player, and **false** means the opposite. |

## setPlaybackRate

```TypeScript
setPlaybackRate(playbackRate: number): void
```

Sets the playback rate.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| playbackRate | number | Yes | Playback rate.<br>Value range: [0, 10.0], where 1 indicates the original speed. If the value is out of range, it is automatically corrected to the boundary value. |

## setVolume

```TypeScript
setVolume(volume: number): void
```

Sets the playback volume.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| volume | number | Yes | Volume of the player.<br>Value range: [0, 1.0], where 0 indicates mute and 1.0 indicates the maximum volume. If the value is out of range, it is automatically corrected to the boundary value. |

## suspendPlayer

```TypeScript
suspendPlayer?(type: SuspendType): void
```

Notifies the app to destroy the player and save its status information. This method is used only in pair with resumePlayer.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [SuspendType](arkts-arkweb-webview-suspendtype-e.md) | Yes | Player suspension type, which specifies how the player is suspended. Different SuspendType values correspond to different suspension scenarios. |

## updateRect

```TypeScript
updateRect(x: number, y: number, width: number, height: number): void
```

Notifies the app of the surface position information. This method is called back by the ArkWeb kernel when the web page layout changes, the page scrolls, or the playback area changes. The app must update the position and size of the native player's rendering surface accordingly.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | x coordinate of the surface relative to the Web component.<br>Unit: px. |
| y | number | Yes | y coordinate of the surface relative to the Web component.<br>Unit: px. |
| width | number | Yes | Width of the surface.<br>Unit: px. |
| height | number | Yes | Height of the surface.<br>Unit: px. |
