# PhotoOutput

拍照会话中使用的输出信息，继承[CameraOutput](arkts-camera-camera-cameraoutput-i.md)。

**继承/实现关系：** PhotoOutput extends [CameraOutput](arkts-camera-camera-cameraoutput-i.md)

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.Camera.Core

## 导入模块

```TypeScript
```

## capture

```TypeScript
capture(callback: AsyncCallback<void>): void
```

以默认设置触发一次拍照，通过注册回调函数获取结果。使用callback异步回调。

**起始版本：** 10

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当以默认设置触发拍照成功，err为undefined，否则为错误对象。错误码类型 [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md)。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400104](../errorcode-camera.md#7400104-会话未运行) | Session not running. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function capture(photoOutput: camera.PhotoOutput): void {
  photoOutput.capture((err: BusinessError) => {
    if (err) {
      console.error(`Failed to capture the photo, error code: ${err.code}.`);
      return;
    }
    console.info('Callback invoked to indicate the photo capture request success.');
  });
}
```

## capture

```TypeScript
capture(): Promise<void>
```

以默认设置触发一次拍照。使用Promise异步回调。

**起始版本：** 10

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400104](../errorcode-camera.md#7400104-会话未运行) | Session not running. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function capture(photoOutput: camera.PhotoOutput): void {
  photoOutput.capture().then(() => {
    console.info('Promise returned to indicate that photo capture request success.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to photo output capture, error code: ${error.code}.`);
  });
}
```

## capture

```TypeScript
capture(setting: PhotoCaptureSetting, callback: AsyncCallback<void>): void
```

以指定参数触发一次拍照，通过注册回调函数获取结果。使用callback异步回调。

**起始版本：** 10

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| setting | [PhotoCaptureSetting](arkts-camera-camera-photocapturesetting-i.md) | 是 | 拍照设置，传入undefined类型数据按默认设置触发一次拍照处理。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数，用于获取结果。接口调用失败会返回相应错误码，错误码类型 [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md)。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400104](../errorcode-camera.md#7400104-会话未运行) | Session not running. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function capture(photoOutput: camera.PhotoOutput): void {
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
  photoOutput.capture(settings, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to capture the photo, error code: ${err.code}.`);
      return;
    }
    console.info('Callback invoked to indicate the photo capture request success.');
  });
}
```

## capture

```TypeScript
capture(setting: PhotoCaptureSetting): Promise<void>
```

以指定参数触发一次拍照。使用Promise异步回调。

**起始版本：** 10

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| setting | [PhotoCaptureSetting](arkts-camera-camera-photocapturesetting-i.md) | 是 | 拍照设置，传入undefined类型数据按默认设置触发一次拍照处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400104](../errorcode-camera.md#7400104-会话未运行) | Session not running. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function capture(photoOutput: camera.PhotoOutput): void {
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
  photoOutput.capture(settings).then(() => {
    console.info('Promise returned to indicate that photo capture request success.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to photo output capture, error code: ${error.code}.`);
  });
}
```

## enableAutoExtendedGainmapDelivery

```TypeScript
enableAutoExtendedGainmapDelivery(enabled: boolean): void
```

是否启用自动扩展增益图（Gainmap）的输出。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | 是否启用自动扩展增益图（Gainmap）的输出。true表示启用，false表示不启用。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config, only throw in session usage. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { camera } from '@kit.CameraKit';

function enableAutoExtendedGainmapDelivery(photoOutput: camera.PhotoOutput): void {
  try {
    photoOutput.enableAutoExtendedGainmapDelivery(true);
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The enableAutoExtendedGainmapDelivery call failed. error code: ${err.code}`);
  }
}
```

## enableMirror

```TypeScript
enableMirror(enabled: boolean): void
```

是否启用动态照片镜像拍照。调用该接口前，需要通过[isMovingPhotoSupported](#ismovingphotosupported)查询是否支持动态照片拍摄功能以及通过 [isMirrorSupported](#ismirrorsupported)查询是否支持镜像拍照功能。

**起始版本：** 13

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | 是否启用动态照片镜像拍照。true为开启动态照片镜像拍照，false为关闭动态照片镜像拍照。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function enableMirror(photoOutput: camera.PhotoOutput): void {
  try {
    photoOutput.enableMirror(true);
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The enableMirror call failed. error code: ${err.code}`);
  }
}
```

```TypeScript
import { camera } from '@kit.CameraKit';
import { media } from '@kit.MediaKit';
import { BusinessError } from '@kit.BasicServicesKit';

