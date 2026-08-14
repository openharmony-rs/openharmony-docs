# PhotoOutput

拍照会话中使用的输出信息，继承[CameraOutput](arkts-camera-camera-cameraoutput-i.md#CameraOutput)。

**继承/实现关系：** PhotoOutput extends [CameraOutput](arkts-camera-camera-cameraoutput-i.md#CameraOutput)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-camera-interface PhotoOutput--><!--Device-camera-interface PhotoOutput-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## burstCapture

```TypeScript
burstCapture(setting: PhotoCaptureSetting): Promise<void>
```

Starts the burst mode, in which users can capture a series of photos in quick succession. This API is generally used in photo mode. After the burst mode starts, the bottom layer continues displaying photos. You can call [confirmCapture](#confirmCapture) to cancel the burst mode. This API uses a promise to return the result.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-PhotoOutput-burstCapture(setting: PhotoCaptureSetting): Promise<void>--><!--Device-PhotoOutput-burstCapture(setting: PhotoCaptureSetting): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| setting | [PhotoCaptureSetting](arkts-camera-camera-photocapturesetting-i.md) | 是 | Shooting parameters. The input of **undefined** is processed as if no parameters were passed. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400104](../errorcode-camera.md#7400104-会话未运行) | Session not running. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## 示例

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

## confirmCapture

```TypeScript
confirmCapture(): void
```

Confirms photo capture. This API is generally used in night photo mode when users need to stop the exposure countdown and take a photo in advance. This API is used to end the burst mode, which is started by calling [burstCapture](#burstCapture).

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-PhotoOutput-confirmCapture(): void--><!--Device-PhotoOutput-confirmCapture(): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400104](../errorcode-camera.md#7400104-会话未运行) | Session not running. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## 示例

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

## deferImageDelivery

```TypeScript
deferImageDelivery(type: DeferredDeliveryImageType): void
```

Enables deferred delivery of a certain type.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-PhotoOutput-deferImageDelivery(type: DeferredDeliveryImageType): void--><!--Device-PhotoOutput-deferImageDelivery(type: DeferredDeliveryImageType): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [DeferredDeliveryImageType](arkts-camera-camera-deferreddeliveryimagetype-e-sys.md) | 是 | Deferred delivery image type. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400104](../errorcode-camera.md#7400104-会话未运行) | Session not running. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## 示例

```TypeScript
function deferImageDelivery(photoOutput: camera.PhotoOutput, type: camera.DeferredDeliveryImageType): void {
  photoOutput.deferImageDelivery(type);
}
```

## enableAutoCloudImageEnhancement

```TypeScript
enableAutoCloudImageEnhancement(enabled: boolean): void
```

Enable auto cloud image enhancement

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-PhotoOutput-enableAutoCloudImageEnhancement(enabled: boolean): void--><!--Device-PhotoOutput-enableAutoCloudImageEnhancement(enabled: boolean): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | Target state for auto cloud image enhancement. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## enableAutoHighQualityPhoto

```TypeScript
enableAutoHighQualityPhoto(enabled: boolean): void
```

Enables automatic high quality for photos. Before using this API, call [isAutoHighQualityPhotoSupported](#isAutoHighQualityPhotoSupported) to check whether automatic high quality is supported.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-PhotoOutput-enableAutoHighQualityPhoto(enabled: boolean): void--><!--Device-PhotoOutput-enableAutoHighQualityPhoto(enabled: boolean): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | Whether to enable or disable automatic high quality for photos. **true** to enable, **false** otherwise. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400104](../errorcode-camera.md#7400104-会话未运行) | session is not running. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function enableAutoHighQualityPhoto(photoOutput: camera.PhotoOutput): void {
  return photoOutput.enableAutoHighQualityPhoto(true);
}
```

## enableDepthDataDelivery

```TypeScript
enableDepthDataDelivery(enabled: boolean): void
```

Enable depth data delivery.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-PhotoOutput-enableDepthDataDelivery(enabled: boolean): void--><!--Device-PhotoOutput-enableDepthDataDelivery(enabled: boolean): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | Target state for depth data delivery. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400104](../errorcode-camera.md#7400104-会话未运行) | Session not running. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## enableOffline

```TypeScript
enableOffline(): void
```

Enable offline processing.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-PhotoOutput-enableOffline(): void--><!--Device-PhotoOutput-enableOffline(): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400104](../errorcode-camera.md#7400104-会话未运行) | session is not running. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## enableOriginalImageGeneration

```TypeScript
enableOriginalImageGeneration(enabled: boolean): void
```

Enable original image generation.

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PhotoOutput-enableOriginalImageGeneration(enabled: boolean): void--><!--Device-PhotoOutput-enableOriginalImageGeneration(enabled: boolean): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | enable original image generation if TRUE. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## enableQuickThumbnail

```TypeScript
enableQuickThumbnail(enabled: boolean): void
```

Enables or disables the quick thumbnail feature. This API takes effect after [addOutput](arkts-camera-camera-session-i.md#addOutput) and [addInput](arkts-camera-camera-session-i.md#addInput) and before [commitConfig](arkts-camera-camera-session-i.md#commitConfig).

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-PhotoOutput-enableQuickThumbnail(enabled: boolean): void--><!--Device-PhotoOutput-enableQuickThumbnail(enabled: boolean): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | Whether to enable the quick thumbnail feature. **true** to enable, **false** otherwise. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect.<br>**适用版本：** 12+ |
| [7400104](../errorcode-camera.md#7400104-会话未运行) | session is not running. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error.<br>**适用版本：** 12+ |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application.<br>**适用版本：** 12+ |

## 示例

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

## enableRawDelivery

```TypeScript
enableRawDelivery(enabled: boolean): void
```

Enable raw image image delivery.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-PhotoOutput-enableRawDelivery(enabled: boolean): void--><!--Device-PhotoOutput-enableRawDelivery(enabled: boolean): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | Target state for raw image delivery. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400104](../errorcode-camera.md#7400104-会话未运行) | Session not running. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## isAutoCloudImageEnhancementSupported

```TypeScript
isAutoCloudImageEnhancementSupported(): boolean
```

Confirm if the auto cloud image enhancement is supported.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-PhotoOutput-isAutoCloudImageEnhancementSupported(): boolean--><!--Device-PhotoOutput-isAutoCloudImageEnhancementSupported(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | TRUE if the auto cloud image enhancement is supported. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## isAutoHighQualityPhotoSupported

```TypeScript
isAutoHighQualityPhotoSupported(): boolean
```

Checks whether automatic high quality is supported for photos.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-PhotoOutput-isAutoHighQualityPhotoSupported(): boolean--><!--Device-PhotoOutput-isAutoHighQualityPhotoSupported(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Check result for whether automatic high quality is supported. **true** if supported, **false** otherwise. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400104](../errorcode-camera.md#7400104-会话未运行) | session is not running. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function isAutoHighQualityPhotoSupported(photoOutput: camera.PhotoOutput): boolean {
  return photoOutput.isAutoHighQualityPhotoSupported();
}
```

## isDeferredImageDeliveryEnabled

```TypeScript
isDeferredImageDeliveryEnabled(type: DeferredDeliveryImageType): boolean
```

Checks whether deferred delivery of a certain type is enabled.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-PhotoOutput-isDeferredImageDeliveryEnabled(type: DeferredDeliveryImageType): boolean--><!--Device-PhotoOutput-isDeferredImageDeliveryEnabled(type: DeferredDeliveryImageType): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [DeferredDeliveryImageType](arkts-camera-camera-deferreddeliveryimagetype-e-sys.md) | 是 | Deferred delivery image type. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Check result for whether deferred delivery is enabled. **true** if enabled, **false** otherwise. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400104](../errorcode-camera.md#7400104-会话未运行) | Session not running. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## 示例

```TypeScript
function isDeferredImageDeliveryEnabled(photoOutput: camera.PhotoOutput, type: camera.DeferredDeliveryImageType): boolean {
  let res: boolean = false;
  res = photoOutput.isDeferredImageDeliveryEnabled(type);
  return res;
}
```

## isDeferredImageDeliverySupported

```TypeScript
isDeferredImageDeliverySupported(type: DeferredDeliveryImageType): boolean
```

Checks whether deferred delivery of a certain type is supported.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-PhotoOutput-isDeferredImageDeliverySupported(type: DeferredDeliveryImageType): boolean--><!--Device-PhotoOutput-isDeferredImageDeliverySupported(type: DeferredDeliveryImageType): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [DeferredDeliveryImageType](arkts-camera-camera-deferreddeliveryimagetype-e-sys.md) | 是 | Deferred delivery image type. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Check result for the support of deferred delivery. **true** if supported, **false** otherwise. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400104](../errorcode-camera.md#7400104-会话未运行) | Session not running. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## 示例

```TypeScript
function isDeferredImageDeliverySupported(photoOutput: camera.PhotoOutput, type: camera.DeferredDeliveryImageType): boolean {
  let res: boolean = false;
  res = photoOutput.isDeferredImageDeliverySupported(type);
  return res;
}
```

## isDepthDataDeliverySupported

```TypeScript
isDepthDataDeliverySupported(): boolean
```

Check if the depth data delivery is supported.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-PhotoOutput-isDepthDataDeliverySupported(): boolean--><!--Device-PhotoOutput-isDepthDataDeliverySupported(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | TRUE if the type of delivery image is enabled. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400104](../errorcode-camera.md#7400104-会话未运行) | Session not running. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## isOfflineSupported

```TypeScript
isOfflineSupported(): boolean
```

Confirm if offline processing is supported.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-PhotoOutput-isOfflineSupported(): boolean--><!--Device-PhotoOutput-isOfflineSupported(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | TRUE if the type of offline is supported. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## isOriginalImageGenerationSupported

```TypeScript
isOriginalImageGenerationSupported(): boolean
```

Confirm if original image generation supported.

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PhotoOutput-isOriginalImageGenerationSupported(): boolean--><!--Device-PhotoOutput-isOriginalImageGenerationSupported(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | TRUE if the original image generation is supported. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## isQuickThumbnailSupported

```TypeScript
isQuickThumbnailSupported(): boolean
```

Checks whether the quick thumbnail feature is supported. This API takes effect after [addOutput](arkts-camera-camera-session-i.md#addOutput) and [addInput](arkts-camera-camera-session-i.md#addInput) and before [commitConfig](arkts-camera-camera-session-i.md#commitConfig).

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-PhotoOutput-isQuickThumbnailSupported(): boolean--><!--Device-PhotoOutput-isQuickThumbnailSupported(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Check result for the support of the quick thumbnail feature. **true** if supported, **false** otherwise. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400104](../errorcode-camera.md#7400104-会话未运行) | session is not running. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application.<br>**适用版本：** 12+ |

## 示例

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

## isRawDeliverySupported

```TypeScript
isRawDeliverySupported(): boolean
```

Confirm if the raw image delivery is supported

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-PhotoOutput-isRawDeliverySupported(): boolean--><!--Device-PhotoOutput-isRawDeliverySupported(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | TRUE if the type of delivery image is support. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400104](../errorcode-camera.md#7400104-会话未运行) | Session not running. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## offDeferredPhotoProxyAvailable

```TypeScript
offDeferredPhotoProxyAvailable(callback?: AsyncCallback<DeferredPhotoProxy>): void
```

Unsubscribes deferred photo proxy available event callback.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-PhotoOutput-offDeferredPhotoProxyAvailable(callback?: AsyncCallback<DeferredPhotoProxy>): void--><!--Device-PhotoOutput-offDeferredPhotoProxyAvailable(callback?: AsyncCallback<DeferredPhotoProxy>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[DeferredPhotoProxy](arkts-camera-camera-deferredphotoproxy-i-sys.md)&gt; | 否 | Callback used to get the DeferredPhotoProxy. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## offOfflineDeliveryFinished

```TypeScript
offOfflineDeliveryFinished(callback?: AsyncCallback<void>): void
```

Unsubscribes offline Delivery finished events. This method is valid only after enableOffline() is called.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-PhotoOutput-offOfflineDeliveryFinished(callback?: AsyncCallback<void>): void--><!--Device-PhotoOutput-offOfflineDeliveryFinished(callback?: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 否 | Callback used to get offline Delivery finished events. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## offQuickThumbnail

```TypeScript
offQuickThumbnail(callback?: AsyncCallback<image.PixelMap>): void
```

Unsubscribes from camera thumbnail events. This method is valid only after enableQuickThumbnail(true) is called.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-PhotoOutput-offQuickThumbnail(callback?: AsyncCallback<image.PixelMap>): void--><!--Device-PhotoOutput-offQuickThumbnail(callback?: AsyncCallback<image.PixelMap>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;image.PixelMap&gt; | 否 | Callback used to get the quick thumbnail. |

## off_deferredPhotoProxyAvailable

```TypeScript
off(type: 'deferredPhotoProxyAvailable', callback?: AsyncCallback<DeferredPhotoProxy>): void
```

Unsubscribes from events indicating available thumbnail proxies.

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

<!--Device-PhotoOutput-off(type: 'deferredPhotoProxyAvailable', callback?: AsyncCallback<DeferredPhotoProxy>): void--><!--Device-PhotoOutput-off(type: 'deferredPhotoProxyAvailable', callback?: AsyncCallback<DeferredPhotoProxy>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'deferredPhotoProxyAvailable' | 是 | Event type. The value is fixed at **'deferredPhotoProxyAvailable'**. The event can be listened for when a photoOutput instance is created. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[DeferredPhotoProxy](arkts-camera-camera-deferredphotoproxy-i-sys.md)&gt; | 否 | Callback used to return the result. This parameter is optional. If this parameter is specified, the subscription to the specified event **on('deferredPhotoProxyAvailable')** with the specified callback is canceled. (The callback object cannot be an anonymous function.) |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## 示例

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

## off_offlineDeliveryFinished

```TypeScript
off(type: 'offlineDeliveryFinished', callback?: AsyncCallback<void>): void
```

Unsubscribes offline Delivery finished events. This method is valid only after enableOffline() is called.

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

<!--Device-PhotoOutput-off(type: 'offlineDeliveryFinished', callback?: AsyncCallback<void>): void--><!--Device-PhotoOutput-off(type: 'offlineDeliveryFinished', callback?: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'offlineDeliveryFinished' | 是 | Event type. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 否 | Callback used to get offline Delivery finished events. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## off_quickThumbnail

```TypeScript
off(type: 'quickThumbnail', callback?: AsyncCallback<image.PixelMap>): void
```

Unsubscribes from quick thumbnail output events.

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

<!--Device-PhotoOutput-off(type: 'quickThumbnail', callback?: AsyncCallback<image.PixelMap>): void--><!--Device-PhotoOutput-off(type: 'quickThumbnail', callback?: AsyncCallback<image.PixelMap>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'quickThumbnail' | 是 | Event type. The value is fixed at **'quickThumbnail'**. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;image.PixelMap&gt; | 否 | Callback used to return the result. This parameter is optional. If this parameter is specified, the subscription to the specified event **on('quickThumbnail')** with the specified callback is canceled. (The callback object cannot be an anonymous function.) |

## 示例

```TypeScript
function unregisterQuickThumbnail(photoOutput: camera.PhotoOutput): void {
  photoOutput.off('quickThumbnail');
}
```

## onDeferredPhotoProxyAvailable

```TypeScript
onDeferredPhotoProxyAvailable(callback: AsyncCallback<DeferredPhotoProxy>): void
```

Subscribes deferred photo proxy available event callback.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-PhotoOutput-onDeferredPhotoProxyAvailable(callback: AsyncCallback<DeferredPhotoProxy>): void--><!--Device-PhotoOutput-onDeferredPhotoProxyAvailable(callback: AsyncCallback<DeferredPhotoProxy>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[DeferredPhotoProxy](arkts-camera-camera-deferredphotoproxy-i-sys.md)&gt; | 是 | Callback used to get the DeferredPhotoProxy. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## onOfflineDeliveryFinished

```TypeScript
onOfflineDeliveryFinished(callback: AsyncCallback<void>): void
```

Subscribes offline Delivery finished events. This method is valid only after enableOffline() is called.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-PhotoOutput-onOfflineDeliveryFinished(callback: AsyncCallback<void>): void--><!--Device-PhotoOutput-onOfflineDeliveryFinished(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | Callback used to get offline Delivery finished events. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## onQuickThumbnail

```TypeScript
onQuickThumbnail(callback: AsyncCallback<image.PixelMap>): void
```

Subscribes to camera thumbnail events. This method is valid only after enableQuickThumbnail(true) is called.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-PhotoOutput-onQuickThumbnail(callback: AsyncCallback<image.PixelMap>): void--><!--Device-PhotoOutput-onQuickThumbnail(callback: AsyncCallback<image.PixelMap>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;image.PixelMap&gt; | 是 | Callback used to get the quick thumbnail. |

## on_deferredPhotoProxyAvailable

```TypeScript
on(type: 'deferredPhotoProxyAvailable', callback: AsyncCallback<DeferredPhotoProxy>): void
```

Subscribes to events indicating available thumbnail proxies. This API uses an asynchronous callback to return the result.

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

<!--Device-PhotoOutput-on(type: 'deferredPhotoProxyAvailable', callback: AsyncCallback<DeferredPhotoProxy>): void--><!--Device-PhotoOutput-on(type: 'deferredPhotoProxyAvailable', callback: AsyncCallback<DeferredPhotoProxy>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'deferredPhotoProxyAvailable' | 是 | Event type. The value is fixed at **'deferredPhotoProxyAvailable'**. The event can be listened for when a photoOutput instance is created. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[DeferredPhotoProxy](arkts-camera-camera-deferredphotoproxy-i-sys.md)&gt; | 是 | Callback used to return the thumbnail proxy. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## 示例

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

## on_offlineDeliveryFinished

```TypeScript
on(type: 'offlineDeliveryFinished', callback: AsyncCallback<void>): void
```

Subscribes offline Delivery finished events. This method is valid only after enableOffline() is called.

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

<!--Device-PhotoOutput-on(type: 'offlineDeliveryFinished', callback: AsyncCallback<void>): void--><!--Device-PhotoOutput-on(type: 'offlineDeliveryFinished', callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'offlineDeliveryFinished' | 是 | Event type. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | Callback used to get offline Delivery finished events. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## on_quickThumbnail

```TypeScript
on(type: 'quickThumbnail', callback: AsyncCallback<image.PixelMap>): void
```

Subscribes to quick thumbnail output events. This API uses an asynchronous callback to return the result. The listening takes effect after **enableQuickThumbnail(true)** is called.

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

<!--Device-PhotoOutput-on(type: 'quickThumbnail', callback: AsyncCallback<image.PixelMap>): void--><!--Device-PhotoOutput-on(type: 'quickThumbnail', callback: AsyncCallback<image.PixelMap>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'quickThumbnail' | 是 | Event type. The value is fixed at **'quickThumbnail'**. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;image.PixelMap&gt; | 是 | Callback that returns a PixelMap instance. |

## 示例

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

## setEditData

```TypeScript
setEditData(editData: string): void
```

Set edit data.

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PhotoOutput-setEditData(editData: string): void--><!--Device-PhotoOutput-setEditData(editData: string): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| editData | string | 是 | The edit data. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

