# AutoExposure

AutoExposure继承自[AutoExposureQuery](arkts-camera-camera-autoexposurequery-i.md#AutoExposureQuery)。 自动曝光类，对设备自动曝光（AE）操作。

**继承/实现关系：** AutoExposure extends [AutoExposureQuery](arkts-camera-camera-autoexposurequery-i.md#AutoExposureQuery)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-camera-interface AutoExposure--><!--Device-camera-interface AutoExposure-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## getExposureMeteringMode

```TypeScript
getExposureMeteringMode(): ExposureMeteringMode
```

获取当前曝光测光模式。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-AutoExposure-getExposureMeteringMode(): ExposureMeteringMode--><!--Device-AutoExposure-getExposureMeteringMode(): ExposureMeteringMode-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ExposureMeteringMode](arkts-camera-camera-exposuremeteringmode-e-sys.md) | 当前曝光测光模式。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed, the inputDevice or the session is abnormal.<br>**适用版本：** 24+ |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config, only throw in session usage. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application.<br>**适用版本：** 12 - 23 |

## setExposureMeteringMode

```TypeScript
setExposureMeteringMode(aeMeteringMode: ExposureMeteringMode): void
```

设置曝光测光模式。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-AutoExposure-setExposureMeteringMode(aeMeteringMode: ExposureMeteringMode): void--><!--Device-AutoExposure-setExposureMeteringMode(aeMeteringMode: ExposureMeteringMode): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| aeMeteringMode | [ExposureMeteringMode](arkts-camera-camera-exposuremeteringmode-e-sys.md) | 是 | 曝光测光模式。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect.<br>**适用版本：** 12 - 23 |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed, the inputDevice or the session is abnormal.<br>**适用版本：** 24+ |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config, only throw in session usage. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application.<br>**适用版本：** 12 - 23 |

