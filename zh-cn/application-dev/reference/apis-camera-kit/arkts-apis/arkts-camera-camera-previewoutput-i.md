# PreviewOutput

预览输出类。继承[CameraOutput](arkts-camera-camera-cameraoutput-i.md)。

**继承/实现关系：** PreviewOutput extends [CameraOutput](arkts-camera-camera-cameraoutput-i.md)

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.Camera.Core

## 导入模块

```TypeScript
```

## addDeferredSurface

```TypeScript
addDeferredSurface(surfaceId: string): void
```

配置延迟预览的Surface，可以在[commitConfig](arkts-camera-camera-session-i.md#commitconfig)配流和[start](arkts-camera-camera-session-i.md#start)启流之后 运行。

**起始版本：** 24

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| surfaceId | string | 是 | 从XComponent组件获取的surfaceId。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed. A non-system application calls a system API.<br>**适用版本：** 13 - 23 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function preview(cameraManager: camera.CameraManager, cameraInfo: camera.CameraDevice, previewProfile: camera.Profile, photoProfile: camera.Profile, mode: camera.SceneMode, previewSurfaceId: string): Promise<void> {
  let cameraInput: camera.CameraInput = cameraManager.createCameraInput(cameraInfo);
  let previewOutput: camera.PreviewOutput = cameraManager.createDeferredPreviewOutput(previewProfile);
  let photoOutput: camera.PhotoOutput = cameraManager.createPhotoOutput(photoProfile);
  let session: camera.Session  = cameraManager.createSession(mode);
  session.beginConfig();
  session.addInput(cameraInput);
  session.addOutput(previewOutput);
  session.addOutput(photoOutput);
  await session.commitConfig();
  try {
    await session.start();
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`start session failed. error code: ${err.code}`);
  }
  previewOutput.addDeferredSurface(previewSurfaceId);
}
```

## enableBandwidthCompression

```TypeScript
enableBandwidthCompression(enabled: boolean): void
```

使能预览带宽压缩。使能之前，可先使用方法[isBandwidthCompressionSupported](#isbandwidthcompressionsupported)对设备是否支持预览 带宽压缩进行检查。

> **说明：**
> 
> 该接口只能在使用[Session.commitConfig](arkts-camera-camera-session-i.md#commitconfig)接口之前调用，否则会影响预览流
> 出流格式。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | 是否使能预览带宽压缩。true表示使能，false表示不使能。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function enableBandwidthCompression(previewOutput: camera.PreviewOutput, enabled: boolean): void {
  try {
    previewOutput.enableBandwidthCompression(enabled);
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The previewOutput.enableBandwidthCompression call failed. error code: ${err.code}`);
  }
}
```

## getActiveFrameRate

```TypeScript
getActiveFrameRate(): FrameRateRange
```

获取已设置的帧率范围。使用[setFrameRate](#setframerate)接口对预览流设置过帧率后可查询。

**起始版本：** 12

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FrameRateRange](arkts-camera-camera-frameraterange-i.md) | 帧率范围 |

**示例**

```TypeScript
function getActiveFrameRate(previewOutput: camera.PreviewOutput): camera.FrameRateRange {
  let activeFrameRate: camera.FrameRateRange = previewOutput.getActiveFrameRate();
  return activeFrameRate;
}
```

```TypeScript
function getActiveFrameRate(videoOutput: camera.VideoOutput): camera.FrameRateRange {
  let activeFrameRate: camera.FrameRateRange = videoOutput.getActiveFrameRate();
  return activeFrameRate;
}
```

## getActiveProfile

```TypeScript
getActiveProfile(): Profile
```

获取当前生效的配置信息。

**起始版本：** 12

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Profile](arkts-camera-camera-profile-i.md) | 当前生效的配置信息 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function testGetActiveProfile(photoOutput: camera.PhotoOutput): camera.Profile | undefined {
  let activeProfile: camera.Profile | undefined = undefined;
  try {
    activeProfile = photoOutput.getActiveProfile();
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The photoOutput.getActiveProfile call failed. error code: ${err.code}`);
  }
  return activeProfile;
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function testGetActiveProfile(previewOutput: camera.PreviewOutput): camera.Profile | undefined {
  let activeProfile: camera.Profile | undefined = undefined;
  try {
    activeProfile = previewOutput.getActiveProfile();
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The previewOutput.getActiveProfile call failed. error code: ${err.code}`);
  }
  return activeProfile;
}
```

## getPreviewRotation

```TypeScript
getPreviewRotation(displayRotation?: number): ImageRotation
```

获取预览旋转角度。  
- 设备自然方向：设备默认使用方向。例如，直板机默认使用方向为竖屏（充电口向下）。  
- 相机镜头角度：值等于相机图像顺时针旋转到设备自然方向的角度。例如，直板机后置相机传感器是横屏安装的，所以需要顺时针旋转90度到设备自然方向。  
- [屏幕旋转角度](https://developer.huawei.com/consumer/cn/doc/best-practices/bpta-multi-device-window-direction#section737072712182)： 显示设备的屏幕顺时针旋转角度。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| displayRotation | number | 否 | 显示设备的屏幕旋转角度，通过 [display.getDefaultDisplaySync](../../apis-arkui/arkts-apis/arkts-arkui-display-getdefaultdisplaysync-f.md)获得。 从API version 23开始，入参displayRotation为可选参数，当不传入参数时，由系统获取displayRotation进行预览旋转角度计算。 单位为度数（degree），取值范围为[0, 360]。<br>**起始版本：** 23 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ImageRotation](arkts-camera-camera-imagerotation-e.md) | 返回预览旋转角度。若接口调用失败，返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect.<br>**适用版本：** 12 - 22 |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function testGetPreviewRotation(previewOutput: camera.PreviewOutput, imageRotation : camera.ImageRotation): camera.ImageRotation {
  let previewRotation: camera.ImageRotation = camera.ImageRotation.ROTATION_0;
  try {
    previewRotation = previewOutput.getPreviewRotation(imageRotation);
    console.info(`Preview rotation is: ${previewRotation}`);
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The previewOutput.getPreviewRotation call failed. error code: ${err.code}`);
  }
  return previewRotation;
}

function testGetPreviewRotationWithOutParam(previewOutput: camera.PreviewOutput): camera.ImageRotation {
  let previewRotation: camera.ImageRotation = camera.ImageRotation.ROTATION_0;
  try {
    previewRotation = previewOutput.getPreviewRotation();
    console.info(`Preview rotation is: ${previewRotation}`);
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The previewOutput.testGetPreviewRotationWithOutParam call failed. error code: ${err.code}`);
  }
  return previewRotation;
}
```

## getSupportedFrameRates

```TypeScript
getSupportedFrameRates(): Array<FrameRateRange>
```

查询支持的帧率范围。

**起始版本：** 12

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[FrameRateRange](arkts-camera-camera-frameraterange-i.md)&gt; | 支持的帧率范围列表。若接口调用失败，返回undefined。 |

**示例**

```TypeScript
function getSupportedFrameRates(previewOutput: camera.PreviewOutput): Array<camera.FrameRateRange> {
  let supportedFrameRatesArray: Array<camera.FrameRateRange> = previewOutput.getSupportedFrameRates();
  return supportedFrameRatesArray;
}
```

```TypeScript
function getSupportedFrameRates(videoOutput: camera.VideoOutput): Array<camera.FrameRateRange> {
  let supportedFrameRatesArray: Array<camera.FrameRateRange> = videoOutput.getSupportedFrameRates();
  return supportedFrameRatesArray;
}
```

## isBandwidthCompressionSupported

```TypeScript
isBandwidthCompressionSupported(): boolean
```

检查是否支持预览带宽压缩（指通过编码减少数据量，降低其在传输链路中的带宽占用）。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 是否支持预览带宽压缩。true表示支持，false表示不支持。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function isBandwidthCompressionSupported(previewOutput: camera.PreviewOutput): boolean {
  let supported: boolean = false;
  try {
    supported = previewOutput.isBandwidthCompressionSupported();
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The previewOutput.isBandwidthCompressionSupported call failed. error code: ${err.code}`);
  }
  return supported;
}
```

## isLogViewAssistSupported

```TypeScript
isLogViewAssistSupported(): boolean
```

LOG视频下，查询是否支持辅助监看功能。辅助监看开启后，预览画面还原至原色域，录制出的视频仍然是LOG视频格式。

> **说明：**
> 
> 辅助监看效果仅支持1080P及以下分辨率。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 是否支持辅助监看功能。true表示支持，false表示不支持。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function isLogViewAssistSupported(previewOutput: camera.PreviewOutput): boolean {
  let supported: boolean = false;
  try {
      supported = previewOutput.isLogViewAssistSupported();
  } catch (error) {
      // 失败返回错误码error.code并处理。
      let err = error as BusinessError;
      console.error(`The previewOutput.isLogViewAssistSupported call failed. error code: ${err.code}`);
  }
  return supported;
}
```

