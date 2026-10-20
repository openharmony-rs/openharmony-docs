# ImagingModeQuery（系统接口）

```TypeScript
interface ImagingModeQuery
```

成像模式查询对象。

**起始版本：** 26.0.1

<!--Device-camera-interface ImagingModeQuery--><!--Device-camera-interface ImagingModeQuery-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
```

## isImagingModeSupported

```TypeScript
isImagingModeSupported(mode: CameraImagingMode): boolean
```

检测是否支持指定的相机成像模式。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImagingModeQuery-isImagingModeSupported(mode: CameraImagingMode): boolean--><!--Device-ImagingModeQuery-isImagingModeSupported(mode: CameraImagingMode): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [CameraImagingMode](arkts-camera-camera-cameraimagingmode-e-sys.md) | 是 | 成像模式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 是否支持该成像模式。**true**表示支持，**false**表示不支持。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config, only throw in session usage. |
