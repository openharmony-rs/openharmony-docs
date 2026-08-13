# Stabilization

Stabilization继承自[StabilizationQuery](arkts-camera-camera-stabilizationquery-i.md#StabilizationQuery)。 提供设备在录像模式下设置视频防抖的操作。 需要会话中有录像流（[VideoOutput](arkts-camera-camera-videooutput-i.md#VideoOutput)）的前提下，才可以对视频进行防抖设置。

**继承/实现关系：** Stabilization extends [StabilizationQuery](arkts-camera-camera-stabilizationquery-i.md#StabilizationQuery)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-camera-interface Stabilization--><!--Device-camera-interface Stabilization-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## getActiveVideoStabilizationMode

```TypeScript
getActiveVideoStabilizationMode(): VideoStabilizationMode
```

查询当前正在使用的视频防抖模式。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-Stabilization-getActiveVideoStabilizationMode(): VideoStabilizationMode--><!--Device-Stabilization-getActiveVideoStabilizationMode(): VideoStabilizationMode-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [VideoStabilizationMode](arkts-camera-camera-videostabilizationmode-e.md) | 视频防抖是否正在使用。若接口调用失败，返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## setVideoStabilizationMode

```TypeScript
setVideoStabilizationMode(mode: VideoStabilizationMode): void
```

设置视频防抖模式。需要先检查设备是否支持对应的防抖模式，可以通过 [isVideoStabilizationModeSupported](arkts-camera-camera-stabilizationquery-i.md#isVideoStabilizationModeSupported)方法判断所设置的模式是 否支持。建议在[commitConfig](arkts-camera-camera-session-i.md#commitConfig)与[Start](arkts-camera-camera-session-i.md#start)之间设置视频防抖。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-Stabilization-setVideoStabilizationMode(mode: VideoStabilizationMode): void--><!--Device-Stabilization-setVideoStabilizationMode(mode: VideoStabilizationMode): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [VideoStabilizationMode](arkts-camera-camera-videostabilizationmode-e.md) | 是 | 需要设置的视频防抖模式。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

