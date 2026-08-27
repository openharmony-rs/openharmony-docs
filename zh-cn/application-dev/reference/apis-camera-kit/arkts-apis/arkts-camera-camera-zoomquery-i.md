# ZoomQuery

提供了与设备的缩放相关的查询功能，包括获取支持的缩放比例范围。

> **说明：**
> 
> - 本Interface的起始版本为API version 12。接口在API version 12发生兼容变更，保留了内层元素的起始版本信息，会出现外层元素

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Camera.Core

## 导入模块

```TypeScript
```

## getRAWCaptureZoomRatioRange

```TypeScript
getRAWCaptureZoomRatioRange(): Array<number>
```

获取RAW拍摄期间支持的变焦比例范围。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array & lt;number & gt; | 变焦比例范围。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed, the inputDevice or the session is abnormal. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function getRAWCaptureZoomRatioRange(photoSession: camera.PhotoSession): Array<number> {
  let zoomRatioRange: Array<number> = [];
  try {
    zoomRatioRange = photoSession.getRAWCaptureZoomRatioRange();
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The getRAWCaptureZoomRatioRange call failed. error code: ${err.code}`);
  }
  return zoomRatioRange;
}
```

## getZoomPointInfos

```TypeScript
getZoomPointInfos(): Array<ZoomPointInfo>
```

获取当前模式的等效焦距信息列表。

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[ZoomPointInfo](arkts-camera-camera-zoompointinfo-i.md)&gt; | 获取当前模式的等效焦距信息列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application.<br>**适用版本：** 12 - 24 |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config, only throw in session usage. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function getZoomPointInfos(photoSession: camera.PhotoSession): Array<camera.ZoomPointInfo> {
  let zoomPointInfos: Array<camera.ZoomPointInfo> = [];
  try {
    zoomPointInfos = photoSession.getZoomPointInfos();
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The getZoomPointInfos call failed. error code: ${err.code}`);
  }
  return zoomPointInfos;
}
```

## getZoomRatioRange

```TypeScript
getZoomRatioRange(): Array<number>
```

获取支持的变焦范围。

**起始版本：** 11

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array & lt;number & gt; | 用于获取可变焦距比范围，返回的数组包括其最小值和最大值。接口调用失败会抛出相应错误码并返回undefined，错误码类型 [CameraErrorCode]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config, only throw in session usage. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function getZoomRatioRange(captureSession: camera.CaptureSession): Array<number> {
  let zoomRatioRange: Array<number> = [];
  try {
    zoomRatioRange = captureSession.getZoomRatioRange();
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The getZoomRatioRange call failed. error code: ${err.code}`);
  }
  return zoomRatioRange;
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function getZoomRatioRange(photoSession: camera.PhotoSession): Array<number> {
  let zoomRatioRange: Array<number> = [];
  try {
    zoomRatioRange = photoSession.getZoomRatioRange();
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The getZoomRatioRange call failed. error code: ${err.code}`);
  }
  return zoomRatioRange;
}
```
