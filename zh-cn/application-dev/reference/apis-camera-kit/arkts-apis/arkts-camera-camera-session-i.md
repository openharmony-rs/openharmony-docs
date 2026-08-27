# Session

会话类，保存一次相机运行所需要的所有资源[CameraInput](arkts-camera-camera-camerainput-i.md)、[CameraOutput](arkts-camera-camera-cameraoutput-i.md)，并向相机设备申请完成相机功 能（录像，拍照）。

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Camera.Core

## 导入模块

```TypeScript
```

## addInput

```TypeScript
addInput(cameraInput: CameraInput): void
```

把[CameraInput](arkts-camera-camera-camerainput-i.md)加入到会话。

**起始版本：** 11

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| cameraInput | [CameraInput](arkts-camera-camera-camerainput-i.md) | 是 | 需要添加的CameraInput实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config.<br>**适用版本：** 11 - 17 |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error.<br>**适用版本：** 12+ |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function addInput(captureSession: camera.CaptureSession, cameraInput: camera.CameraInput): void {
  try {
    captureSession.addInput(cameraInput);
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The addInput call failed. error code: ${err.code}`);
  }
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function addInput(session: camera.Session, cameraInput: camera.CameraInput): void {
  try {
    session.addInput(cameraInput);
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The addInput call failed. error code: ${err.code}`);
  }
}
```

## addOutput

```TypeScript
addOutput(cameraOutput: CameraOutput): void
```

把[CameraOutput](arkts-camera-camera-cameraoutput-i.md)加入到会话。

**起始版本：** 11

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| cameraOutput | [CameraOutput](arkts-camera-camera-cameraoutput-i.md) | 是 | 需要添加的CameraOutput实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config.<br>**适用版本：** 11 - 17 |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error.<br>**适用版本：** 12+ |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function addOutput(captureSession: camera.CaptureSession, cameraOutput: camera.CameraOutput): void {
  try {
    captureSession.addOutput(cameraOutput);
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The addOutput call failed. error code: ${err.code}`);
  }
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function addOutput(session: camera.Session, cameraOutput: camera.CameraOutput): void {
  try {
    session.addOutput(cameraOutput);
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The addOutput call failed. error code: ${err.code}`);
  }
}
```

## beginConfig

```TypeScript
beginConfig(): void
```

开始配置会话。

**起始版本：** 11

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400105](../errorcode-camera.md#7400105-会话配置被锁定) | Session config locked. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error.<br>**适用版本：** 12+ |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function beginConfig(captureSession: camera.CaptureSession): void {
  try {
    captureSession.beginConfig();
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The beginConfig call failed. error code: ${err.code}`);
  }
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function beginConfig(session: camera.Session): void {
  try {
    session.beginConfig();
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The beginConfig call failed. error code: ${err.code}`);
  }
}
```

## canAddInput

```TypeScript
canAddInput(cameraInput: CameraInput): boolean
```

判断当前cameraInput是否可以添加到session中。当前函数需要在[beginConfig](#beginconfig)和 [commitConfig](#commitconfig)之间生效。

**起始版本：** 11

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| cameraInput | [CameraInput](arkts-camera-camera-camerainput-i.md) | 是 | 需要添加的CameraInput实例。传参异常（如超出范围、传入null、未定义等），实际接口不会生效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 判断当前cameraInput是否可以添加到session中。true表示支持添加当前cameraInput，false表示不支持添加。 |

**示例**

```TypeScript
function canAddInput(session: camera.Session, cameraInput: camera.CameraInput): void {
  let canAdd: boolean = session.canAddInput(cameraInput);
  console.info(`The input canAddInput: ${canAdd}`);
}
```

## canAddOutput

```TypeScript
canAddOutput(cameraOutput: CameraOutput): boolean
```

判断当前cameraOutput是否可以添加到session中。当前函数需要在[addInput](#addinput)和 [commitConfig](#commitconfig)之间生效。

**起始版本：** 11

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| cameraOutput | [CameraOutput](arkts-camera-camera-cameraoutput-i.md) | 是 | 需要添加的CameraOutput实例。传参异常（如超出范围、传入null、未定义等），实际接口不会生效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 是否可以添加当前cameraOutput到session中，true为可添加，false为不可添加。 |

**示例**

```TypeScript
function canAddOutput(session: camera.Session, cameraOutput: camera.CameraOutput): void {
  let canAdd: boolean = session.canAddOutput(cameraOutput);
  console.info(`This addOutput can add: ${canAdd}`);
}
```

## commitConfig

```TypeScript
commitConfig(callback: AsyncCallback<void>): void
```

提交配置信息，通过注册回调函数获取结果。使用callback异步回调。

**起始版本：** 11

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当提交配置信息成功，err为undefined，否则为错误对象。错误码类型 [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md)，比如预览流与录像输出流的分辨率的宽高比不一致，会返回7400201。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function commitConfig(captureSession: camera.CaptureSession): void {
  captureSession.commitConfig((err: BusinessError) => {
    if (err) {
      console.error(`The commitConfig call failed. error code: ${err.code}`);
      return;
    }
    console.info('Callback invoked to indicate the commit config success.');
  });
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function commitConfig(session: camera.Session): void {
  session.commitConfig((err: BusinessError) => {
    if (err) {
      console.error(`The commitConfig call failed. error code: ${err.code}`);
      return;
    }
    console.info('Callback invoked to indicate the commit config success.');
  });
}
```

