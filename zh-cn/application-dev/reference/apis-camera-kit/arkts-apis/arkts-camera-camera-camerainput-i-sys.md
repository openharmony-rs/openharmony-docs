# CameraInput

相机设备输入对象。 会话中[Session](arkts-camera-camera-session-i.md#Session)使用的相机信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-camera-interface CameraInput--><!--Device-camera-interface CameraInput-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## closeDelayed

```TypeScript
closeDelayed(time: int): Promise<void>
```

Delay close camera.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-CameraInput-closeDelayed(time: int): Promise<void>--><!--Device-CameraInput-closeDelayed(time: int): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| time | int | 是 | delay time for turning off camera, in units of second. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## controlAuxiliary

```TypeScript
controlAuxiliary(auxiliaryType: AuxiliaryType, auxiliaryStatus: AuxiliaryStatus): Promise<void>
```

Control auxiliary.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-CameraInput-controlAuxiliary(auxiliaryType: AuxiliaryType, auxiliaryStatus: AuxiliaryStatus): Promise<void>--><!--Device-CameraInput-controlAuxiliary(auxiliaryType: AuxiliaryType, auxiliaryStatus: AuxiliaryStatus): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| auxiliaryType | [AuxiliaryType](arkts-camera-camera-auxiliarytype-e-sys.md) | 是 | Auxiliary type. |
| auxiliaryStatus | [AuxiliaryStatus](arkts-camera-camera-auxiliarystatus-e-sys.md) | 是 | Auxiliary status. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## off_cameraOcclusionDetection

```TypeScript
off(type: 'cameraOcclusionDetection', callback?: AsyncCallback<CameraOcclusionDetectionResult>): void
```

注销监听CameraInput的镜头遮挡或脏污事件。使用callback异步回调。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-CameraInput-off(type: 'cameraOcclusionDetection', callback?: AsyncCallback<CameraOcclusionDetectionResult>): void--><!--Device-CameraInput-off(type: 'cameraOcclusionDetection', callback?: AsyncCallback<CameraOcclusionDetectionResult>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'cameraOcclusionDetection' | 是 | 监听事件，固定为'cameraOcclusionDetection'，CameraInput对象创建成功可监听。相机镜头被遮挡或有脏污可 触发该事件并返回结果。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[CameraOcclusionDetectionResult](arkts-camera-camera-cameraocclusiondetectionresult-i-sys.md)&gt; | 否 | 回调函数，如果指定参数则取消对应callback（callback对象不可是匿名函数），否 则取消所有callback。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application.<br>**适用版本：** 12 - 22 |

## on_cameraOcclusionDetection

```TypeScript
on(type: 'cameraOcclusionDetection', callback: AsyncCallback<CameraOcclusionDetectionResult>): void
```

监听CameraInput的镜头遮挡或脏污事件，通过注册回调函数获取结果。使用callback异步回调。 > **说明：** > > 当前注册监听接口，不支持在on监听的回调方法里，调用off注销回调。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-CameraInput-on(type: 'cameraOcclusionDetection', callback: AsyncCallback<CameraOcclusionDetectionResult>): void--><!--Device-CameraInput-on(type: 'cameraOcclusionDetection', callback: AsyncCallback<CameraOcclusionDetectionResult>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'cameraOcclusionDetection' | 是 | 监听事件，固定为'cameraOcclusionDetection'，CameraInput对象创建成功可监听。相机镜头被遮挡或有脏污可 触发该事件并返回结果。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[CameraOcclusionDetectionResult](arkts-camera-camera-cameraocclusiondetectionresult-i-sys.md)&gt; | 是 | 回调函数，用于获取结果。返回遮挡状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application.<br>**适用版本：** 12 - 22 |

## usedAsPosition

```TypeScript
usedAsPosition(position: CameraPosition): void
```

Sets the camera to be used as a camera at the specified position.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-CameraInput-usedAsPosition(position: CameraPosition): void--><!--Device-CameraInput-usedAsPosition(position: CameraPosition): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| position | [CameraPosition](arkts-camera-camera-cameraposition-e.md) | 是 | The positon used for the camera. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

