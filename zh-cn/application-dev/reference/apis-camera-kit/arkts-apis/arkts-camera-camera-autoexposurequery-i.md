# AutoExposureQuery

针对设备的自动曝光特性提供了一系列查询功能。   
> 
> - 本模块接口在API version 12发生兼容变更，保留了内层元素的起始版本信息，会出现外层元素

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Camera.Core

## 导入模块

```TypeScript
```

## getExposureBiasRange

```TypeScript
getExposureBiasRange(): Array<number>
```

查询曝光补偿范围。

**起始版本：** 11

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array & lt;number & gt; | 获取补偿范围的数组。接口调用失败会返回相应错误码，错误码类型[CameraErrorCode]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config, only throw in session usage. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function getExposureBiasRange(photoSession: camera.PhotoSession): Array<number> {
  let biasRangeArray: Array<number> = [];
  try {
    biasRangeArray = photoSession.getExposureBiasRange();
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The getExposureBiasRange call failed. error code: ${err.code}`);
  }
  return biasRangeArray;
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function getExposureBiasRange(captureSession: camera.CaptureSession): Array<number> {
  let biasRangeArray: Array<number> = [];
  try {
    biasRangeArray = captureSession.getExposureBiasRange();
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The getExposureBiasRange call failed. error code: ${err.code}`);
  }
  return biasRangeArray;
}
```

## isExposureMeteringModeSupported

```TypeScript
isExposureMeteringModeSupported(aeMeteringMode: ExposureMeteringMode): boolean
```

检测是否支持指定的曝光测光模式。

**起始版本：** 24

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| aeMeteringMode | [ExposureMeteringMode](arkts-camera-camera-exposuremeteringmode-e.md) | 是 | 曝光测光模式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 是否支持曝光测光模式。true表示支持，false表示不支持 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application.<br>**适用版本：** 12 - 23 |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect.<br>**适用版本：** 12 - 23 |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config, only throw in session usage. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function isExposureMeteringModeSupported(photoSession: camera.PhotoSession, aeMeteringMode: camera.ExposureMeteringMode): boolean {
  let isSupported: boolean = false;
  try {
    isSupported = photoSession.isExposureMeteringModeSupported(aeMeteringMode);
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The isExposureMeteringModeSupported call failed. error code: ${err.code}`);
  }
  return isSupported;
}
```

## isExposureModeSupported

```TypeScript
isExposureModeSupported(aeMode: ExposureMode): boolean
```

检测曝光模式是否支持。

**起始版本：** 11

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

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

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function isExposureModeSupported(photoSession: camera.PhotoSession): boolean {
  let isSupported: boolean = false;
  try {
    isSupported = photoSession.isExposureModeSupported(camera.ExposureMode.EXPOSURE_MODE_LOCKED);
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The isExposureModeSupported call failed. error code: ${err.code}`);
  }
  return isSupported;
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function isExposureModeSupported(captureSession: camera.CaptureSession): boolean {
  let isSupported: boolean = false;
  try {
    isSupported = captureSession.isExposureModeSupported(camera.ExposureMode.EXPOSURE_MODE_LOCKED);
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The isExposureModeSupported call failed. error code: ${err.code}`);
  }
  return isSupported;
}
```