## commitConfig

```TypeScript
commitConfig(): Promise<void>
```

提交配置信息。使用Promise异步回调。

**起始版本：** 11

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function commitConfig(captureSession: camera.CaptureSession): void {
  captureSession.commitConfig().then(() => {
    console.info('Promise returned to indicate the commit config success.');
  }).catch((error: BusinessError) => {
    // 失败返回错误码error.code并处理。
    console.error(`The commitConfig call failed. error code: ${error.code}`);
  });
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function commitConfig(session: camera.Session): void {
  session.commitConfig().then(() => {
    console.info('Promise returned to indicate the commit config success.');
  }).catch((error: BusinessError) => {
    // 失败返回错误码error.code并处理。
    console.error(`The commitConfig call failed. error code: ${error.code}`);
  });
}
```

## release

```TypeScript
release(callback: AsyncCallback<void>): void
```

释放会话资源，通过注册回调函数获取结果。使用callback异步回调。

**起始版本：** 11

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当释放会话资源成功，err为undefined，否则为错误对象。错误码类型 [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md)。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function releasePreviewOutput(previewOutput: camera.PreviewOutput): void {
  previewOutput.release((err: BusinessError) => {
    if (err) {
      console.error(`Failed to release the Preview output instance ${err.code}`);
      return;
    }
    console.info('Callback invoked to indicate that the preview output instance is released successfully.');
  });
}

function releaseVideoOutput(videoOutput: camera.VideoOutput): void {
  videoOutput.release((err: BusinessError) => {
    if (err) {
      console.error(`Failed to release the video output instance ${err.code}`);
      return;
    }
    console.info('Callback invoked to indicate that the video output instance is released successfully.');
  });
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function releaseCaptureSession(captureSession: camera.CaptureSession): void {
  captureSession.release((err: BusinessError) => {
    if (err) {
      console.error(`Failed to release the CaptureSession instance, error code: ${err.code}.`);
      return;
    }
    console.info('Callback invoked to indicate that the CaptureSession instance is released successfully.');
  });
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function releaseCaptureSession(session: camera.Session): void {
  session.release((err: BusinessError) => {
    if (err) {
      console.error(`Failed to release the session instance, error code: ${err.code}.`);
      return;
    }
    console.info('Callback invoked to indicate that the session instance is released successfully.');
  });
}
```

## release

```TypeScript
release(): Promise<void>
```

释放会话资源。使用Promise异步回调。

**起始版本：** 11

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

**示例**

```TypeScript
async function releaseDepthData(depthData: camera.DepthData): Promise<void> {
  await depthData.release();
}
```

```TypeScript
async function releaseDeferredPhotoProxy(proxyObj: camera.DeferredPhotoProxy): Promise<void> {
  await proxyObj.release();
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function releasePreviewOutput(previewOutput: camera.PreviewOutput): void {
  previewOutput.release().then(() => {
    console.info('Promise returned to indicate that the preview output instance is released successfully.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to preview output release, error code: ${error.code}`);
  });
}

