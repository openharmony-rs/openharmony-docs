# PreviewOutput（系统接口）

```TypeScript
interface PreviewOutput extends CameraOutput
```

预览输出类。

**继承/实现关系：** PreviewOutput extends [CameraOutput](arkts-camera-camera-cameraoutput-i.md)

**起始版本：** 10

<!--Device-camera-interface PreviewOutput extends CameraOutput--><!--Device-camera-interface PreviewOutput extends CameraOutput-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
```

## attachSketchSurface

```TypeScript
attachSketchSurface(surfaceId: string): void
```

为画中画预览绑定 surface。

**起始版本：** 11

<!--Device-PreviewOutput-attachSketchSurface(surfaceId: string): void--><!--Device-PreviewOutput-attachSketchSurface(surfaceId: string): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| surfaceId | string | 是 | Surface ID，通过XComponent 获取。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect.<br>**适用版本：** 12+ |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error.<br>**适用版本：** 12+ |

<!--Del-->
**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function attachSketchSurface(previewOutput: camera.PreviewOutput, session: camera.Session, cameraInput: camera.CameraInput, sketchSurfaceId: string): void {
  try {
    session.beginConfig();
    session.addInput(cameraInput);
    session.addOutput(previewOutput);
    previewOutput.enableSketch(true);
    session.commitConfig();
    previewOutput.attachSketchSurface(sketchSurfaceId);
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The attachSketchSurface call failed. error code: ${err.code}`);
  }
}
```

<!--DelEnd-->

## enableSketch

```TypeScript
enableSketch(enabled: boolean): void
```

使能或去使能画中画预览。

**起始版本：** 11

<!--Device-PreviewOutput-enableSketch(enabled: boolean): void--><!--Device-PreviewOutput-enableSketch(enabled: boolean): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | 是否使能画中画视图。**true**表示使能，**false**表示去使能。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed.<br>**适用版本：** 12+ |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error.<br>**适用版本：** 12+ |

<!--Del-->
**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function enableSketch(previewOutput: camera.PreviewOutput, session: camera.Session, cameraInput: camera.CameraInput): void {
  try {
    session.beginConfig();
    session.addInput(cameraInput);
    session.addOutput(previewOutput);
    previewOutput.enableSketch(true);
    session.commitConfig();
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The enableSketch call failed. error code: ${err.code}`);
  }
}
```

<!--DelEnd-->

## getSketchRatio

```TypeScript
getSketchRatio(): number
```

获取启用画中画预览时的变焦比。

**起始版本：** 11

<!--Device-PreviewOutput-getSketchRatio(): double--><!--Device-PreviewOutput-getSketchRatio(): double-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 变焦比。若不支持画中画预览，返回**-1**。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

<!--Del-->
**示例**

```TypeScript
function getSketchRatio(previewOutput: camera.PreviewOutput): number {
  let sketchRatio: number = previewOutput.getSketchRatio();
  return sketchRatio;
}
```

<!--DelEnd-->

## isSketchSupported

```TypeScript
isSketchSupported(): boolean
```

检查是否支持画中画（PiP）预览。

**起始版本：** 11

<!--Device-PreviewOutput-isSketchSupported(): boolean--><!--Device-PreviewOutput-isSketchSupported(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示是否支持画中画预览。**true**表示支持，**false**表示不支持。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |

<!--Del-->
**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function isSketchSupported(previewOutput: camera.PreviewOutput): boolean {
  try {
    let isSupported: boolean = previewOutput.isSketchSupported();
    return isSupported;
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The isSketchSupported call failed. error code: ${err.code}`);
  }
  return false;
}
```

<!--DelEnd-->

## off('sketchStatusChanged')

```TypeScript
off(type: 'sketchStatusChanged', callback?: AsyncCallback<SketchStatusData>): void
```

取消订阅画中画状态变化事件。

**起始版本：** 11

<!--Device-PreviewOutput-off(type: 'sketchStatusChanged', callback?: AsyncCallback<SketchStatusData>): void--><!--Device-PreviewOutput-off(type: 'sketchStatusChanged', callback?: AsyncCallback<SketchStatusData>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'sketchStatusChanged' | 是 | 事件类型。取值固定为**'sketchStatusChanged'**。该事件可在创建画中画预览流时监听。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[SketchStatusData](arkts-camera-camera-sketchstatusdata-i-sys.md)&gt; | 否 | 用于返回结果的回调。该参数为可选参数。若指定该参数，则取消对指定事件**on('sketchStatusChanged')** 中指定回调的订阅。（回调对象不能是匿名函数。） |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |

<!--Del-->
**示例**

```TypeScript
function unregisterSketchStatusChanged(previewOutput: camera.PreviewOutput): void {
  previewOutput.off('sketchStatusChanged');
}
```

<!--DelEnd-->

## on('sketchStatusChanged')

```TypeScript
on(type: 'sketchStatusChanged', callback: AsyncCallback<SketchStatusData>): void
```

订阅画中画状态变化事件。该接口使用异步回调返回结果。

**起始版本：** 11

<!--Device-PreviewOutput-on(type: 'sketchStatusChanged', callback: AsyncCallback<SketchStatusData>): void--><!--Device-PreviewOutput-on(type: 'sketchStatusChanged', callback: AsyncCallback<SketchStatusData>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'sketchStatusChanged' | 是 | 事件类型。取值固定为**'sketchStatusChanged'**。该事件可在创建画中画预览流时监听。当画中画预览使能、去使能，或使能画中画预览后变焦比变化时，会触发该事件。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[SketchStatusData](arkts-camera-camera-sketchstatusdata-i-sys.md)&gt; | 是 | 用于返回画中画状态数据的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |

<!--Del-->
**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function callback(error: BusinessError, data: camera.SketchStatusData): void {
  if (error !== undefined && error.code !== 0) {
    console.error(`Callback Error, errorCode: ${error.code}`);
    return;
  }
  console.info(`sketch errorCode is ${error.code}, data is ${JSON.stringify(data)}`);
}

function registerSketchStatusChanged(previewOutput: camera.PreviewOutput): void {
  previewOutput.on('sketchStatusChanged', callback);
}
```

<!--DelEnd-->
