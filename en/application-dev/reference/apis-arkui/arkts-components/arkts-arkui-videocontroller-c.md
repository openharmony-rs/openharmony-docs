# VideoController

A **VideoController** object can control one or more **Video** components.

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor()
```

A constructor used to create a **VideoController** object.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## exitFullscreen

```TypeScript
exitFullscreen()
```

Exits full-screen mode.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## pause

```TypeScript
pause()
```

Pauses playback. The current frame is then displayed, and playback will be resumed from this paused position.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## requestFullscreen

```TypeScript
requestFullscreen(value: boolean)
```

Requests full-screen playback.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to request full-screen playback (filling the application window).<br>**true**: Request full-screen playback.<br>**false**: Do not request full-screen playback.<br>Default value: **false**. |

## reset

```TypeScript
reset(): void
```

Resets the **AVPlayer** instance of this component, which displays the current frame and sets the playback to start from the beginning for subsequent playbacks.

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
> To start playback from a specific position, disable autoplay, wait for video preparation to complete, and then
> seek to the target position.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Video playback position.<br>Value range: [0, [duration](arkts-arkui-preparedinfo-i.md)]<br> When the set value is greater than the duration, the progress will jump to the end; when the set value is less than 0, no progress jump will occur.<br>Unit: second<br>Since API version 8, seek mode configuration is supported. For details, see [setCurrentTime&lt;sup&gt;8+&lt;/sup&gt;](#setcurrenttime-1). |

## setCurrentTime

```TypeScript
setCurrentTime(value: number, seekMode: SeekMode)
```

Sets the video playback position with the specified seek mode.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Video playback position.<br>Value range: [0, [duration](arkts-arkui-preparedinfo-i.md)]<br> When the set value is greater than the duration, the progress will jump to the end; when the set value is less than 0, no progress jump will occur.<br>Unit: second |
| seekMode | [SeekMode](arkts-arkui-seekmode-e.md) | Yes | Seek mode. |

## start

```TypeScript
start()
```

Starts playback.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## stop

```TypeScript
stop()
```

Stops playback. The current frame is then displayed, and playback will restart from the very beginning.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