function releaseVideoOutput(videoOutput: camera.VideoOutput): void {
  videoOutput.release().then(() => {
    console.info('Promise returned to indicate that the video output instance is released successfully.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to video output release, error code: ${error.code}`);
  });
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function releaseCaptureSession(captureSession: camera.CaptureSession): void {
  captureSession.release().then(() => {
    console.info('Promise returned to indicate that the CaptureSession instance is released successfully.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to release the CaptureSession instance, error code: ${err.code}.`);
  });
}
```

```TypeScript
async function releasePhoto(photo: camera.Photo): Promise<void> {
  await photo.release();
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function releaseCaptureSession(session: camera.Session): void {
  session.release().then(() => {
    console.info('Promise returned to indicate that the session instance is released successfully.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to release the session instance, error code: ${error.code}.`);
  });
}
```

```TypeScript
import { camera } from '@kit.CameraKit';

async function releaseCapturePhoto(capturePhoto: camera.CapturePhoto): Promise<void> {
  await capturePhoto.release();
}
```

## removeInput

```TypeScript
removeInput(cameraInput: CameraInput): void
```

移除[CameraInput](arkts-camera-camera-camerainput-i.md)。当前函数需要在[beginConfig](#beginconfig)和 [commitConfig](#commitconfig)之间生效。

**起始版本：** 11

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| cameraInput | [CameraInput](arkts-camera-camera-camerainput-i.md) | 是 | 需要移除的CameraInput实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config.<br>**适用版本：** 11 - 17 |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error.<br>**适用版本：** 12+ |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function removeInput(captureSession: camera.CaptureSession, cameraInput: camera.CameraInput): void {
  try {
    captureSession.removeInput(cameraInput);
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The removeInput call failed. error code: ${err.code}`);
  }
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function removeInput(session: camera.Session, cameraInput: camera.CameraInput): void {
  try {
    session.removeInput(cameraInput);
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The removeInput call failed. error code: ${err.code}`);
  }
}
```

## removeOutput

```TypeScript
removeOutput(cameraOutput: CameraOutput): void
```

从会话中移除[CameraOutput](arkts-camera-camera-cameraoutput-i.md)。

**起始版本：** 11

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| cameraOutput | [CameraOutput](arkts-camera-camera-cameraoutput-i.md) | 是 | 需要移除的CameraOutput实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config.<br>**适用版本：** 11 - 17 |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error.<br>**适用版本：** 12+ |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function removeOutput(captureSession: camera.CaptureSession, previewOutput: camera.PreviewOutput): void {
  try {
    captureSession.removeOutput(previewOutput);
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The removeOutput call failed. error code: ${err.code}`);
  }
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function removeOutput(session: camera.Session, previewOutput: camera.PreviewOutput): void {
  try {
    session.removeOutput(previewOutput);
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The removeOutput call failed. error code: ${err.code}`);
  }
}
```

## start

```TypeScript
start(callback: AsyncCallback<void>): void
```

开始会话工作，通过注册回调函数获取结果。使用callback异步回调。

**起始版本：** 11

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当开始会话工作成功，err为undefined，否则为错误对象。错误码类型 [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md)。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed.<br>**适用版本：** 12+ |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function startCaptureSession(captureSession: camera.CaptureSession): void {
  captureSession.start((err: BusinessError) => {
    if (err) {
      console.error(`Failed to start the session, error code: ${err.code}.`);
      return;
    }
    console.info('Callback invoked to indicate the session start success.');
  });
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function startMetadataOutput(metadataOutput: camera.MetadataOutput): void {
  metadataOutput.start((err: BusinessError) => {
    if (err) {
      console.error(`Failed to start metadata output, error code: ${err.code}.`);
      return;
    }
    console.info('Callback returned with metadata output started.');
  });
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function startPreviewOutput(previewOutput: camera.PreviewOutput): void {
  previewOutput.start((err: BusinessError) => {
    if (err) {
      console.error(`Failed to start the preview output, error code: ${err.code}.`);
      return;
    }
    console.info('Callback returned with preview output started.');
  });
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function startCaptureSession(session: camera.Session): void {
  session.start((err: BusinessError) => {
    if (err) {
      console.error(`Failed to start the session, error code: ${err.code}.`);
      return;
    }
    console.info('Callback invoked to indicate the session start success.');
  });
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function startVideoOutput(videoOutput: camera.VideoOutput): void {
  videoOutput.start((err: BusinessError) => {
    if (err.code) {
      console.error(`Failed to start the video output, error code: ${err.code}.`);
      return;
    }
    console.info('Callback invoked to indicate the video output start success.');
  });
}
```

## start

```TypeScript
start(): Promise<void>
```

开始会话工作。使用Promise异步回调。

**起始版本：** 11

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed.<br>**适用版本：** 12+ |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function startDepthDataOutput(depthDataOutput: camera.DepthDataOutput): void {
  depthDataOutput.start().then(() => {
    console.info('Promise returned to indicate that start method execution success.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to depth data output start, error code: ${error.code}.`);
  });
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function startCaptureSession(captureSession: camera.CaptureSession): void {
  captureSession.start().then(() => {
    console.info('Promise returned to indicate the session start success.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to start the session, error code: ${err.code}.`);
  });
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function startMetadataOutput(metadataOutput: camera.MetadataOutput): void {
  metadataOutput.start().then(() => {
    console.info('Callback returned with metadata output started.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to metadata output start, error code: ${error.code}`);
  });
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function startPreviewOutput(previewOutput: camera.PreviewOutput): void {
  previewOutput.start().then(() => {
    console.info('Promise returned with preview output started.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to preview output start, error code: ${error.code}.`);
  });
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function startCaptureSession(session: camera.Session): void {
  session.start().then(() => {
    console.info('Promise returned to indicate the session start success.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to start the session, error code: ${error.code}.`);
  });
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function startVideoOutput(videoOutput: camera.VideoOutput): void {
  videoOutput.start().then(() => {
    console.info('Promise returned to indicate that start method execution success.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to video output start, error code: ${error.code}.`);
  });
}
```

## stop

```TypeScript
stop(callback: AsyncCallback<void>): void
```

停止会话工作，通过注册回调函数获取结果。使用callback异步回调。

**起始版本：** 11

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当停止会话工作成功，err为undefined，否则为错误对象。错误码类型 [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md)。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function stopCaptureSession(captureSession: camera.CaptureSession): void {
  captureSession.stop((err: BusinessError) => {
    if (err) {
      console.error(`Failed to stop the session, error code: ${err.code}.`);
      return;
    }
    console.info('Callback invoked to indicate the session stop success.');
  });
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function stopMetadataOutput(metadataOutput: camera.MetadataOutput): void {
  metadataOutput.stop((err: BusinessError) => {
    if (err) {
      console.error(`Failed to stop the metadata output, error code: ${err.code}.`);
      return;
    }
    console.info('Callback returned with metadata output stopped.');
  })
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function stopPreviewOutput(previewOutput: camera.PreviewOutput): void {
  previewOutput.stop((err: BusinessError) => {
    if (err) {
      console.error(`Failed to stop the preview output, error code: ${err.code}.`);
      return;
    }
    console.info('Returned with preview output stopped.');
  })
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function stopCaptureSession(session: camera.Session): void {
  session.stop((err: BusinessError) => {
    if (err) {
      console.error(`Failed to stop the session, error code: ${err.code}.`);
      return;
    }
    console.info('Callback invoked to indicate the session stop success.');
  });
}
```

```TypeScript
function stopVideoOutput(videoOutput: camera.VideoOutput): void {
  videoOutput.stop(() => {
    console.info('Callback invoked to indicate the video output stop success.');
  });
}
```

## stop

```TypeScript
stop(): Promise<void>
```

停止会话工作。使用Promise异步回调。

**起始版本：** 11

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function stopDepthDataOutput(depthDataOutput: camera.DepthDataOutput): void {
  depthDataOutput.stop().then(() => {
    console.info('Promise returned to indicate that stop method execution success.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to depth data output stop, error code: ${error.code}.`);
  });
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function stopCaptureSession(captureSession: camera.CaptureSession): void {
  captureSession.stop().then(() => {
    console.info('Promise returned to indicate the session stop success.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to stop the session, error code: ${err.code}.`);
  });
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function stopMetadataOutput(metadataOutput: camera.MetadataOutput): void {
  metadataOutput.stop().then(() => {
    console.info('Callback returned with metadata output stopped.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to metadata output stop, error code: ${error.code}`);
  });
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function stopPreviewOutput(previewOutput: camera.PreviewOutput): void {
  previewOutput.stop().then(() => {
    console.info('Callback returned with preview output stopped.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to preview output stop, error code: ${error.code}.`);
  });
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function stopCaptureSession(session: camera.Session): void {
  session.stop().then(() => {
    console.info('Promise returned to indicate the session stop success.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to stop the session, error code: ${error.code}.`);
  });
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function stopVideoOutput(videoOutput: camera.VideoOutput): void {
  videoOutput.stop().then(() => {
    console.info('Promise returned to indicate that stop method execution success.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to video output stop, error code: ${error.code}.`);
  });
}
```