## off('frameStart')

```TypeScript
off(type: 'frameStart', callback?: AsyncCallback<void>): void
```

注销预览帧启动的监听。

**起始版本：** 10

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'frameStart' | 是 | 监听事件，固定为'frameStart'，previewOutput创建成功可监听。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 否 | 回调函数，如果指定参数则取消对应callback（callback对象不可是匿名函数），否则取消所有callback。 |

## off('frameEnd')

```TypeScript
off(type: 'frameEnd', callback?: AsyncCallback<void>): void
```

注销监听预览帧结束。

**起始版本：** 10

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'frameEnd' | 是 | 监听事件，固定为'frameEnd'，previewOutput创建成功可监听。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 否 | 回调函数，如果指定参数则取消对应callback（callback对象不可是匿名函数），否则取消所有callback。 |

## off('error')

```TypeScript
off(type: 'error', callback?: ErrorCallback): void
```

注销监听预览输出的错误事件。

**起始版本：** 10

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 监听事件，固定为'error'，previewOutput创建成功可监听。 |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | 否 | 回调函数，如果指定参数则取消对应callback（callback对象不可是匿名函数），否则取消所有callback。 |

## on('frameStart')

```TypeScript
on(type: 'frameStart', callback: AsyncCallback<void>): void
```

监听预览帧启动，通过注册回调函数获取结果。使用callback异步回调。

