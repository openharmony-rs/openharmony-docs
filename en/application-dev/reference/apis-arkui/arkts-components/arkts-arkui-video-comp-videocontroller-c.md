# VideoController

```TypeScript
declare class VideoController
```

A **VideoController** object can control one or more **Video** components.

## Objects to Import

```ts
let controller: VideoController = new VideoController();
```

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor()
```

A constructor used to create a **VideoController** object.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## exitFullscreen

```TypeScript
exitFullscreen()
```

Exits full-screen mode.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## pause

```TypeScript
pause()
```

Pauses playback. The current frame is then displayed, and playback will be resumed from this paused position.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## requestFullscreen

```TypeScript
requestFullscreen(value: boolean)
```

Requests full-screen playback.

> **NOTE:** 
> 
> The built-in full-screen feature of the **Video** component only sets the video content to full screen and
> displays the default controller. It does not support displaying a custom title or controller. If additional
> functionality is required, implement custom full-screen features.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to play in full-screen mode (fill the app window).<br>The value **true** requests full-screen playback, and **false** does not request full-screen playback. <br>Default value: **false** |

## reset

```TypeScript
reset(): void
```

Resets the video player. The current frame is displayed, and playback starts from the beginning when it is played again.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## setCurrentTime

```TypeScript
setCurrentTime(value: number)
```

Sets the video playback position.

> **NOTE:** 
> 
> To start playback from a specific time point in the video, disable autoplay, and seek to the target position
> before playing after the video is prepared.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Video playback progress position. <br>Value range: [0, [duration](arkts-arkui-video-comp-preparedinfo-i.md)] <br>If the **value** is greater than **duration**, the progress jumps to the end; if the **value** is less than 0, no progress jump is performed. <br>Unit: s <br>Since API version 8, the video seek mode can be set. For details, see [setCurrentTime&lt;sup&gt;8+&lt;/sup&gt;](#setcurrenttime-1). |

<a id="setcurrenttime-1"></a>

## setCurrentTime

```TypeScript
setCurrentTime(value: number, seekMode: SeekMode)
```

Sets the video playback position with the specified seek mode.

> **NOTE:** 
> 
> To start playback from a specific time point in the video, disable autoplay, and seek to the target position
> before playing after the video is prepared.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Video playback position. <br>Value range: [0, [duration](arkts-arkui-video-comp-preparedinfo-i.md)] <br>If **value** is greater than **duration**, the progress jumps to the end. If **value** is less than 0, no progress jump is performed. <br>Unit: s |
| seekMode | [SeekMode](arkts-arkui-video-comp-seekmode-e.md) | Yes | Seek mode.<br>Abnormal values **undefined**, **null**, **NaN**, and **Infinity** are processed as **PreviousKeyframe**. |

## start

```TypeScript
start()
```

Starts playback.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## stop

```TypeScript
stop()
```

Stops playback. The current frame is then displayed, and playback will restart from the very beginning.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
