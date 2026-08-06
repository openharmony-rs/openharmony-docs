# CameraInput

相机设备输入对象。 会话中[Session]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_使用的相机信息。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-camera-interface CameraInput--><!--Device-camera-interface CameraInput-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## close

```TypeScript
close(callback: AsyncCallback<void>): void
```

关闭相机，通过注册回调函数获取状态。使用callback异步回调。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-CameraInput-close(callback: AsyncCallback<void>): void--><!--Device-CameraInput-close(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | 回调函数。当关闭相机成功，err为undefined，否则为错误对象。错误码类型[CameraErrorCode]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

## close

```TypeScript
close(): Promise<void>
```

关闭相机，使用Promise异步回调。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-CameraInput-close(): Promise<void>--><!--Device-CameraInput-close(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

## getPhysicalCameraOrientation

ArkTS-Dyn:
```TypeScript
getPhysicalCameraOrientation(): number
```

ArkTS-Sta:
```TypeScript
getPhysicalCameraOrientation(): int
```

获取设备当前折叠状态下的物理镜头角度。

**起始版本：** 22

**ArkTS模式：** ArkTS-Dyn起始版本为22；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-CameraInput-getPhysicalCameraOrientation(): int--><!--Device-CameraInput-getPhysicalCameraOrientation(): int-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 返回设备当前折叠状态下的物理镜头角度。 |

## isPhysicalCameraOrientationVariable

```TypeScript
isPhysicalCameraOrientationVariable(): boolean
```

查询设备不同折叠状态下，相机物理镜头角度是否可变。

**起始版本：** 22

**ArkTS模式：** ArkTS-Dyn起始版本为22；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-CameraInput-isPhysicalCameraOrientationVariable(): boolean--><!--Device-CameraInput-isPhysicalCameraOrientationVariable(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 查询设备不同折叠状态下，相机物理镜头角度是否可变。true表示可变，false表示不可变。若接口调用失败，返回undefined。 |

## off('error')

```TypeScript
off(type: 'error', camera: CameraDevice, callback?: ErrorCallback): void
```

注销监听CameraInput的错误事件。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-CameraInput-off(type: 'error', camera: CameraDevice, callback?: ErrorCallback): void--><!--Device-CameraInput-off(type: 'error', camera: CameraDevice, callback?: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 监听事件，固定为'error'，CameraInput对象创建成功可监听。相机设备出错情况下可触发该事件并返回结果，比如设备不可用或者冲突等返回对应错误信息。 |
| camera | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | CameraDevice对象。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 回调函数，如果指定参数则取消对应callback（callback对象不能是匿名函数），否则取消所有callback。 |

## off('cameraOcclusionDetection')

```TypeScript
off(type: 'cameraOcclusionDetection', callback?: AsyncCallback<CameraOcclusionDetectionResult>): void
```

注销监听CameraInput的镜头遮挡或脏污事件。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-CameraInput-off(type: 'cameraOcclusionDetection', callback?: AsyncCallback<CameraOcclusionDetectionResult>): void--><!--Device-CameraInput-off(type: 'cameraOcclusionDetection', callback?: AsyncCallback<CameraOcclusionDetectionResult>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'cameraOcclusionDetection' | 是 | 监听事件，固定为'cameraOcclusionDetection'，CameraInput对象创建成功可监听。相机镜头被遮挡或有脏污可触发该事件并返回结果。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;CameraOcclusionDetectionResult&gt; | 否 | 回调函数，如果指定参数则取消对应callback（callback对象不可是匿名函数），否则取消所有callback。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12 - 22 |

## offCameraOcclusionDetection

```TypeScript
offCameraOcclusionDetection(callback?: AsyncCallback<CameraOcclusionDetectionResult>): void
```

Unsubscribes from camera occlusion detection results.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-CameraInput-offCameraOcclusionDetection(callback?: AsyncCallback<CameraOcclusionDetectionResult>): void--><!--Device-CameraInput-offCameraOcclusionDetection(callback?: AsyncCallback<CameraOcclusionDetectionResult>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;CameraOcclusionDetectionResult&gt; | 否 | Callback used to get detection results. |

## offError

```TypeScript
offError(camera: CameraDevice, callback?: ErrorCallback): void
```

Unsubscribes from error events.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-CameraInput-offError(camera: CameraDevice, callback?: ErrorCallback): void--><!--Device-CameraInput-offError(camera: CameraDevice, callback?: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| camera | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | Camera device. |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | Callback used to get the camera input errors. |

## on('error')

```TypeScript
on(type: 'error', camera: CameraDevice, callback: ErrorCallback): void
```

监听CameraInput的错误事件，通过注册回调函数获取结果。使用callback异步回调。 > **说明：** > > 当前注册监听接口，不支持在on监听的回调方法里，调用off注销回调。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-CameraInput-on(type: 'error', camera: CameraDevice, callback: ErrorCallback): void--><!--Device-CameraInput-on(type: 'error', camera: CameraDevice, callback: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 监听事件，固定为'error'，CameraInput对象创建成功可监听。相机设备出错情况下可触发该事件并返回结果，比如设备不可用或者冲突等返回对应错误信息。 |
| camera | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | CameraDevice对象。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 回调函数，用于获取结果。返回错误码，错误码类型[CameraErrorCode]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 |

## on('cameraOcclusionDetection')

```TypeScript
on(type: 'cameraOcclusionDetection', callback: AsyncCallback<CameraOcclusionDetectionResult>): void
```

监听CameraInput的镜头遮挡或脏污事件，通过注册回调函数获取结果。使用callback异步回调。 > **说明：** > > 当前注册监听接口，不支持在on监听的回调方法里，调用off注销回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-CameraInput-on(type: 'cameraOcclusionDetection', callback: AsyncCallback<CameraOcclusionDetectionResult>): void--><!--Device-CameraInput-on(type: 'cameraOcclusionDetection', callback: AsyncCallback<CameraOcclusionDetectionResult>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'cameraOcclusionDetection' | 是 | 监听事件，固定为'cameraOcclusionDetection'，CameraInput对象创建成功可监听。相机镜头被遮挡或有脏污可触发该事件并返回结果。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;CameraOcclusionDetectionResult&gt; | 是 | 回调函数，用于获取结果。返回遮挡状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12 - 22 |

## onCameraOcclusionDetection

```TypeScript
onCameraOcclusionDetection(callback: AsyncCallback<CameraOcclusionDetectionResult>): void
```

Subscribes to camera occlusion detection results.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-CameraInput-onCameraOcclusionDetection(callback: AsyncCallback<CameraOcclusionDetectionResult>): void--><!--Device-CameraInput-onCameraOcclusionDetection(callback: AsyncCallback<CameraOcclusionDetectionResult>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;CameraOcclusionDetectionResult&gt; | 是 | Callback used to get detection results. |

## onError

```TypeScript
onError(camera: CameraDevice, callback: ErrorCallback): void
```

Subscribes to error events.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-CameraInput-onError(camera: CameraDevice, callback: ErrorCallback): void--><!--Device-CameraInput-onError(camera: CameraDevice, callback: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| camera | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | Camera device. |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | Callback used to get the camera input errors. |

## open

```TypeScript
open(callback: AsyncCallback<void>): void
```

打开相机，通过注册回调函数获取状态。使用callback异步回调。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-CameraInput-open(callback: AsyncCallback<void>): void--><!--Device-CameraInput-open(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;void&gt; | 是 | 回调函数。当打开相机成功，err为undefined，否则为错误对象，错误码类型[CameraErrorCode]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400107](../errorcode-camera.md#7400107-相机冲突) | Can not use camera cause of conflict. |
| [7400108](../errorcode-camera.md#7400108-安全策略无法使用相机) | Camera disabled cause of security reason. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

## open

```TypeScript
open(): Promise<void>
```

打开相机，使用Promise异步回调。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-CameraInput-open(): Promise<void>--><!--Device-CameraInput-open(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed. |
| [7400107](../errorcode-camera.md#7400107-相机冲突) | Can not use camera cause of conflict. |
| [7400108](../errorcode-camera.md#7400108-安全策略无法使用相机) | Camera disabled cause of security reason. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

## open

```TypeScript
open(isSecureEnabled: boolean): Promise<bigint>
```

打开相机。使用Promise异步回调。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-CameraInput-open(isSecureEnabled: boolean): Promise<bigint>--><!--Device-CameraInput-open(isSecureEnabled: boolean): Promise<bigint>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isSecureEnabled | boolean | 是 | 设置true为使能以安全的方式打开相机，设置false则反之。接口调用失败会返回相应错误码，错误码类型[CameraErrorCode]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;bigint&gt; | Promise对象，返回安全相机的句柄。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400107](../errorcode-camera.md#7400107-相机冲突) | Can not use camera cause of conflict. |
| [7400108](../errorcode-camera.md#7400108-安全策略无法使用相机) | Camera disabled cause of security reason. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

## open

```TypeScript
open(type: CameraConcurrentType): Promise<void>
```

以指定的并发类型打开相机。使用Promise异步回调。

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-CameraInput-open(type: CameraConcurrentType): Promise<void>--><!--Device-CameraInput-open(type: CameraConcurrentType): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 以指定的并发类型打开相机。接口调用失败会返回相应错误码。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed. |
| [7400107](../errorcode-camera.md#7400107-相机冲突) | Can not use camera cause of conflict. |
| [7400108](../errorcode-camera.md#7400108-安全策略无法使用相机) | Camera disabled cause of security reason. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

## usePhysicalCameraOrientation

```TypeScript
usePhysicalCameraOrientation(isUsed: boolean): void
```

选择是否使用物理镜头角度。

**起始版本：** 22

**ArkTS模式：** ArkTS-Dyn起始版本为22；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-CameraInput-usePhysicalCameraOrientation(isUsed: boolean): void--><!--Device-CameraInput-usePhysicalCameraOrientation(isUsed: boolean): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isUsed | boolean | 是 | 选择是否使用物理镜头角度。true表示使用，false表示不使用。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

