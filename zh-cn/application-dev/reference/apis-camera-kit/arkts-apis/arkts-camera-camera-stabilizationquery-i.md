# StabilizationQuery

提供了查询设备在录像模式下是否支持对应的视频防抖模式的能力。 > **说明：** > > - 本Interface的起始版本为API version 12。接口在API version 12发生兼容变更，保留了内层元素的起始版本信息，会出现外层元素@since版本号大于内层元素的情况，不影响接口使用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-camera-interface StabilizationQuery--><!--Device-camera-interface StabilizationQuery-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## isVideoStabilizationModeSupported

```TypeScript
isVideoStabilizationModeSupported(vsMode: VideoStabilizationMode): boolean
```

查询是否支持指定的视频防抖模式。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-StabilizationQuery-isVideoStabilizationModeSupported(vsMode: VideoStabilizationMode): boolean--><!--Device-StabilizationQuery-isVideoStabilizationModeSupported(vsMode: VideoStabilizationMode): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| vsMode | [VideoStabilizationMode](arkts-camera-camera-videostabilizationmode-e.md) | 是 | 视频防抖模式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回视频防抖模式是否支持。true表示支持，false表示不支持。接口调用失败会抛出相应错误码并返回undefined，错误码类型 [CameraErrorCode]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config, only throw in session usage. |