function enableMirror(videoOutput: camera.VideoOutput, mirrorMode: boolean, aVRecorder: media.AVRecorder, deviceDegree : number): void {
    try {
        videoOutput.enableMirror(mirrorMode);
        aVRecorder.updateRotation(videoOutput.getVideoRotation(deviceDegree));
    } catch (error) {
        let err = error as BusinessError;
    }
}
```

## enableMovingPhoto

```TypeScript
enableMovingPhoto(enabled: boolean): void
```

使能动态照片拍照。

**起始版本：** 12

**需要权限：** ohos.permission.MICROPHONE

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | 使能动态照片拍照。true为开启动态照片，false为关闭动态照片。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | permission denied. |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function enableMovingPhoto(photoOutput: camera.PhotoOutput): void {
  try {
    photoOutput.enableMovingPhoto(true);
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The enableMovingPhoto call failed. error code: ${err.code}`);
  }
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

## getPhotoRotation

```TypeScript
getPhotoRotation(deviceDegree?: number): ImageRotation
```

获取拍照旋转角度。  
- 设备自然方向：设备默认使用方向。例如，直板机默认使用方向为竖屏（充电口向下）。  
- 相机镜头角度：值等于相机图像顺时针旋转到设备自然方向的角度。例如，直板机后置相机传感器是横屏安装的，所以需要顺时针旋转90度到设备自然方向。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceDegree | number | 否 | 设备旋转角度，单位度，取值范围：[0, 360]。 若入参超过该范围，则取入参除以360的余数。 从API version 23开始，入参deviceDegree为可选参数，当不传入参数时，由系统获取deviceDegree进行拍照旋转角度计算。<br>**起始版本：** 23 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ImageRotation](arkts-camera-camera-imagerotation-e.md) | 返回拍照旋转角度。若接口调用失败，返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect.<br>**适用版本：** 12 - 22 |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function testGetPhotoRotation(photoOutput: camera.PhotoOutput, deviceDegree : number): camera.ImageRotation {
  let photoRotation: camera.ImageRotation = camera.ImageRotation.ROTATION_0;
  try {
    photoRotation = photoOutput.getPhotoRotation(deviceDegree);
    console.info(`Photo rotation is: ${photoRotation}`);
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The photoOutput.getPhotoRotation call failed. error code: ${err.code}`);
  }
  return photoRotation;
}

function testGetPhotoRotationWithOutParam(photoOutput: camera.PhotoOutput): camera.ImageRotation {
  let photoRotation: camera.ImageRotation = camera.ImageRotation.ROTATION_0;
  try {
    photoRotation = photoOutput.getPhotoRotation();
    console.info(`Photo rotation is: ${photoRotation}`);
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The photoOutput.testGetPhotoRotationWithOutParam call failed. error code: ${err.code}`);
  }
  return photoRotation;
}
```

## getSupportedMovingPhotoVideoCodecTypes

```TypeScript
getSupportedMovingPhotoVideoCodecTypes(): Array<VideoCodecType>
```

查询支持的动态照片短视频编码类型。

**起始版本：** 13

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[VideoCodecType](arkts-camera-camera-videocodectype-e.md)&gt; | 支持的动态照片短视频编码类型列表。若接口调用失败，返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

**示例**

```TypeScript
function getSupportedMovingPhotoVideoCodecType(photoOutput: camera.PhotoOutput): Array<camera.VideoCodecType> {
  let supportedVideoCodecTypesArray: Array<camera.VideoCodecType> = photoOutput.getSupportedMovingPhotoVideoCodecTypes();
  return supportedVideoCodecTypesArray;
}
```

## isAutoExtendedGainmapDeliverySupported

```TypeScript
isAutoExtendedGainmapDeliverySupported(): boolean
```

确认是否支持自动扩展增益图（Gainmap）的输出。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 是否支持自动扩展增益图（Gainmap）的输出。true表示支持，false表示不支持。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { camera } from '@kit.CameraKit';

function isAutoExtendedGainmapDeliverySupported(photoOutput: camera.PhotoOutput): boolean {
  let isSupported: boolean = false;
  try {
    isSupported = photoOutput.isAutoExtendedGainmapDeliverySupported();
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The isAutoExtendedGainmapDeliverySupported call failed. error code: ${err.code}`);
  }
  return isSupported;
}
```

## isMirrorSupported

```TypeScript
isMirrorSupported(): boolean
```

查询是否支持镜像拍照。

**起始版本：** 10

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回是否支持镜像拍照，true表示支持，false表示不支持。若接口调用失败，返回undefined。 |

**示例**

```TypeScript
function isMirrorSupported(photoOutput: camera.PhotoOutput): boolean {
  let isSupported: boolean = photoOutput.isMirrorSupported();
  return isSupported;
}
```

```TypeScript
function testIsMirrorSupported(videoOutput: camera.VideoOutput): boolean {
  let isSupported: boolean = videoOutput.isMirrorSupported();
  return isSupported;
}
```

## isMovingPhotoSupported

```TypeScript
isMovingPhotoSupported(): boolean
```

查询是否支持动态照片拍摄。

**起始版本：** 12

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回是否支持动态照片拍照。true表示支持，false表示不支持。若接口调用失败，返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function isMovingPhotoSupported(photoOutput: camera.PhotoOutput): boolean {
  let isSupported: boolean = false;
  try {
    isSupported = photoOutput.isMovingPhotoSupported();
  } catch (error) {
    // 失败返回错误码error.code并处理。
    let err = error as BusinessError;
    console.error(`The isMovingPhotoSupported call failed. error code: ${err.code}`);
  }
  return isSupported;
}
```

