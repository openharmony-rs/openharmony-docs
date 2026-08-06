# PhotoOutput

拍照会话中使用的输出信息，继承[CameraOutput]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_。

**继承/实现关系：** PhotoOutput extends [CameraOutput](arkts-camera-camera-cameraoutput-i.md)

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-camera-interface PhotoOutput extends CameraOutput--><!--Device-camera-interface PhotoOutput extends CameraOutput-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## capture

```TypeScript
capture(callback: AsyncCallback<void>): void
```

以默认设置触发一次拍照，通过注册回调函数获取结果。使用callback异步回调。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoOutput-capture(callback: AsyncCallback<void>): void--><!--Device-PhotoOutput-capture(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | 回调函数。当以默认设置触发拍照成功，err为undefined，否则为错误对象。错误码类型[CameraErrorCode]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400104](../errorcode-camera.md#7400104-会话未运行) | Session not running. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

## capture

```TypeScript
capture(): Promise<void>
```

以默认设置触发一次拍照。使用Promise异步回调。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoOutput-capture(): Promise<void>--><!--Device-PhotoOutput-capture(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400104](../errorcode-camera.md#7400104-会话未运行) | Session not running. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

## capture

```TypeScript
capture(setting: PhotoCaptureSetting, callback: AsyncCallback<void>): void
```

以指定参数触发一次拍照，通过注册回调函数获取结果。使用callback异步回调。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoOutput-capture(setting: PhotoCaptureSetting, callback: AsyncCallback<void>): void--><!--Device-PhotoOutput-capture(setting: PhotoCaptureSetting, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| setting | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 拍照设置，传入undefined类型数据按默认设置触发一次拍照处理。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | 回调函数，用于获取结果。接口调用失败会返回相应错误码，错误码类型[CameraErrorCode]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400104](../errorcode-camera.md#7400104-会话未运行) | Session not running. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

## capture

```TypeScript
capture(setting: PhotoCaptureSetting): Promise<void>
```

以指定参数触发一次拍照。使用Promise异步回调。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoOutput-capture(setting: PhotoCaptureSetting): Promise<void>--><!--Device-PhotoOutput-capture(setting: PhotoCaptureSetting): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| setting | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 拍照设置，传入undefined类型数据按默认设置触发一次拍照处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400104](../errorcode-camera.md#7400104-会话未运行) | Session not running. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

## enableAutoExtendedGainmapDelivery

```TypeScript
enableAutoExtendedGainmapDelivery(enabled: boolean): void
```

是否启用自动扩展增益图（Gainmap）的输出。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoOutput-enableAutoExtendedGainmapDelivery(enabled: boolean): void--><!--Device-PhotoOutput-enableAutoExtendedGainmapDelivery(enabled: boolean): void-End-->

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

## enableMirror

```TypeScript
enableMirror(enabled: boolean): void
```

是否启用动态照片镜像拍照。 调用该接口前，需要通过[isMovingPhotoSupported]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_查询是否支持动态照片拍摄功能以及通过 [isMirrorSupported]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_查询是否支持镜像拍照功能。

**起始版本：** 13

**ArkTS模式：** ArkTS-Dyn起始版本为13；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoOutput-enableMirror(enabled: boolean): void--><!--Device-PhotoOutput-enableMirror(enabled: boolean): void-End-->

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

## enableMovingPhoto

```TypeScript
enableMovingPhoto(enabled: boolean): void
```

使能动态照片拍照。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**需要权限：** ohos.permission.MICROPHONE

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoOutput-enableMovingPhoto(enabled: boolean): void--><!--Device-PhotoOutput-enableMovingPhoto(enabled: boolean): void-End-->

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

## getActiveProfile

```TypeScript
getActiveProfile(): Profile
```

获取当前生效的配置信息。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoOutput-getActiveProfile(): Profile--><!--Device-PhotoOutput-getActiveProfile(): Profile-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 当前生效的配置信息 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

## getPhotoRotation

ArkTS-Dyn:
```TypeScript
getPhotoRotation(deviceDegree?: number): ImageRotation
```

ArkTS-Sta:
```TypeScript
getPhotoRotation(deviceDegree?: int): ImageRotation
```

获取拍照旋转角度。 - 设备自然方向：设备默认使用方向。例如，直板机默认使用方向为竖屏（充电口向下）。 - 相机镜头角度：值等于相机图像顺时针旋转到设备自然方向的角度。例如，直板机后置相机传感器是横屏安装的，所以需要顺时针旋转90度到设备自然方向。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoOutput-getPhotoRotation(deviceDegree?: int): ImageRotation--><!--Device-PhotoOutput-getPhotoRotation(deviceDegree?: int): ImageRotation-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceDegree | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 否 | 设备旋转角度，单位度，取值范围：[0, 360]。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_若入参超过该范围，则取入参除以360的余数。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_从API version 23开始，入参deviceDegree为可选参数，当不传入参数时，由系统获取deviceDegree进行拍照旋转角度计算。\_\_\_HTML\_TAG\_USD\_0\_\_\_**起始版本：** 23 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回拍照旋转角度。若接口调用失败，返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12 - 22 |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

## getSupportedMovingPhotoVideoCodecTypes

```TypeScript
getSupportedMovingPhotoVideoCodecTypes(): Array<VideoCodecType>
```

查询支持的动态照片短视频编码类型。

**起始版本：** 13

**ArkTS模式：** ArkTS-Dyn起始版本为13；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoOutput-getSupportedMovingPhotoVideoCodecTypes(): Array<VideoCodecType>--><!--Device-PhotoOutput-getSupportedMovingPhotoVideoCodecTypes(): Array<VideoCodecType>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;VideoCodecType&gt; | 支持的动态照片短视频编码类型列表。若接口调用失败，返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

## isAutoExtendedGainmapDeliverySupported

```TypeScript
isAutoExtendedGainmapDeliverySupported(): boolean
```

确认是否支持自动扩展增益图（Gainmap）的输出。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoOutput-isAutoExtendedGainmapDeliverySupported(): boolean--><!--Device-PhotoOutput-isAutoExtendedGainmapDeliverySupported(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 是否支持自动扩展增益图（Gainmap）的输出。true表示支持，false表示不支持。 |

## isMirrorSupported

```TypeScript
isMirrorSupported(): boolean
```

查询是否支持镜像拍照。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoOutput-isMirrorSupported(): boolean--><!--Device-PhotoOutput-isMirrorSupported(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回是否支持镜像拍照，true表示支持，false表示不支持。若接口调用失败，返回undefined。 |

## isMovingPhotoSupported

```TypeScript
isMovingPhotoSupported(): boolean
```

查询是否支持动态照片拍摄。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoOutput-isMovingPhotoSupported(): boolean--><!--Device-PhotoOutput-isMovingPhotoSupported(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回是否支持动态照片拍照。true表示支持，false表示不支持。若接口调用失败，返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

## isPhotoQualityPrioritizationSupported

```TypeScript
isPhotoQualityPrioritizationSupported(qualityPrioritization: PhotoQualityPrioritization): boolean
```

检查是否支持指定的拍照画质优先策略。

**起始版本：** 21

**ArkTS模式：** ArkTS-Dyn起始版本为21；ArkTS-Sta起始版本为24。

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoOutput-isPhotoQualityPrioritizationSupported(qualityPrioritization: PhotoQualityPrioritization): boolean--><!--Device-PhotoOutput-isPhotoQualityPrioritizationSupported(qualityPrioritization: PhotoQualityPrioritization): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| qualityPrioritization | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 要检查的拍照画质优先策略。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 是否支持指定的拍照画质优先策略。true表示支持，false表示不支持。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error,reconfiguring streams is needed to recover from failure. |

## off('photoAvailable')

```TypeScript
off(type: 'photoAvailable', callback?: AsyncCallback<Photo>): void
```

注销监听拍照返回照片上报事件。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoOutput-off(type: 'photoAvailable', callback?: AsyncCallback<Photo>): void--><!--Device-PhotoOutput-off(type: 'photoAvailable', callback?: AsyncCallback<Photo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'photoAvailable' | 是 | 监听事件，固定为'photoAvailable'，photoOutput创建成功后可监听。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;Photo&gt; | 否 | 回调函数，如果指定参数则取消对应callback（callback对象不可是匿名函数），否则取消所有callback。 |

## off('photoAssetAvailable')

```TypeScript
off(type: 'photoAssetAvailable', callback?: AsyncCallback<photoAccessHelper.PhotoAsset>): void
```

注销photoAsset上报。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoOutput-off(type: 'photoAssetAvailable', callback?: AsyncCallback<photoAccessHelper.PhotoAsset>): void--><!--Device-PhotoOutput-off(type: 'photoAssetAvailable', callback?: AsyncCallback<photoAccessHelper.PhotoAsset>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'photoAssetAvailable' | 是 | 监听事件，固定为'photoAssetAvailable'，photoOutput创建成功后可监听。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;photoAccessHelper.PhotoAsset&gt; | 否 | 需要解监听的回调方法。如果callback不为空且与此对应的监听方法一致，不为匿名方法，则解注册该方法；如果callback为空，则解监听所有回调。 |

## off('captureStart')

```TypeScript
off(type: 'captureStart', callback?: AsyncCallback<number>): void
```

注销拍照开始的监听。 > **说明：** > > 从 API version 10开始支持，从API version 11开始废弃。 > > 当前注册监听接口，不支持在on监听的回调方法里，调用off注销回调。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** 11

**替代接口：** camera.PhotoOutput.off(type:

<!--Device-PhotoOutput-off(type: 'captureStart', callback?: AsyncCallback<number>): void--><!--Device-PhotoOutput-off(type: 'captureStart', callback?: AsyncCallback<number>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'captureStart' | 是 | 监听事件，固定为'captureStart'，photoOutput创建成功后可监听。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;number&gt; | 否 | 回调函数，如果指定参数则取消对应callback（callback对象不可是匿名函数），否则取消所有callback。 |

## off('captureStartWithInfo')

```TypeScript
off(type: 'captureStartWithInfo', callback?: AsyncCallback<CaptureStartInfo>): void
```

注销监听拍照。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoOutput-off(type: 'captureStartWithInfo', callback?: AsyncCallback<CaptureStartInfo>): void--><!--Device-PhotoOutput-off(type: 'captureStartWithInfo', callback?: AsyncCallback<CaptureStartInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'captureStartWithInfo' | 是 | 监听事件，固定为'captureStartWithInfo'，photoOutput创建成功后可监听。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;CaptureStartInfo&gt; | 否 | 回调函数，如果指定参数则取消对应callback（callback对象不可是匿名函数），否则取消所有callback。 |

## off('frameShutter')

```TypeScript
off(type: 'frameShutter', callback?: AsyncCallback<FrameShutterInfo>): void
```

注销监听拍照帧输出捕获。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoOutput-off(type: 'frameShutter', callback?: AsyncCallback<FrameShutterInfo>): void--><!--Device-PhotoOutput-off(type: 'frameShutter', callback?: AsyncCallback<FrameShutterInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'frameShutter' | 是 | 监听事件，固定为'frameShutter'，photoOutput创建成功后可监听。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;FrameShutterInfo&gt; | 否 | 回调函数，如果指定参数则取消对应callback（callback对象不可是匿名函数），否则取消所有callback。 |

## off('frameShutterEnd')

```TypeScript
off(type: 'frameShutterEnd', callback?: AsyncCallback<FrameShutterEndInfo>): void
```

注销监听拍照曝光结束捕获。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoOutput-off(type: 'frameShutterEnd', callback?: AsyncCallback<FrameShutterEndInfo>): void--><!--Device-PhotoOutput-off(type: 'frameShutterEnd', callback?: AsyncCallback<FrameShutterEndInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'frameShutterEnd' | 是 | 监听事件，固定为'frameShutterEnd'，photoOutput创建成功后可监听。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;FrameShutterEndInfo&gt; | 否 | 回调函数，如果指定参数则取消对应callback（callback对象不可是匿名函数），否则取消所有callback。 |

## off('captureEnd')

```TypeScript
off(type: 'captureEnd', callback?: AsyncCallback<CaptureEndInfo>): void
```

注销监听拍照结束。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoOutput-off(type: 'captureEnd', callback?: AsyncCallback<CaptureEndInfo>): void--><!--Device-PhotoOutput-off(type: 'captureEnd', callback?: AsyncCallback<CaptureEndInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'captureEnd' | 是 | 监听事件，固定为'captureEnd'，photoOutput创建成功后可监听。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;CaptureEndInfo&gt; | 否 | 回调函数，如果指定参数则取消对应callback（callback对象不可是匿名函数），否则取消所有callback。 |

## off('captureReady')

```TypeScript
off(type: 'captureReady', callback?: AsyncCallback<void>): void
```

注销监听可拍下一张。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoOutput-off(type: 'captureReady', callback?: AsyncCallback<void>): void--><!--Device-PhotoOutput-off(type: 'captureReady', callback?: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'captureReady' | 是 | 监听事件，固定为'captureReady'，photoOutput创建成功后可监听。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 否 | 回调函数，如果指定参数则取消对应callback（callback对象不可是匿名函数），否则取消所有callback。 |

## off('estimatedCaptureDuration')

```TypeScript
off(type: 'estimatedCaptureDuration', callback?: AsyncCallback<double>): void
```

注销监听预估的拍照时间。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoOutput-off(type: 'estimatedCaptureDuration', callback?: AsyncCallback<double>): void--><!--Device-PhotoOutput-off(type: 'estimatedCaptureDuration', callback?: AsyncCallback<double>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'estimatedCaptureDuration' | 是 | 监听事件，固定为'estimatedCaptureDuration'，photoOutput创建成功后可监听。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;double&gt; | 否 | 回调函数，如果指定参数则取消对应callback（callback对象不可是匿名函数），否则取消所有callback。 |

## off('error')

```TypeScript
off(type: 'error', callback?: ErrorCallback): void
```

注销监听拍照输出发生错误。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoOutput-off(type: 'error', callback?: ErrorCallback): void--><!--Device-PhotoOutput-off(type: 'error', callback?: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 监听事件，固定为'error'，photoOutput创建成功后可监听。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 回调函数，如果指定参数则取消对应callback（callback对象不可是匿名函数），否则取消所有callback。 |

## offCaptureEnd

```TypeScript
offCaptureEnd(callback?: AsyncCallback<CaptureEndInfo>): void
```

Unsubscribes from capture end event callback.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-PhotoOutput-offCaptureEnd(callback?: AsyncCallback<CaptureEndInfo>): void--><!--Device-PhotoOutput-offCaptureEnd(callback?: AsyncCallback<CaptureEndInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;CaptureEndInfo&gt; | 否 | Callback used to get the capture end information. |

## offCapturePhotoAvailable

```TypeScript
offCapturePhotoAvailable(callback?: Callback<CapturePhoto>): void
```

注销监听全质量图和未压缩图。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoOutput-offCapturePhotoAvailable(callback?: Callback<CapturePhoto>): void--><!--Device-PhotoOutput-offCapturePhotoAvailable(callback?: Callback<CapturePhoto>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;CapturePhoto&gt; | 否 | 回调函数，如果指定参数则取消对应callback，callback对象不可是匿名函数，否则取消所有callback。 |

## offCaptureReady

```TypeScript
offCaptureReady(callback?: AsyncCallback<void>): void
```

Unsubscribes from capture ready event callback.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-PhotoOutput-offCaptureReady(callback?: AsyncCallback<void>): void--><!--Device-PhotoOutput-offCaptureReady(callback?: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 否 | Callback used to notice capture ready. |

## offCaptureStartWithInfo

```TypeScript
offCaptureStartWithInfo(callback?: AsyncCallback<CaptureStartInfo>): void
```

Unsubscribes from capture start event callback.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-PhotoOutput-offCaptureStartWithInfo(callback?: AsyncCallback<CaptureStartInfo>): void--><!--Device-PhotoOutput-offCaptureStartWithInfo(callback?: AsyncCallback<CaptureStartInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;CaptureStartInfo&gt; | 否 | Callback used to get the capture start info. |

## offError

```TypeScript
offError(callback?: ErrorCallback): void
```

Unsubscribes from error events.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-PhotoOutput-offError(callback?: ErrorCallback): void--><!--Device-PhotoOutput-offError(callback?: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | Callback used to get the photo output errors. |

## offEstimatedCaptureDuration

```TypeScript
offEstimatedCaptureDuration(callback?: AsyncCallback<double>): void
```

Unsubscribes from estimated capture duration event callback.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-PhotoOutput-offEstimatedCaptureDuration(callback?: AsyncCallback<double>): void--><!--Device-PhotoOutput-offEstimatedCaptureDuration(callback?: AsyncCallback<double>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;double&gt; | 否 | Callback used to notify the estimated capture duration (in milliseconds). |

## offFrameShutter

```TypeScript
offFrameShutter(callback?: AsyncCallback<FrameShutterInfo>): void
```

Unsubscribes from frame shutter event callback.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-PhotoOutput-offFrameShutter(callback?: AsyncCallback<FrameShutterInfo>): void--><!--Device-PhotoOutput-offFrameShutter(callback?: AsyncCallback<FrameShutterInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;FrameShutterInfo&gt; | 否 | Callback used to get the frame shutter information. |

## offFrameShutterEnd

```TypeScript
offFrameShutterEnd(callback?: AsyncCallback<FrameShutterEndInfo>): void
```

Unsubscribes from frame shutter end event callback.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-PhotoOutput-offFrameShutterEnd(callback?: AsyncCallback<FrameShutterEndInfo>): void--><!--Device-PhotoOutput-offFrameShutterEnd(callback?: AsyncCallback<FrameShutterEndInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;FrameShutterEndInfo&gt; | 否 | Callback used to get the frame shutter end information. |

## offPhotoAssetAvailable

```TypeScript
offPhotoAssetAvailable(callback?: AsyncCallback<photoAccessHelper.PhotoAsset>): void
```

Unsubscribes photo asset event callback.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-PhotoOutput-offPhotoAssetAvailable(callback?: AsyncCallback<photoAccessHelper.PhotoAsset>): void--><!--Device-PhotoOutput-offPhotoAssetAvailable(callback?: AsyncCallback<photoAccessHelper.PhotoAsset>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;photoAccessHelper.PhotoAsset&gt; | 否 | Callback used to get the asset. |

## offPhotoAvailable

```TypeScript
offPhotoAvailable(callback?: AsyncCallback<Photo>): void
```

Unsubscribes photo available event callback.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-PhotoOutput-offPhotoAvailable(callback?: AsyncCallback<Photo>): void--><!--Device-PhotoOutput-offPhotoAvailable(callback?: AsyncCallback<Photo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;Photo&gt; | 否 | Callback used to get the Photo. |

## on('photoAvailable')

```TypeScript
on(type: 'photoAvailable', callback: AsyncCallback<Photo>): void
```

注册监听拍照返回照片上报事件。使用callback异步回调。 > **说明：** > > 当前注册监听接口，不支持在on监听的回调方法里，调用off注销回调。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoOutput-on(type: 'photoAvailable', callback: AsyncCallback<Photo>): void--><!--Device-PhotoOutput-on(type: 'photoAvailable', callback: AsyncCallback<Photo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'photoAvailable' | 是 | 监听事件，固定为'photoAvailable'，photoOutput创建成功后可监听。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;Photo&gt; | 是 | 回调函数，用于监听拍照返回照片上报事件。 |

## on('photoAssetAvailable')

```TypeScript
on(type: 'photoAssetAvailable', callback: AsyncCallback<photoAccessHelper.PhotoAsset>): void
```

注册监听photoAsset上报。使用callback异步回调。 > **说明：** > > 当前注册监听接口，不支持在on监听的回调方法里，调用off注销回调。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoOutput-on(type: 'photoAssetAvailable', callback: AsyncCallback<photoAccessHelper.PhotoAsset>): void--><!--Device-PhotoOutput-on(type: 'photoAssetAvailable', callback: AsyncCallback<photoAccessHelper.PhotoAsset>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'photoAssetAvailable' | 是 | 监听事件，固定为'photoAssetAvailable'，photoOutput创建成功后可监听。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;photoAccessHelper.PhotoAsset&gt; | 是 | 回调函数，用于监听photoAsset上报。 |

## on('captureStart')

```TypeScript
on(type: 'captureStart', callback: AsyncCallback<number>): void
```

监听拍照开始，通过注册回调函数获取Capture ID。使用callback异步回调。 > **说明：** > > 从 API version 10开始支持，从API version 11开始废弃。 > > 当前注册监听接口，不支持在on监听的回调方法里，调用off注销回调。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** 11

**替代接口：** camera.PhotoOutput.on(type:

<!--Device-PhotoOutput-on(type: 'captureStart', callback: AsyncCallback<number>): void--><!--Device-PhotoOutput-on(type: 'captureStart', callback: AsyncCallback<number>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'captureStart' | 是 | 监听事件，固定为'captureStart'，photoOutput创建成功后可监听。每次拍照，底层开始曝光时触发该事件并返回。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;number&gt; | 是 | 使用callback的方式获取Capture ID。 |

## on('captureStartWithInfo')

```TypeScript
on(type: 'captureStartWithInfo', callback: AsyncCallback<CaptureStartInfo>): void
```

监听拍照开始，通过注册回调函数获取[CaptureStartInfo]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_。使用callback异步回调。 > **说明：** > > 当前注册监听接口，不支持在on监听的回调方法里，调用off注销回调。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoOutput-on(type: 'captureStartWithInfo', callback: AsyncCallback<CaptureStartInfo>): void--><!--Device-PhotoOutput-on(type: 'captureStartWithInfo', callback: AsyncCallback<CaptureStartInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'captureStartWithInfo' | 是 | 监听事件，固定为'captureStartWithInfo'，photoOutput创建成功后可监听。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;CaptureStartInfo&gt; | 是 | 使用callback的方式获取Capture ID。 |

## on('frameShutter')

```TypeScript
on(type: 'frameShutter', callback: AsyncCallback<FrameShutterInfo>): void
```

监听拍照帧输出捕获，通过注册回调函数获取结果。使用callback异步回调。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoOutput-on(type: 'frameShutter', callback: AsyncCallback<FrameShutterInfo>): void--><!--Device-PhotoOutput-on(type: 'frameShutter', callback: AsyncCallback<FrameShutterInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'frameShutter' | 是 | 监听事件，固定为'frameShutter'，photoOutput创建成功后可监听。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;FrameShutterInfo&gt; | 是 | 回调函数，用于获取相关信息。该回调返回意味着可以再次下发拍照请求。 |

## on('frameShutterEnd')

```TypeScript
on(type: 'frameShutterEnd', callback: AsyncCallback<FrameShutterEndInfo>): void
```

监听拍照曝光结束捕获，通过注册回调函数获取结果。使用callback异步回调。 > **说明：** > > 当前注册监听接口，不支持在on监听的回调方法里，调用off注销回调。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoOutput-on(type: 'frameShutterEnd', callback: AsyncCallback<FrameShutterEndInfo>): void--><!--Device-PhotoOutput-on(type: 'frameShutterEnd', callback: AsyncCallback<FrameShutterEndInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'frameShutterEnd' | 是 | 监听事件，固定为'frameShutterEnd'，photoOutput创建成功后可监听。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;FrameShutterEndInfo&gt; | 是 | 回调函数，用于获取相关信息。该回调返回表示拍照曝光结束。 |

## on('captureEnd')

```TypeScript
on(type: 'captureEnd', callback: AsyncCallback<CaptureEndInfo>): void
```

监听拍照结束，通过注册回调函数获取结果。使用callback异步回调。 > **说明：** > > 当前注册监听接口，不支持在on监听的回调方法里，调用off注销回调。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoOutput-on(type: 'captureEnd', callback: AsyncCallback<CaptureEndInfo>): void--><!--Device-PhotoOutput-on(type: 'captureEnd', callback: AsyncCallback<CaptureEndInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'captureEnd' | 是 | 监听事件，固定为'captureEnd'。photoOutput创建成功后可监听。拍照完全结束可触发该事件发生并返回相应信息。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;CaptureEndInfo&gt; | 是 | 回调函数，用于获取相关信息。 |

## on('captureReady')

```TypeScript
on(type: 'captureReady', callback: AsyncCallback<void>): void
```

监听可拍下一张，通过注册回调函数获取结果。使用callback异步回调。 > **说明：** > > 当前注册监听接口，不支持在on监听的回调方法里，调用off注销回调。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoOutput-on(type: 'captureReady', callback: AsyncCallback<void>): void--><!--Device-PhotoOutput-on(type: 'captureReady', callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'captureReady' | 是 | 监听事件，固定为'captureReady'，photoOutput创建成功后可监听。当下一张可拍时可触发该事件发生并返回相应信息。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | 回调函数，用于获取相关信息。 |

## on('estimatedCaptureDuration')

```TypeScript
on(type: 'estimatedCaptureDuration', callback: AsyncCallback<double>): void
```

监听预估的拍照时间，通过注册回调函数获取结果。使用callback异步回调。 > **说明：** > > 当前注册监听接口，不支持在on监听的回调方法里，调用off注销回调。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoOutput-on(type: 'estimatedCaptureDuration', callback: AsyncCallback<double>): void--><!--Device-PhotoOutput-on(type: 'estimatedCaptureDuration', callback: AsyncCallback<double>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'estimatedCaptureDuration' | 是 | 监听事件，固定为'estimatedCaptureDuration'，photoOutput创建成功后可监听。拍照完全结束可触发该事件发生并返回相应信息。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;double&gt; | 是 | 回调函数，用于获取预估的单次拍照底层出sensor采集帧时间，单位：毫秒。如果上报-1，代表没有预估时间。 |

## on('error')

```TypeScript
on(type: 'error', callback: ErrorCallback): void
```

监听拍照输出发生错误，通过注册回调函数获取结果。使用callback异步回调。 > **说明：** > > 当前注册监听接口，不支持在on监听的回调方法里，调用off注销回调。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoOutput-on(type: 'error', callback: ErrorCallback): void--><!--Device-PhotoOutput-on(type: 'error', callback: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 监听事件，固定为'error'，photoOutput创建成功后可监听。拍照接口调用时出现错误触发该事件并返回错误信息。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 回调函数，用于获取错误信息。返回错误码，错误码类型[CameraErrorCode]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 |

## onCaptureEnd

```TypeScript
onCaptureEnd(callback: AsyncCallback<CaptureEndInfo>): void
```

Subscribes capture end event callback.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-PhotoOutput-onCaptureEnd(callback: AsyncCallback<CaptureEndInfo>): void--><!--Device-PhotoOutput-onCaptureEnd(callback: AsyncCallback<CaptureEndInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;CaptureEndInfo&gt; | 是 | Callback used to get the capture end information. |

## onCapturePhotoAvailable

```TypeScript
onCapturePhotoAvailable(callback: Callback<CapturePhoto>): void
```

注册监听全质量图和未压缩图。使用callback异步回调。 > **说明：** > > - 注册监听接口时，不支持在该接口监听的回调方法里调用 > [offCapturePhotoAvailable]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ > 注销回调。 > > - 拍摄未压缩图（YUV）格式图片时，仅支持使用此接口注册监听。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoOutput-onCapturePhotoAvailable(callback: Callback<CapturePhoto>): void--><!--Device-PhotoOutput-onCapturePhotoAvailable(callback: Callback<CapturePhoto>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;CapturePhoto&gt; | 是 | 回调函数，用于监听全质量图和未压缩图上报事件。 |

## onCaptureReady

```TypeScript
onCaptureReady(callback: AsyncCallback<void>): void
```

Subscribes capture ready event callback. After receiving the callback, can proceed to the next capture

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-PhotoOutput-onCaptureReady(callback: AsyncCallback<void>): void--><!--Device-PhotoOutput-onCaptureReady(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | Callback used to notice capture ready. |

## onCaptureStartWithInfo

```TypeScript
onCaptureStartWithInfo(callback: AsyncCallback<CaptureStartInfo>): void
```

Subscribes capture start event callback.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-PhotoOutput-onCaptureStartWithInfo(callback: AsyncCallback<CaptureStartInfo>): void--><!--Device-PhotoOutput-onCaptureStartWithInfo(callback: AsyncCallback<CaptureStartInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;CaptureStartInfo&gt; | 是 | Callback used to get the capture start info. |

## onError

```TypeScript
onError(callback: ErrorCallback): void
```

Subscribes to error events.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-PhotoOutput-onError(callback: ErrorCallback): void--><!--Device-PhotoOutput-onError(callback: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | Callback used to get the photo output errors. |

## onEstimatedCaptureDuration

```TypeScript
onEstimatedCaptureDuration(callback: AsyncCallback<double>): void
```

Subscribes estimated capture duration event callback.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-PhotoOutput-onEstimatedCaptureDuration(callback: AsyncCallback<double>): void--><!--Device-PhotoOutput-onEstimatedCaptureDuration(callback: AsyncCallback<double>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;double&gt; | 是 | Callback used to notify the estimated capture duration (in milliseconds). |

## onFrameShutter

```TypeScript
onFrameShutter(callback: AsyncCallback<FrameShutterInfo>): void
```

Subscribes frame shutter event callback.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-PhotoOutput-onFrameShutter(callback: AsyncCallback<FrameShutterInfo>): void--><!--Device-PhotoOutput-onFrameShutter(callback: AsyncCallback<FrameShutterInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;FrameShutterInfo&gt; | 是 | Callback used to get the frame shutter information. |

## onFrameShutterEnd

```TypeScript
onFrameShutterEnd(callback: AsyncCallback<FrameShutterEndInfo>): void
```

Subscribes frame shutter end event callback.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-PhotoOutput-onFrameShutterEnd(callback: AsyncCallback<FrameShutterEndInfo>): void--><!--Device-PhotoOutput-onFrameShutterEnd(callback: AsyncCallback<FrameShutterEndInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;FrameShutterEndInfo&gt; | 是 | Callback used to get the frame shutter end information. |

## onPhotoAssetAvailable

```TypeScript
onPhotoAssetAvailable(callback: AsyncCallback<photoAccessHelper.PhotoAsset>): void
```

Subscribes to photo asset event callback. This API processes deferred photo delivery data by quickly displaying low-quality images to give users the impression of faster photo capture, while also generating high-quality images to maintain the final output quality. For details about the design specifications, see \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-PhotoOutput-onPhotoAssetAvailable(callback: AsyncCallback<photoAccessHelper.PhotoAsset>): void--><!--Device-PhotoOutput-onPhotoAssetAvailable(callback: AsyncCallback<photoAccessHelper.PhotoAsset>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;photoAccessHelper.PhotoAsset&gt; | 是 | Callback used to get the asset. |

## onPhotoAvailable

```TypeScript
onPhotoAvailable(callback: AsyncCallback<Photo>): void
```

Subscribes photo available event callback.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-PhotoOutput-onPhotoAvailable(callback: AsyncCallback<Photo>): void--><!--Device-PhotoOutput-onPhotoAvailable(callback: AsyncCallback<Photo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;Photo&gt; | 是 | Callback used to get the Photo. |

## setMovingPhotoVideoCodecType

```TypeScript
setMovingPhotoVideoCodecType(codecType: VideoCodecType): void
```

设置动态照片短视频编码类型。

**起始版本：** 13

**ArkTS模式：** ArkTS-Dyn起始版本为13；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoOutput-setMovingPhotoVideoCodecType(codecType: VideoCodecType): void--><!--Device-PhotoOutput-setMovingPhotoVideoCodecType(codecType: VideoCodecType): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| codecType | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 动态照片短视频编码类型。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_如果设置不在枚举范围内，则该参数不会生效。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

## setPhotoQualityPrioritization

```TypeScript
setPhotoQualityPrioritization(qualityPrioritization: PhotoQualityPrioritization): void
```

设置拍照画质优先策略。 设置之前，可先使用方法 [isPhotoQualityPrioritizationSupported]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_对设备是否支持指定的 拍照画质优先策略进行检查。

**起始版本：** 21

**ArkTS模式：** ArkTS-Dyn起始版本为21；ArkTS-Sta起始版本为24。

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务API中使用。

<!--Device-PhotoOutput-setPhotoQualityPrioritization(qualityPrioritization: PhotoQualityPrioritization): void--><!--Device-PhotoOutput-setPhotoQualityPrioritization(qualityPrioritization: PhotoQualityPrioritization): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| qualityPrioritization | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 要设置的拍照画质优先策略。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error,reconfiguring streams is needed to recover from failure. |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed. |

