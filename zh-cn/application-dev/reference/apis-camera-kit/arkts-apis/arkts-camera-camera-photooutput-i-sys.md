# PhotoOutput（系统接口）

```TypeScript
interface PhotoOutput extends CameraOutput
```

拍照会话中使用的输出信息。

**继承/实现关系：** PhotoOutput extends [CameraOutput](arkts-camera-camera-cameraoutput-i.md)

**起始版本：** 10

<!--Device-camera-interface PhotoOutput extends CameraOutput--><!--Device-camera-interface PhotoOutput extends CameraOutput-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
```

## burstCapture

```TypeScript
burstCapture(setting: PhotoCaptureSetting): Promise<void>
```

启动连拍模式，用户可连续快速拍摄多张照片。该接口通常用于拍照模式。连拍开始后，底层会持续显示照片。可调用[confirmCapture](#confirmcapture) 取消连拍模式。该接口使用 Promise返回结果。

**起始版本：** 12

<!--Device-PhotoOutput-burstCapture(setting: PhotoCaptureSetting): Promise<void>--><!--Device-PhotoOutput-burstCapture(setting: PhotoCaptureSetting): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| setting | [PhotoCaptureSetting](arkts-camera-camera-photocapturesetting-i.md) | 是 | 拍照参数。传入 **undefined** 时按未传参处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回值的 Promise。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400104](../errorcode-camera.md#7400104-会话未运行) | Session not running. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

<!--Del-->
**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function burstCapture(photoOutput: camera.PhotoOutput): void {
  let captureLocation: camera.Location = {
    latitude: 0,
    longitude: 0,
    altitude: 0
  }
  let settings: camera.PhotoCaptureSetting = {
    quality: camera.QualityLevel.QUALITY_LEVEL_LOW,
    rotation: camera.ImageRotation.ROTATION_0,
    location: captureLocation,
    mirror: false
  }
  photoOutput.burstCapture(settings).then(() => {
    console.info('Promise returned to indicate that photo burstCapture request success.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to photo output burstCapture, error code: ${error.code}.`);
  });
}
```

<!--DelEnd-->

## confirmCapture

```TypeScript
confirmCapture(): void
```

确认拍照。该接口通常用于夜间拍照模式下用户需要停止曝光倒计时并提前拍照的场景。该接口用于结束由[burstCapture](#burstcapture) 启动的连拍模式。

**起始版本：** 11

<!--Device-PhotoOutput-confirmCapture(): void--><!--Device-PhotoOutput-confirmCapture(): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400104](../errorcode-camera.md#7400104-会话未运行) | Session not running. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

<!--Del-->
**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function confirmCapture(photoOutput: camera.PhotoOutput): void {
  try {
    photoOutput.confirmCapture();
  } catch (error) {
    let err = error as BusinessError;
    console.error(`The confirmCapture call failed. error code: ${err.code}`);
  }
}
```

<!--DelEnd-->

## deferImageDelivery

```TypeScript
deferImageDelivery(type: DeferredDeliveryImageType): void
```

使能指定类型的分段式投递。

**起始版本：** 11