## isPhotoQualityPrioritizationSupported

```TypeScript
isPhotoQualityPrioritizationSupported(qualityPrioritization: PhotoQualityPrioritization): boolean
```

检查是否支持指定的拍照画质优先策略。

**起始版本：** 21

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| qualityPrioritization | [PhotoQualityPrioritization](arkts-camera-camera-photoqualityprioritization-e.md) | 是 | 要检查的拍照画质优先策略。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 是否支持指定的拍照画质优先策略。true表示支持，false表示不支持。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error, reconfiguring streams is needed to recover from failure. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { camera } from '@kit.CameraKit';

let photoOutput: camera.PhotoOutput;

function isPhotoQualityPrioritizationSupported(qualityPrioritization: camera.PhotoQualityPrioritization): boolean {
  let isSupported: boolean = false;
  try {
    isSupported = photoOutput.isPhotoQualityPrioritizationSupported(qualityPrioritization);
  } catch (error) {
    let err = error as BusinessError;
    console.error(`The isPhotoQualityPrioritizationSupported call failed. error code: ${err.code}`);
  }
  return isSupported;
}
```

## off('photoAvailable')

```TypeScript
off(type: 'photoAvailable', callback?: AsyncCallback<Photo>): void
```

注销监听拍照返回照片上报事件。

**起始版本：** 11

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'photoAvailable' | 是 | 监听事件，固定为'photoAvailable'，photoOutput创建成功后可监听。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[Photo](arkts-camera-camera-photo-i.md)&gt; | 否 | 回调函数，如果指定参数则取消对应callback（callback对象不可是匿名函数），否则取消所有callback。 |

## off('photoAssetAvailable')

```TypeScript
off(type: 'photoAssetAvailable', callback?: AsyncCallback<photoAccessHelper.PhotoAsset>): void
```

注销photoAsset上报。

**起始版本：** 12

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'photoAssetAvailable' | 是 | 监听事件，固定为'photoAssetAvailable'，photoOutput创建成功后可监听。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;photoAccessHelper.PhotoAsset&gt; | 否 | 需要解监听的回调方法。如果callback不为空且与此对应的监听方法一致，不为匿名方法，则解注 册该方法；如果callback为空，则解监听所有回调。 |

## off('captureStart')

```TypeScript
off(type: 'captureStart', callback?: AsyncCallback<number>): void
```

注销拍照开始的监听。

> **说明：**
> 
> 从 API version 10开始支持，从API version 11开始废弃。
> 
> 当前注册监听接口，不支持在on监听的回调方法里，调用off注销回调。

**起始版本：** 10

**废弃版本：** 11

**替代接口：** [off](#offcapturestartwithinfo)(type: 'captureStartWithInfo', callback?: AsyncCallback&lt;CaptureStartInfo&gt;)

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'captureStart' | 是 | 监听事件，固定为'captureStart'，photoOutput创建成功后可监听。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 否 | 回调函数，如果指定参数则取消对应callback（callback对象不可是匿名函数），否则取消所有callback。 |

## off('captureStartWithInfo')

```TypeScript
off(type: 'captureStartWithInfo', callback?: AsyncCallback<CaptureStartInfo>): void
```

注销监听拍照。

**起始版本：** 11

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'captureStartWithInfo' | 是 | 监听事件，固定为'captureStartWithInfo'，photoOutput创建成功后可监听。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[CaptureStartInfo](arkts-camera-camera-capturestartinfo-i.md)&gt; | 否 | 回调函数，如果指定参数则取消对应callback（callback对象不可是匿名函数），否则取消所有callback。 |

## off('frameShutter')

```TypeScript
off(type: 'frameShutter', callback?: AsyncCallback<FrameShutterInfo>): void
```

注销监听拍照帧输出捕获。

**起始版本：** 10

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'frameShutter' | 是 | 监听事件，固定为'frameShutter'，photoOutput创建成功后可监听。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[FrameShutterInfo](arkts-camera-camera-frameshutterinfo-i.md)&gt; | 否 | 回调函数，如果指定参数则取消对应callback（callback对象不可是匿名函数），否则取消所有callback。 |

## off('frameShutterEnd')

```TypeScript
off(type: 'frameShutterEnd', callback?: AsyncCallback<FrameShutterEndInfo>): void
```

注销监听拍照曝光结束捕获。

**起始版本：** 12

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'frameShutterEnd' | 是 | 监听事件，固定为'frameShutterEnd'，photoOutput创建成功后可监听。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[FrameShutterEndInfo](arkts-camera-camera-frameshutterendinfo-i.md)&gt; | 否 | 回调函数，如果指定参数则取消对应callback（callback对象不可是匿名函数），否则取消所有 callback。 |

## off('captureEnd')

```TypeScript
off(type: 'captureEnd', callback?: AsyncCallback<CaptureEndInfo>): void
```

注销监听拍照结束。

**起始版本：** 10

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'captureEnd' | 是 | 监听事件，固定为'captureEnd'，photoOutput创建成功后可监听。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[CaptureEndInfo](arkts-camera-camera-captureendinfo-i.md)&gt; | 否 | 回调函数，如果指定参数则取消对应callback（callback对象不可是匿名函数），否则取消所有callback。 |

## off('captureReady')

```TypeScript
off(type: 'captureReady', callback?: AsyncCallback<void>): void
```

注销监听可拍下一张。

**起始版本：** 12

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'captureReady' | 是 | 监听事件，固定为'captureReady'，photoOutput创建成功后可监听。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 否 | 回调函数，如果指定参数则取消对应callback（callback对象不可是匿名函数），否则取消所有callback。 |

## off('estimatedCaptureDuration')

```TypeScript
off(type: 'estimatedCaptureDuration', callback?: AsyncCallback<number>): void
```

注销监听预估的拍照时间。

**起始版本：** 12

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'estimatedCaptureDuration' | 是 | 监听事件，固定为'estimatedCaptureDuration'，photoOutput创建成功后可监听。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 否 | 回调函数，如果指定参数则取消对应callback（callback对象不可是匿名函数），否则取消所有callback。 |

## off('error')

```TypeScript
off(type: 'error', callback?: ErrorCallback): void
```

注销监听拍照输出发生错误。

**起始版本：** 10

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 监听事件，固定为'error'，photoOutput创建成功后可监听。 |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | 否 | 回调函数，如果指定参数则取消对应callback（callback对象不可是匿名函数），否则取消所有callback。 |

## offCapturePhotoAvailable

```TypeScript
offCapturePhotoAvailable(callback?: Callback<CapturePhoto>): void
```

注销监听全质量图和未压缩图。使用callback异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[CapturePhoto](arkts-camera-camera-capturephoto-i.md)&gt; | 否 | 回调函数，如果指定参数则取消对应callback，callback对象不可是匿名函数，否则取消所有callback。 |

**示例**

```TypeScript
import { camera } from '@kit.CameraKit';
import { image } from '@kit.ImageKit';