> **说明：**
> 
> 当前注册监听接口，不支持在on监听的回调方法里，调用off注销回调。

**起始版本：** 10

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'frameStart' | 是 | 监听事件，固定为'frameStart'，previewOutput创建成功可监听。底层第一次开始曝光时触发该事件并返回。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数，用于获取结果。只要有该事件返回就证明预览开始。 |

## on('frameEnd')

```TypeScript
on(type: 'frameEnd', callback: AsyncCallback<void>): void
```

监听预览帧结束，通过注册回调函数获取结果。使用callback异步回调。

> **说明：**
> 
> 当前注册监听接口，不支持在on监听的回调方法里，调用off注销回调。

**起始版本：** 10

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'frameEnd' | 是 | 监听事件，固定为'frameEnd'，previewOutput创建成功可监听。预览完全结束最后一帧时触发该事件并返回。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数，用于获取结果。只要有该事件返回就证明预览结束。 |

## on('error')

```TypeScript
on(type: 'error', callback: ErrorCallback): void
```

监听预览输出的错误事件，通过注册回调函数获取结果。使用callback异步回调。

> **说明：**
> 
> 当前注册监听接口，不支持在on监听的回调方法里，调用off注销回调。

**起始版本：** 10

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 监听事件，固定为'error'，previewOutput创建成功可监听。预览接口使用错误时触发该事件，比如调用 [Session.start](arkts-camera-camera-session-i.md#start)，[CameraOutput.release](arkts-camera-camera-cameraoutput-i.md#release)等接口发 生错误时返回对应错误信息。 |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | 是 | 回调函数，用于获取错误信息。返回错误码，错误码类型[CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md)。 |

## setFrameRate

```TypeScript
setFrameRate(minFps: number, maxFps: number): void
```

设置预览流帧率范围，设置的范围必须在支持的帧率范围内。进行设置前，可通过[getSupportedFrameRates](#getsupportedframerates)接口查询支持的帧率范围。

> **说明：**
> 
> 仅在[PhotoSession](arkts-camera-camera-photosession-i.md)或[VideoSession](arkts-camera-camera-videosession-i.md)模式下支持。

**起始版本：** 12

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| minFps | number | 是 | 最小帧率（单位：fps），当传入的最大值小于最小值时，传参异常，接口不生效。 |
| maxFps | number | 是 | 最大帧率（单位：fps），当传入的最小值大于最大值时，传参异常，接口不生效。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400110](../errorcode-camera.md#7400110-与当前配置存在冲突) | Unresolved conflicts with current configurations. |

**示例**

```TypeScript
function setFrameRateRange(previewOutput: camera.PreviewOutput, frameRateRange: Array<number>): void {
  previewOutput.setFrameRate(frameRateRange[0], frameRateRange[1]);
}
```

```TypeScript
function setFrameRateRange(videoOutput: camera.VideoOutput, frameRateRange: Array<number>): void {
  videoOutput.setFrameRate(frameRateRange[0], frameRateRange[1]);
}
```

## setLogViewAssistEnable

```TypeScript
setLogViewAssistEnable(enable: boolean): void
```

LOG视频下，使能辅助监看之前，可先使用方法[isLogViewAssistSupported](#islogviewassistsupported)查询设备是否支持预览辅助 监看。

> **说明：**
> 
> - 该接口只能在使用[Session.commitConfig](arkts-camera-camera-session-i.md#commitconfig)接口之后调用。
> 
> - 预览辅助监看效果仅支持1080P及以下分辨率。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean | 是 | 是否使能辅助监看。true表示使能，false表示不使能。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function setLogViewAssistEnable(previewOutput: camera.PreviewOutput, enable: boolean): void {
  try {
      previewOutput.setLogViewAssistEnable(enable);
  } catch (error) {
      // 失败返回错误码error.code并处理。
      let err = error as BusinessError;
      console.error(`The previewOutput.setLogViewAssistEnable call failed. error code: ${err.code}`);
  }
}
```

## setPreviewRotation

```TypeScript
setPreviewRotation(previewRotation: ImageRotation, isDisplayLocked?: boolean): void
```

设置预览旋转角度。

**起始版本：** 12

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| previewRotation | [ImageRotation](arkts-camera-camera-imagerotation-e.md) | 是 | 预览旋转角度 |
| isDisplayLocked | boolean | 否 | Surface在屏幕旋转时是否锁定方向，未设置时默认取值为false，即不锁定方向。true表示锁定方向，false表示不锁定方向。详情请参考 [SurfaceRotationOptions](../../apis-arkui/arkts-components/arkts-arkui-surfacerotationoptions-i.md) |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function testSetPreviewRotation(previewOutput: camera.PreviewOutput, previewRotation : camera.ImageRotation, isDisplayLocked: boolean): void {
  try {
    previewOutput.setPreviewRotation(previewRotation, isDisplayLocked);
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The previewOutput.setPreviewRotation call failed. error code: ${err.code}`);
  }
  return;
}
```

## start

```TypeScript
start(callback: AsyncCallback<void>): void
```

开始输出预览流，通过注册回调函数获取结果。使用callback异步回调。

> **说明：**
> 
> 从 API version 10开始支持，从API version 11开始废弃。

**起始版本：** 10

**废弃版本：** 11

**替代接口：** [start](arkts-camera-camera-session-i.md#start)(callback: AsyncCallback&lt;void&gt;)

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当开始输出预览流成功，err为undefined，否则为错误对象。错误码类型 [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md)。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

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

开始输出预览流。使用Promise异步回调。

> **说明：**
> 
> 从 API version 10开始支持，从API version 11开始废弃。

**起始版本：** 10

**废弃版本：** 11

**替代接口：** [start](arkts-camera-camera-session-i.md#start)()

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

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

停止输出预览流，通过注册回调函数获取结果。使用callback异步回调。

> **说明：**
> 
> 从 API version 10开始支持，从API version 11开始废弃。

**起始版本：** 10

**废弃版本：** 11

**替代接口：** [stop](arkts-camera-camera-session-i.md#stop)(callback: AsyncCallback&lt;void&gt;)

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当停止输出预览流成功，err为undefined，否则为错误对象。 |

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

停止输出预览流。使用Promise异步回调。

> **说明：**
> 
> 从 API version 10开始支持，从API version 11开始废弃。

**起始版本：** 10

**废弃版本：** 11

**替代接口：** [stop](arkts-camera-camera-session-i.md#stop)()

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

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
