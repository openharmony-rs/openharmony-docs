# VideoControllerAsync

Video playback controller class for asynchronous operations.Provides methods to control video playback, timing, and display mode.

**起始版本：** 26.0.0

<!--Device-unnamed-declare class VideoControllerAsync--><!--Device-unnamed-declare class VideoControllerAsync-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="constructor"></a>
## constructor

```TypeScript
constructor()
```

Creates a VideoControllerAsync instance.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-VideoControllerAsync-constructor()--><!--Device-VideoControllerAsync-constructor()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="exitfullscreen"></a>
## exitFullscreen

```TypeScript
exitFullscreen()
```

Exits fullscreen display mode.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-VideoControllerAsync-exitFullscreen()--><!--Device-VideoControllerAsync-exitFullscreen()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="pause"></a>
## pause

```TypeScript
pause(): Promise<void>
```

Pauses video playback asynchronously.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-VideoControllerAsync-pause(): Promise<void>--><!--Device-VideoControllerAsync-pause(): Promise<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

<a id="requestfullscreen"></a>
## requestFullscreen

```TypeScript
requestFullscreen(value: boolean)
```

Requests fullscreen display for the video.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-VideoControllerAsync-requestFullscreen(value: boolean)--><!--Device-VideoControllerAsync-requestFullscreen(value: boolean)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | true to enter fullscreen, false otherwise. |

<a id="reset"></a>
## reset

```TypeScript
reset(): Promise<void>
```

Resets the video controller asynchronously.Restores the controller to its initial state.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-VideoControllerAsync-reset(): Promise<void>--><!--Device-VideoControllerAsync-reset(): Promise<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

<a id="setcurrenttime"></a>
## setCurrentTime

```TypeScript
setCurrentTime(value: number)
```

Sets the current playback time without specifying seek mode.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-VideoControllerAsync-setCurrentTime(value: double)--><!--Device-VideoControllerAsync-setCurrentTime(value: double)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | The target time in seconds<br>Unit: Seconds, The value must be greater than or equal to 0, The maximum value is the total duration of the video. If the duration exceeds the maximum value, the system jumps to the end of the video. |

<a id="setcurrenttime-1"></a>
## setCurrentTime

```TypeScript
setCurrentTime(value: number, seekMode: SeekMode)
```

Sets the current playback time with specified seek mode.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-VideoControllerAsync-setCurrentTime(value: double, seekMode: SeekMode)--><!--Device-VideoControllerAsync-setCurrentTime(value: double, seekMode: SeekMode)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | The target time in seconds<br>Unit: Seconds, The value must be greater than or equal to 0, The maximum value is the total duration of the video. If the duration exceeds the maximum value, the system jumps to the end of the video. |
| seekMode | [SeekMode](../../apis-media-kit/arkts-apis/arkts-media-multimedia-media-seekmode-e.md) | 是 | The seek mode to use for time adjustment. |

<a id="start"></a>
## start

```TypeScript
start(): Promise<void>
```

Starts video playback asynchronously.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-VideoControllerAsync-start(): Promise<void>--><!--Device-VideoControllerAsync-start(): Promise<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

<a id="stop"></a>
## stop

```TypeScript
stop(): Promise<void>
```

Stops video playback asynchronously.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-VideoControllerAsync-stop(): Promise<void>--><!--Device-VideoControllerAsync-stop(): Promise<void>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