function callback(capturePhoto: camera.CapturePhoto): void {
  let picture: image.Image | image.Picture = capturePhoto.main;
}

function unRegisterCapturePhotoOutputPhotoAvailable(photoOutput: camera.PhotoOutput): void {
  photoOutput.offCapturePhotoAvailable(callback);
}
```

## on('photoAvailable')

```TypeScript
on(type: 'photoAvailable', callback: AsyncCallback<Photo>): void
```

注册监听拍照返回照片上报事件。使用callback异步回调。

> **说明：**
> 
> 当前注册监听接口，不支持在on监听的回调方法里，调用off注销回调。

**起始版本：** 11

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'photoAvailable' | 是 | 监听事件，固定为'photoAvailable'，photoOutput创建成功后可监听。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[Photo](arkts-camera-camera-photo-i.md)&gt; | 是 | 回调函数，用于监听拍照返回照片上报事件。 |

## on('photoAssetAvailable')

```TypeScript
on(type: 'photoAssetAvailable', callback: AsyncCallback<photoAccessHelper.PhotoAsset>): void
```

注册监听photoAsset上报。使用callback异步回调。

> **说明：**
> 
> 当前注册监听接口，不支持在on监听的回调方法里，调用off注销回调。

**起始版本：** 12

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'photoAssetAvailable' | 是 | 监听事件，固定为'photoAssetAvailable'，photoOutput创建成功后可监听。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;photoAccessHelper.PhotoAsset&gt; | 是 | 回调函数，用于监听photoAsset上报。 |

## on('captureStart')

```TypeScript
on(type: 'captureStart', callback: AsyncCallback<number>): void
```

监听拍照开始，通过注册回调函数获取Capture ID。使用callback异步回调。

> **说明：**
> 
> 从 API version 10开始支持，从API version 11开始废弃。
> 
> 当前注册监听接口，不支持在on监听的回调方法里，调用off注销回调。

**起始版本：** 10

**废弃版本：** 11

**替代接口：** [on](#oncapturestartwithinfo)(type: 'captureStartWithInfo', callback: AsyncCallback&lt;CaptureStartInfo&gt;)

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'captureStart' | 是 | 监听事件，固定为'captureStart'，photoOutput创建成功后可监听。每次拍照，底层开始曝光时触发该事件并返回。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 使用callback的方式获取Capture ID。 |

## on('captureStartWithInfo')

```TypeScript
on(type: 'captureStartWithInfo', callback: AsyncCallback<CaptureStartInfo>): void
```

监听拍照开始，通过注册回调函数获取[CaptureStartInfo](arkts-camera-camera-capturestartinfo-i.md)。使用callback异步回调。

> **说明：**
> 
> 当前注册监听接口，不支持在on监听的回调方法里，调用off注销回调。

**起始版本：** 11

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'captureStartWithInfo' | 是 | 监听事件，固定为'captureStartWithInfo'，photoOutput创建成功后可监听。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[CaptureStartInfo](arkts-camera-camera-capturestartinfo-i.md)&gt; | 是 | 使用callback的方式获取Capture ID。 |

## on('frameShutter')

```TypeScript
on(type: 'frameShutter', callback: AsyncCallback<FrameShutterInfo>): void
```

监听拍照帧输出捕获，通过注册回调函数获取结果。使用callback异步回调。

**起始版本：** 10

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'frameShutter' | 是 | 监听事件，固定为'frameShutter'，photoOutput创建成功后可监听。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[FrameShutterInfo](arkts-camera-camera-frameshutterinfo-i.md)&gt; | 是 | 回调函数，用于获取相关信息。该回调返回意味着可以再次下发拍照请求。 |

## on('frameShutterEnd')

```TypeScript
on(type: 'frameShutterEnd', callback: AsyncCallback<FrameShutterEndInfo>): void
```

监听拍照曝光结束捕获，通过注册回调函数获取结果。使用callback异步回调。

> **说明：**
> 
> 当前注册监听接口，不支持在on监听的回调方法里，调用off注销回调。

**起始版本：** 12

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'frameShutterEnd' | 是 | 监听事件，固定为'frameShutterEnd'，photoOutput创建成功后可监听。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[FrameShutterEndInfo](arkts-camera-camera-frameshutterendinfo-i.md)&gt; | 是 | 回调函数，用于获取相关信息。该回调返回表示拍照曝光结束。 |

## on('captureEnd')

```TypeScript
on(type: 'captureEnd', callback: AsyncCallback<CaptureEndInfo>): void
```

监听拍照结束，通过注册回调函数获取结果。使用callback异步回调。

> **说明：**
> 
> 当前注册监听接口，不支持在on监听的回调方法里，调用off注销回调。

**起始版本：** 10

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'captureEnd' | 是 | 监听事件，固定为'captureEnd'。photoOutput创建成功后可监听。拍照完全结束可触发该事件发生并返回相应信息。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[CaptureEndInfo](arkts-camera-camera-captureendinfo-i.md)&gt; | 是 | 回调函数，用于获取相关信息。 |

## on('captureReady')

```TypeScript
on(type: 'captureReady', callback: AsyncCallback<void>): void
```

监听可拍下一张，通过注册回调函数获取结果。使用callback异步回调。

> **说明：**
> 
> 当前注册监听接口，不支持在on监听的回调方法里，调用off注销回调。

**起始版本：** 12

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'captureReady' | 是 | 监听事件，固定为'captureReady'，photoOutput创建成功后可监听。当下一张可拍时可触发该事件发生并返回相应信息。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数，用于获取相关信息。 |

## on('estimatedCaptureDuration')

```TypeScript
on(type: 'estimatedCaptureDuration', callback: AsyncCallback<number>): void
```

监听预估的拍照时间，通过注册回调函数获取结果。使用callback异步回调。

> **说明：**
> 
> 当前注册监听接口，不支持在on监听的回调方法里，调用off注销回调。

**起始版本：** 12

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'estimatedCaptureDuration' | 是 | 监听事件，固定为'estimatedCaptureDuration'，photoOutput创建成功后可监听。拍照完全结束可触发该事件发 生并返回相应信息。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数，用于获取预估的单次拍照底层出sensor采集帧时间，单位：毫秒。如果上报-1，代表没有预估时间。 |

## on('error')

```TypeScript
on(type: 'error', callback: ErrorCallback): void
```

监听拍照输出发生错误，通过注册回调函数获取结果。使用callback异步回调。

> **说明：**
> 
> 当前注册监听接口，不支持在on监听的回调方法里，调用off注销回调。

**起始版本：** 10

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 监听事件，固定为'error'，photoOutput创建成功后可监听。拍照接口调用时出现错误触发该事件并返回错误信息。 |
| callback | [ErrorCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-errorcallback-i.md) | 是 | 回调函数，用于获取错误信息。返回错误码，错误码类型[CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md)。 |

## onCapturePhotoAvailable

```TypeScript
onCapturePhotoAvailable(callback: Callback<CapturePhoto>): void
```

注册监听全质量图和未压缩图。使用callback异步回调。

> **说明：**
> 
> - 注册监听接口时，不支持在该接口监听的回调方法里调用
> [offCapturePhotoAvailable](#offcapturephotoavailable)
> 注销回调。
> 
> - 拍摄未压缩图（YUV）格式图片时，仅支持使用此接口注册监听。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[CapturePhoto](arkts-camera-camera-capturephoto-i.md)&gt; | 是 | 回调函数，用于监听全质量图和未压缩图上报事件。 |

**示例**

```TypeScript
import { camera } from '@kit.CameraKit';
import { image } from '@kit.ImageKit';

