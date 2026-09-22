# VideoControllerAsync

```TypeScript
declare class VideoControllerAsync
```

**VideoControllerAsync** is the asynchronous version of **VideoController**. It can obtain the results of some playback control commands through a promise. It does not support controlling multiple **Video** components at the same time.

> **NOTE:** 
> 
> **VideoControllerAsync** provides the execution results of commands. Compared with **VideoController**, playback
> control commands such as [start](arkts-arkui-video-comp-videocontroller-c.md#start), [pause](arkts-arkui-video-comp-videocontroller-c.md#pause),
> [stop](arkts-arkui-video-comp-videocontroller-c.md#stop), and [reset](#reset) are executed asynchronously. They
> return immediately after the request without blocking the current thread, and the execution results can be
> processed through the **then** and **catch** methods of the promise.

## Objects to Import

```ts
let controllerAsync: VideoControllerAsync = new VideoControllerAsync();
```

**Since:** 26.0.0

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor()
```

Constructor of **VideoControllerAsync**.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## exitFullscreen

```TypeScript
exitFullscreen()
```

Exits full-screen playback.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## pause

```TypeScript
pause(): Promise<void>
```

Pauses video playback. The current frame is displayed, and playback resumes from the current position when it is played again. This API uses a promise to return the result.

This method can be called only in the playing state. Calling **pause()** in other states will fail.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

## requestFullscreen

```TypeScript
requestFullscreen(value: boolean)
```

Requests full-screen playback. If this API is not called, full-screen playback is not requested by default.

> **NOTE:** 
> 
> The full-screen function built into the **Video** component only sets the video content to full screen and
> displays the default controller. It cannot display a custom title or controller. To implement other functions,
> you need to implement the full-screen function by yourself.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to play in full screen (fill the app window).<br>**true**: request full-screen playback; **false**: do not request full-screen playback. |

## reset

```TypeScript
reset(): Promise<void>
```

Resets the video player. The current frame is displayed, and playback starts from the beginning when it is played again. This API uses a promise to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

## setCurrentTime

```TypeScript
setCurrentTime(value: number, seekMode?: SeekMode)
```

Sets the playback position of the video, with an optional seek mode.

> **NOTE:** 
> 
> To start playback from a specific time point in the video, disable autoplay, and seek to the target position
> before playing after the video is prepared.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Video playback progress position. <br>Value range: [0, [duration](arkts-arkui-video-comp-preparedinfo-i.md)] <br>If the **value** is greater than **duration**, the progress jumps to the end. If the **value** is less than 0, the progress does not jump. <br>Unit: s |
| seekMode | [SeekMode](arkts-arkui-video-comp-seekmode-e.md) | No | Seek mode.<br>Abnormal values **undefined**, **null**, **NaN**, and **Infinity** are processed as **PreviousKeyframe**. <br>Default value: **PreviousKeyframe** |

## start

```TypeScript
start(): Promise<void>
```

Starts video playback. This API uses a promise to return the result.

Calling **start()** before the video is prepared (before the [onPrepared](arkts-arkui-video-comp-attribute.md#onprepared) callback is received) will fail.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

## stop

```TypeScript
stop(): Promise<void>
```

Stops video playback. The current frame is displayed, and playback starts from the beginning when it is played again. This API uses a promise to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |
