# AutoExposureQuery

针对设备的自动曝光特性提供了一系列查询功能。 > > - 本模块接口在API version 12发生兼容变更，保留了内层元素的起始版本信息，会出现外层元素@since版本号大于内层元素的情况，不影响接口使用。

**起始版本：** 23

<!--Device-camera-interface AutoExposureQuery--><!--Device-camera-interface AutoExposureQuery-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
import { cameraPicker } from '@kit.CameraKit';
```

## getExposureBiasRange

```TypeScript
getExposureBiasRange(): Array<double>
```

查询曝光补偿范围。

**起始版本：** 23

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-AutoExposureQuery-getExposureBiasRange(): Array<double>--><!--Device-AutoExposureQuery-getExposureBiasRange(): Array<double>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;double&gt; | 获取补偿范围的数组。接口调用失败会返回相应错误码，错误码类型[CameraErrorCode]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config, only throw in session usage. |

## isExposureModeSupported

```TypeScript
isExposureModeSupported(aeMode: ExposureMode): boolean
```

检测曝光模式是否支持。

**起始版本：** 23

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-AutoExposureQuery-isExposureModeSupported(aeMode: ExposureMode): boolean--><!--Device-AutoExposureQuery-isExposureModeSupported(aeMode: ExposureMode): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| aeMode | [ExposureMode](arkts-camera-camera-exposuremode-e.md) | 是 | 曝光模式。传参为null或者undefined，作为0处理，曝光锁定。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 获取是否支持曝光模式，true为支持，false为不支持。接口调用失败会抛出相应错误码并返回undefined，错误码类型 [CameraErrorCode]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config, only throw in session usage. |