<!--Device-PhotoOutput-deferImageDelivery(type: DeferredDeliveryImageType): void--><!--Device-PhotoOutput-deferImageDelivery(type: DeferredDeliveryImageType): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [DeferredDeliveryImageType](arkts-camera-camera-deferreddeliveryimagetype-e-sys.md) | 是 | 分段式投递的图像类型。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400104](../errorcode-camera.md#7400104-会话未运行) | Session not running. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

<!--Del-->
**示例**

```TypeScript
function deferImageDelivery(photoOutput: camera.PhotoOutput, type: camera.DeferredDeliveryImageType): void {
  photoOutput.deferImageDelivery(type);
}
```

<!--DelEnd-->

## enableAutoCloudImageEnhancement

```TypeScript
enableAutoCloudImageEnhancement(enabled: boolean): void
```

使能云端自动图像增强。

**起始版本：** 13

<!--Device-PhotoOutput-enableAutoCloudImageEnhancement(enabled: boolean): void--><!--Device-PhotoOutput-enableAutoCloudImageEnhancement(enabled: boolean): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | 云端自动图像增强的目标状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

## enableAutoHighQualityPhoto

```TypeScript
enableAutoHighQualityPhoto(enabled: boolean): void
```

使能照片自动高质量。使用该接口前，请先调用[isAutoHighQualityPhotoSupported](#isautohighqualityphotosupported) 检查是否支持自动高质量。

**起始版本：** 13

<!--Device-PhotoOutput-enableAutoHighQualityPhoto(enabled: boolean): void--><!--Device-PhotoOutput-enableAutoHighQualityPhoto(enabled: boolean): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | 是否使能照片自动高质量。**true**表示使能，**false**表示去使能。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400104](../errorcode-camera.md#7400104-会话未运行) | session is not running. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

<!--Del-->
**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function enableAutoHighQualityPhoto(photoOutput: camera.PhotoOutput): void {
  return photoOutput.enableAutoHighQualityPhoto(true);
}
```

<!--DelEnd-->

## enableDepthDataDelivery

```TypeScript
enableDepthDataDelivery(enabled: boolean): void
```

使能深度数据投递。

**起始版本：** 13

<!--Device-PhotoOutput-enableDepthDataDelivery(enabled: boolean): void--><!--Device-PhotoOutput-enableDepthDataDelivery(enabled: boolean): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | 深度数据投递的目标状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400104](../errorcode-camera.md#7400104-会话未运行) | Session not running. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

## enableOffline

```TypeScript
enableOffline(): void
```

使能离线处理。

**起始版本：** 18

<!--Device-PhotoOutput-enableOffline(): void--><!--Device-PhotoOutput-enableOffline(): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400104](../errorcode-camera.md#7400104-会话未运行) | session is not running. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

## enableOriginalImageGeneration

```TypeScript
enableOriginalImageGeneration(enabled: boolean): void
```

使能原图生成。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PhotoOutput-enableOriginalImageGeneration(enabled: boolean): void--><!--Device-PhotoOutput-enableOriginalImageGeneration(enabled: boolean): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | 为 TRUE 时使能原图生成。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

## enableQuickThumbnail

```TypeScript
enableQuickThumbnail(enabled: boolean): void
```

使能或去使能快速缩略图功能。该接口在调用 [addOutput](arkts-camera-camera-session-i.md#addoutput) 和[addInput](arkts-camera-camera-session-i.md#addinput) 之后、[commitConfig](arkts-camera-camera-session-i.md#commitconfig) 之前调用生效。

**起始版本：** 10

<!--Device-PhotoOutput-enableQuickThumbnail(enabled: boolean): void--><!--Device-PhotoOutput-enableQuickThumbnail(enabled: boolean): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | 是否使能快速缩略图功能。**true**表示使能，**false**表示去使能。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400104](../errorcode-camera.md#7400104-会话未运行) | session is not running. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application.<br>**适用版本：** 12+ |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect.<br>**适用版本：** 12+ |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error.<br>**适用版本：** 12+ |

<!--Del-->
**示例**

```TypeScript
import { common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { camera } from '@kit.CameraKit';

async function enableQuickThumbnail(context: common.BaseContext, mode: camera.SceneMode, photoProfile: camera.Profile): Promise<void> {
  let cameraManager: camera.CameraManager = camera.getCameraManager(context);
  let cameras: Array<camera.CameraDevice> = cameraManager.getSupportedCameras();
  // 创建CaptureSession实例。
  let session: camera.Session = cameraManager.createSession(mode);
  // 开始配置会话。
  session.beginConfig();
  // 把CameraInput加入到会话。
  let cameraInput: camera.CameraInput = cameraManager.createCameraInput(cameras[0]);
  await cameraInput.open();
  session.addInput(cameraInput);
  // 把PhotoOutPut加入到会话。
  let photoOutput: camera.PhotoOutput = cameraManager.createPhotoOutput(photoProfile);
  session.addOutput(photoOutput);
  let isSupported: boolean = photoOutput.isQuickThumbnailSupported();
  if (!isSupported) {
    console.info('Quick Thumbnail is not supported to be turned on.');
    return;
  }
  try {
    photoOutput.enableQuickThumbnail(true);
  } catch (error) {
    let err = error as BusinessError;
    console.error(`The enableQuickThumbnail call failed. error code: ${err.code}`);
  }
}
```

<!--DelEnd-->

## enableRawDelivery

```TypeScript
enableRawDelivery(enabled: boolean): void
```

使能 Raw 图像投递。

**起始版本：** 13

<!--Device-PhotoOutput-enableRawDelivery(enabled: boolean): void--><!--Device-PhotoOutput-enableRawDelivery(enabled: boolean): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | Raw 图像投递的目标状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400104](../errorcode-camera.md#7400104-会话未运行) | Session not running. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

## isAutoCloudImageEnhancementSupported

```TypeScript
isAutoCloudImageEnhancementSupported(): boolean
```

检查是否支持云端自动图像增强。

**起始版本：** 13

<!--Device-PhotoOutput-isAutoCloudImageEnhancementSupported(): boolean--><!--Device-PhotoOutput-isAutoCloudImageEnhancementSupported(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示是否支持云端自动图像增强。**true**表示支持。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

## isAutoHighQualityPhotoSupported

```TypeScript
isAutoHighQualityPhotoSupported(): boolean
```

检查是否支持照片自动高质量。

**起始版本：** 13

<!--Device-PhotoOutput-isAutoHighQualityPhotoSupported(): boolean--><!--Device-PhotoOutput-isAutoHighQualityPhotoSupported(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示是否支持自动高质量。**true**表示支持，**false**表示不支持。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400104](../errorcode-camera.md#7400104-会话未运行) | session is not running. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

<!--Del-->
**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function isAutoHighQualityPhotoSupported(photoOutput: camera.PhotoOutput): boolean {
  return photoOutput.isAutoHighQualityPhotoSupported();
}
```

<!--DelEnd-->

## isDeferredImageDeliveryEnabled

```TypeScript
isDeferredImageDeliveryEnabled(type: DeferredDeliveryImageType): boolean
```

检查是否已使能指定类型的分段式投递。

**起始版本：** 11

<!--Device-PhotoOutput-isDeferredImageDeliveryEnabled(type: DeferredDeliveryImageType): boolean--><!--Device-PhotoOutput-isDeferredImageDeliveryEnabled(type: DeferredDeliveryImageType): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [DeferredDeliveryImageType](arkts-camera-camera-deferreddeliveryimagetype-e-sys.md) | 是 | 分段式投递的图像类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示是否已使能分段式投递。**true**表示已使能，**false**表示未使能。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400104](../errorcode-camera.md#7400104-会话未运行) | Session not running. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

<!--Del-->
**示例**

```TypeScript
function isDeferredImageDeliveryEnabled(photoOutput: camera.PhotoOutput, type: camera.DeferredDeliveryImageType): boolean {
  let res: boolean = false;
  res = photoOutput.isDeferredImageDeliveryEnabled(type);
  return res;
}
```

<!--DelEnd-->

## isDeferredImageDeliverySupported

```TypeScript
isDeferredImageDeliverySupported(type: DeferredDeliveryImageType): boolean
```

检查是否支持指定类型的分段式投递。

**起始版本：** 11

<!--Device-PhotoOutput-isDeferredImageDeliverySupported(type: DeferredDeliveryImageType): boolean--><!--Device-PhotoOutput-isDeferredImageDeliverySupported(type: DeferredDeliveryImageType): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [DeferredDeliveryImageType](arkts-camera-camera-deferreddeliveryimagetype-e-sys.md) | 是 | 分段式投递的图像类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示是否支持分段式投递。**true**表示支持，**false**表示不支持。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400104](../errorcode-camera.md#7400104-会话未运行) | Session not running. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

<!--Del-->
**示例**

```TypeScript
function isDeferredImageDeliverySupported(photoOutput: camera.PhotoOutput, type: camera.DeferredDeliveryImageType): boolean {
  let res: boolean = false;
  res = photoOutput.isDeferredImageDeliverySupported(type);
  return res;
}
```

<!--DelEnd-->

## isDepthDataDeliverySupported

```TypeScript
isDepthDataDeliverySupported(): boolean
```

检查是否支持深度数据投递。

**起始版本：** 13

<!--Device-PhotoOutput-isDepthDataDeliverySupported(): boolean--><!--Device-PhotoOutput-isDepthDataDeliverySupported(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示是否已使能该图像投递类型。**true**表示已使能。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400104](../errorcode-camera.md#7400104-会话未运行) | Session not running. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

## isOfflineSupported

```TypeScript
isOfflineSupported(): boolean
```

检查是否支持离线处理。

**起始版本：** 18

<!--Device-PhotoOutput-isOfflineSupported(): boolean--><!--Device-PhotoOutput-isOfflineSupported(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示是否支持该离线处理类型。**true**表示支持。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

## isOriginalImageGenerationSupported

```TypeScript
isOriginalImageGenerationSupported(): boolean
```

检查是否支持原图生成。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PhotoOutput-isOriginalImageGenerationSupported(): boolean--><!--Device-PhotoOutput-isOriginalImageGenerationSupported(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示是否支持原图生成。**true**表示支持。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

## isQuickThumbnailSupported

```TypeScript
isQuickThumbnailSupported(): boolean
```

检查是否支持快速缩略图功能。该接口在调用 [addOutput](arkts-camera-camera-session-i.md#addoutput) 和[addInput](arkts-camera-camera-session-i.md#addinput) 之后、[commitConfig](arkts-camera-camera-session-i.md#commitconfig) 之前调用生效。

**起始版本：** 10

<!--Device-PhotoOutput-isQuickThumbnailSupported(): boolean--><!--Device-PhotoOutput-isQuickThumbnailSupported(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示是否支持快速缩略图功能。**true**表示支持，**false**表示不支持。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400104](../errorcode-camera.md#7400104-会话未运行) | session is not running. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application.<br>**适用版本：** 12+ |

<!--Del-->
**示例**

```TypeScript
import { common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function isQuickThumbnailSupported(context: common.BaseContext, mode: camera.SceneMode, photoProfile: camera.Profile): Promise<boolean> {
  let cameraManager: camera.CameraManager = camera.getCameraManager(context);
  let cameras: Array<camera.CameraDevice> = cameraManager.getSupportedCameras();
  // 创建CaptureSession实例。
  let session: camera.Session = cameraManager.createSession(mode);
  // 开始配置会话。
  session.beginConfig();
  // 把CameraInput加入到会话。
  if (cameras.length <= 0) {
    console.info('Get supported cameras is null or [].');
    return false;
  }
  let cameraInput: camera.CameraInput = cameraManager.createCameraInput(cameras[0]);
  await cameraInput.open();
  session.addInput(cameraInput);
  // 把photoOutput加入到会话。
  let photoOutput: camera.PhotoOutput = cameraManager.createPhotoOutput(photoProfile);
  try {
    session.addOutput(photoOutput);
  } catch (error) {
    let err = error as BusinessError;
    console.error(`AddOutput called failed. error code: ${err.code}`);
    return false;
  }
  let isSupported: boolean = photoOutput.isQuickThumbnailSupported();
  return isSupported;
}
```

<!--DelEnd-->

## isRawDeliverySupported

```TypeScript
isRawDeliverySupported(): boolean
```

检查是否支持 Raw 图像投递。

**起始版本：** 13

<!--Device-PhotoOutput-isRawDeliverySupported(): boolean--><!--Device-PhotoOutput-isRawDeliverySupported(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示是否支持该图像投递类型。**true**表示支持，**false**表示不支持。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400104](../errorcode-camera.md#7400104-会话未运行) | Session not running. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

## off('deferredPhotoProxyAvailable')

```TypeScript
off(type: 'deferredPhotoProxyAvailable', callback?: AsyncCallback<DeferredPhotoProxy>): void
```

取消订阅缩略图代理可用事件。

**起始版本：** 11

<!--Device-PhotoOutput-off(type: 'deferredPhotoProxyAvailable', callback?: AsyncCallback<DeferredPhotoProxy>): void--><!--Device-PhotoOutput-off(type: 'deferredPhotoProxyAvailable', callback?: AsyncCallback<DeferredPhotoProxy>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'deferredPhotoProxyAvailable' | 是 | 事件类型。取值固定为**'deferredPhotoProxyAvailable'**。该事件可在创建 photoOutput 实例时监听。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[DeferredPhotoProxy](arkts-camera-camera-deferredphotoproxy-i-sys.md)&gt; | 否 | 用于返回结果的回调。该参数为可选参数。若指定该参数，则取消对指定事件**on('deferredPhotoProxyAvailable')** 中指定回调的订阅。（回调对象不能是匿名函数。） |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |

<!--Del-->
**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';

function callback(err: BusinessError, proxyObj: camera.DeferredPhotoProxy): void {
  if (err !== undefined && err.code !== 0) {
    console.error(`Callback Error, errorCode: ${err.code}`);
    return;
  }
  proxyObj.getThumbnail().then((thumbnail: image.PixelMap) => {
    AppStorage.setOrCreate('proxyThumbnail', thumbnail);
  });
}

function unRegisterPhotoOutputDeferredPhotoProxyAvailable(photoOutput: camera.PhotoOutput): void {
  photoOutput.off('deferredPhotoProxyAvailable', callback);
}
```

<!--DelEnd-->

## off('quickThumbnail')

```TypeScript
off(type: 'quickThumbnail', callback?: AsyncCallback<image.PixelMap>): void
```

取消订阅快速缩略图输出事件。

**起始版本：** 10

<!--Device-PhotoOutput-off(type: 'quickThumbnail', callback?: AsyncCallback<image.PixelMap>): void--><!--Device-PhotoOutput-off(type: 'quickThumbnail', callback?: AsyncCallback<image.PixelMap>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'quickThumbnail' | 是 | 事件类型。取值固定为**'quickThumbnail'**。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)&gt; | 否 | 用于返回结果的回调。该参数为可选参数。若指定该参数，则取消对指定事件 **on('quickThumbnail')**中指定回调的订阅。（回调对象不能是匿名函数。） |

<!--Del-->
**示例**

```TypeScript
function unregisterQuickThumbnail(photoOutput: camera.PhotoOutput): void {
  photoOutput.off('quickThumbnail');
}
```

<!--DelEnd-->

## off('offlineDeliveryFinished')

```TypeScript
off(type: 'offlineDeliveryFinished', callback?: AsyncCallback<void>): void
```

取消订阅离线投递完成事件。仅在调用 enableOffline() 后有效。

**起始版本：** 18

<!--Device-PhotoOutput-off(type: 'offlineDeliveryFinished', callback?: AsyncCallback<void>): void--><!--Device-PhotoOutput-off(type: 'offlineDeliveryFinished', callback?: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'offlineDeliveryFinished' | 是 | 事件类型。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 否 | 用于获取离线投递完成事件的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |

## on('deferredPhotoProxyAvailable')

```TypeScript
on(type: 'deferredPhotoProxyAvailable', callback: AsyncCallback<DeferredPhotoProxy>): void
```

订阅缩略图代理可用事件。该接口使用异步回调返回结果。

**起始版本：** 11

<!--Device-PhotoOutput-on(type: 'deferredPhotoProxyAvailable', callback: AsyncCallback<DeferredPhotoProxy>): void--><!--Device-PhotoOutput-on(type: 'deferredPhotoProxyAvailable', callback: AsyncCallback<DeferredPhotoProxy>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'deferredPhotoProxyAvailable' | 是 | 事件类型。取值固定为**'deferredPhotoProxyAvailable'**。该事件可在创建 photoOutput 实例时监听。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[DeferredPhotoProxy](arkts-camera-camera-deferredphotoproxy-i-sys.md)&gt; | 是 | 用于返回缩略图代理的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |

<!--Del-->
**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';

function callback(err: BusinessError, proxyObj: camera.DeferredPhotoProxy): void {
  if (err !== undefined && err.code !== 0) {
    console.error(`Callback Error, errorCode: ${err.code}`);
    return;
  }
  proxyObj.getThumbnail().then((thumbnail: image.PixelMap) => {
    AppStorage.setOrCreate('proxyThumbnail', thumbnail);
  });
}

function registerPhotoOutputDeferredPhotoProxyAvailable(photoOutput: camera.PhotoOutput): void {
  photoOutput.on('deferredPhotoProxyAvailable', callback);
}
```

<!--DelEnd-->

## on('quickThumbnail')

```TypeScript
on(type: 'quickThumbnail', callback: AsyncCallback<image.PixelMap>): void
```

订阅快速缩略图输出事件。该接口使用异步回调返回结果。调用 **enableQuickThumbnail(true)** 后监听生效。

**起始版本：** 10

<!--Device-PhotoOutput-on(type: 'quickThumbnail', callback: AsyncCallback<image.PixelMap>): void--><!--Device-PhotoOutput-on(type: 'quickThumbnail', callback: AsyncCallback<image.PixelMap>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'quickThumbnail' | 是 | 事件类型。取值固定为**'quickThumbnail'**。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)&gt; | 是 | 返回 PixelMap 实例的回调。 |

<!--Del-->
**示例**

```TypeScript
import { common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';
import { camera } from '@kit.CameraKit';

function callback(err: BusinessError, pixelMap: image.PixelMap): void {
  if (err || pixelMap === undefined) {
      console.error('photoOutput on thumbnail failed');
      return;
  }
  // 显示或保存pixelMap。
  // 执行操作。
}

async function registerQuickThumbnail(context: common.BaseContext, mode: camera.SceneMode, photoProfile: camera.Profile): Promise<void> {
  let cameraManager: camera.CameraManager = camera.getCameraManager(context);
  let cameras: Array<camera.CameraDevice> = cameraManager.getSupportedCameras();
  // 创建CaptureSession实例。
  let session: camera.Session = cameraManager.createSession(mode);
  // 开始配置会话。
  session.beginConfig();
  // 把CameraInput加入到会话。
  let cameraInput: camera.CameraInput = cameraManager.createCameraInput(cameras[0]);
  await cameraInput.open();
  session.addInput(cameraInput);
  // 把PhotoOutPut加入到会话。
  let photoOutput: camera.PhotoOutput = cameraManager.createPhotoOutput(photoProfile);
  session.addOutput(photoOutput);
  let isSupported: boolean = photoOutput.isQuickThumbnailSupported();
  if (!isSupported) {
    console.info('Quick Thumbnail is not supported to be turned on.');
    return;
  }
  try {
    photoOutput.enableQuickThumbnail(true);
  } catch (error) {
    let err = error as BusinessError;
    console.error(`The enableQuickThumbnail call failed. error code: ${err.code}`);
  }

  photoOutput.on('quickThumbnail', callback);
}
```

<!--DelEnd-->

## on('offlineDeliveryFinished')

```TypeScript
on(type: 'offlineDeliveryFinished', callback: AsyncCallback<void>): void
```

订阅离线投递完成事件。仅在调用 enableOffline() 后有效。

**起始版本：** 18

<!--Device-PhotoOutput-on(type: 'offlineDeliveryFinished', callback: AsyncCallback<void>): void--><!--Device-PhotoOutput-on(type: 'offlineDeliveryFinished', callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'offlineDeliveryFinished' | 是 | 事件类型。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 用于获取离线投递完成事件的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |

## setEditData

```TypeScript
setEditData(editData: string): void
```

设置编辑数据。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PhotoOutput-setEditData(editData: string): void--><!--Device-PhotoOutput-setEditData(editData: string): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| editData | string | 是 | 编辑数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |
