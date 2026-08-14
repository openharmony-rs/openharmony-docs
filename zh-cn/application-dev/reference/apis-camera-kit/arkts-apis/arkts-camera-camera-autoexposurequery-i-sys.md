# AutoExposureQuery

针对设备的自动曝光特性提供了一系列查询功能。 > > - 本模块接口在API version 12发生兼容变更，保留了内层元素的起始版本信息，会出现外层元素@since版本号大于内层元素的情况，不影响接口使用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-camera-interface AutoExposureQuery--><!--Device-camera-interface AutoExposureQuery-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## isExposureMeteringModeSupported

```TypeScript
isExposureMeteringModeSupported(aeMeteringMode: ExposureMeteringMode): boolean
```

检测是否支持指定的曝光测光模式。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-AutoExposureQuery-isExposureMeteringModeSupported(aeMeteringMode: ExposureMeteringMode): boolean--><!--Device-AutoExposureQuery-isExposureMeteringModeSupported(aeMeteringMode: ExposureMeteringMode): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| aeMeteringMode | [ExposureMeteringMode](arkts-camera-camera-exposuremeteringmode-e-sys.md) | 是 | 曝光测光模式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 是否支持曝光测光模式。true表示支持，false表示不支持 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect.<br>**适用版本：** 12 - 23 |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config, only throw in session usage. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application.<br>**适用版本：** 12 - 23 |