function callback(capturePhoto: camera.CapturePhoto): void {
  let picture: image.Image | image.Picture = capturePhoto.main;
}

function registerCapturePhotoOutputPhotoAvailable(photoOutput: camera.PhotoOutput): void {
  photoOutput.onCapturePhotoAvailable(callback);
}
```

## setMovingPhotoVideoCodecType

```TypeScript
setMovingPhotoVideoCodecType(codecType: VideoCodecType): void
```

设置动态照片短视频编码类型。

**起始版本：** 13

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| codecType | [VideoCodecType](arkts-camera-camera-videocodectype-e.md) | 是 | 动态照片短视频编码类型。 如果设置不在枚举范围内，则该参数不会生效。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

**示例**

```TypeScript
function setMovingPhotoVideoCodecTypes(photoOutput: camera.PhotoOutput, videoCodecType: camera.VideoCodecType): void {
  photoOutput.setMovingPhotoVideoCodecType(videoCodecType);
}
```

## setPhotoQualityPrioritization

```TypeScript
setPhotoQualityPrioritization(qualityPrioritization: PhotoQualityPrioritization): void
```

设置拍照画质优先策略。设置之前，可先使用方法 [isPhotoQualityPrioritizationSupported](#isphotoqualityprioritizationsupported)对设备是否支持指定的 拍照画质优先策略进行检查。

**起始版本：** 21

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| qualityPrioritization | [PhotoQualityPrioritization](arkts-camera-camera-photoqualityprioritization-e.md) | 是 | 要设置的拍照画质优先策略。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error, reconfiguring streams is needed to recover from failure. |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { camera } from '@kit.CameraKit';

let photoOutput: camera.PhotoOutput;

function setPhotoQualityPrioritization(qualityPrioritization: camera.PhotoQualityPrioritization): void {
  try {
    photoOutput.setPhotoQualityPrioritization(qualityPrioritization);
  } catch (error) {
    let err = error as BusinessError;
    console.error(`The setPhotoQualityPrioritization call failed. error code: ${err.code}`);
  }
}
```
