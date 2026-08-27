# Focus

Focus继承自[FocusQuery](arkts-camera-camera-focusquery-i.md)。对焦类，对设备对焦操作。

**继承/实现关系：** Focus extends [FocusQuery](arkts-camera-camera-focusquery-i.md)

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Camera.Core

## 导入模块

```TypeScript
```

## getFocalLength

```TypeScript
getFocalLength(): number
```

查询当前的焦距值。

**起始版本：** 11

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 用于获取当前焦距，单位mm。接口调用失败会返回相应错误码，错误码类型[CameraErrorCode]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function getFocalLength(captureSession: camera.CaptureSession): number {
  const invalidValue: number = -1;
  let focalLength: number = invalidValue;
  try {
    focalLength = captureSession.getFocalLength();
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The getFocalLength call failed. error code: ${err.code}`);
  }
  return focalLength;
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function getFocalLength(photoSession: camera.PhotoSession): number {
  const invalidValue: number = -1;
  let focalLength: number = invalidValue;
  try {
    focalLength = photoSession.getFocalLength();
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The getFocalLength call failed. error code: ${err.code}`);
  }
  return focalLength;
}
```

## getFocusMode

```TypeScript
getFocusMode(): FocusMode
```

获取当前的对焦模式。

**起始版本：** 11

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| FocusMode | 获取当前设备的焦距模式。接口调用失败会抛出相应错误码并返回undefined，错误码类型 [CameraErrorCode]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function getFocusMode(captureSession: camera.CaptureSession): camera.FocusMode | undefined {
  let afMode: camera.FocusMode | undefined = undefined;
  try {
    afMode = captureSession.getFocusMode();
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The getFocusMode call failed. error code: ${err.code}`);
  }
  return afMode;
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function getFocusMode(photoSession: camera.PhotoSession): camera.FocusMode | undefined {
  let afMode: camera.FocusMode | undefined = undefined;
  try {
    afMode = photoSession.getFocusMode();
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The getFocusMode call failed. error code: ${err.code}`);
  }
  return afMode;
}
```

## getFocusPoint

```TypeScript
getFocusPoint(): Point
```

查询当前的焦点。

**起始版本：** 11

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Point | 用于获取当前的焦点。接口调用失败会返回相应错误码，错误码类型为[CameraErrorCode]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function getFocusPoint(captureSession: camera.CaptureSession): camera.Point | undefined {
  let point: camera.Point | undefined = undefined;
  try {
    point = captureSession.getFocusPoint();
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The getFocusPoint call failed. error code: ${err.code}`);
  }
  return point;
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function getFocusPoint(photoSession: camera.PhotoSession): camera.Point | undefined {
  let point: camera.Point | undefined = undefined;
  try {
    point = photoSession.getFocusPoint();
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The getFocusPoint call failed. error code: ${err.code}`);
  }
  return point;
}
```

## lockFocusTracking

```TypeScript
lockFocusTracking(focusPoint: Point): void
```

锁定焦点跟踪，使对焦持续追踪指定的物体。通过focusPoint参数指定追踪目标。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| focusPoint | Point | 是 | 锁定对焦跟踪点。x、y的取值范围均为 [0, 1]，超出范围则设置不生效。(0, 0)表示画面左上角，(1, 1)表示画面右下角。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config, only throw in session usage. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function lockFocusTracking(photoSession: camera.PhotoSession): void {
  try {
    const focusPoint: camera.Point = {x: 0, y: 0};
    photoSession.lockFocusTracking(focusPoint);
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The lockFocusTrack call failed. error code: ${err.code}`);
  }
}
```

## setFocusMode

```TypeScript
setFocusMode(afMode: FocusMode): void
```

设置对焦模式。进行设置之前，需要先检查设备是否支持指定的焦距模式，可使用方法[isFocusModeSupported](arkts-camera-camera-focusquery-i.md#isfocusmodesupported)。

**起始版本：** 11

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| afMode | FocusMode | 是 | 指定的焦距模式。传参为null或者undefined，作为0处理，手动对焦模式。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function setFocusMode(captureSession: camera.CaptureSession): void {
  try {
    captureSession.setFocusMode(camera.FocusMode.FOCUS_MODE_AUTO);
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The setFocusMode call failed. error code: ${err.code}`);
  }
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function setFocusMode(photoSession: camera.PhotoSession): void {
  try {
    photoSession.setFocusMode(camera.FocusMode.FOCUS_MODE_AUTO);
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The setFocusMode call failed. error code: ${err.code}`);
  }
}
```

## setFocusPoint

```TypeScript
setFocusPoint(point: Point): void
```

设置焦点，焦点应在0-1坐标系内，该坐标系左上角为{0，0}，右下角为{1，1}。此坐标系是以设备充电口在右侧时的横向设备方向为基准的，例如应用的预览界面布局以设备充电口在下侧时的竖向方向为基准，布局宽高为{w，h}，且触碰点为{x，y}，则转换后的坐标点为{y/h，1-x/w}。

**起始版本：** 11

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| point | Point | 是 | 焦点。x、y设置范围应在[0，1]之内，超过范围，如果小于0设置0，大于1设置1。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function setFocusPoint(captureSession: camera.CaptureSession): void {
  const focusPoint: camera.Point = {x: 1, y: 1};
  try {
    captureSession.setFocusPoint(focusPoint);
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The setFocusPoint call failed. error code: ${err.code}`);
  }
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function setFocusPoint(photoSession: camera.PhotoSession): void {
  const focusPoint: camera.Point = {x: 1, y: 1};
  try {
    photoSession.setFocusPoint(focusPoint);
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The setFocusPoint call failed. error code: ${err.code}`);
  }
}
```

## unlockFocusTracking

```TypeScript
unlockFocusTracking(): void
```

解锁焦点跟踪。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config, only throw in session usage. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function unlockFocusTracking(photoSession: camera.PhotoSession): void {
  try {
    photoSession.unlockFocusTracking();
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The unlockFocusTrack call failed. error code: ${err.code}`);
  }
}
```
