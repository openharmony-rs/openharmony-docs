# VideoOutput

录像会话中使用的输出信息，继承[CameraOutput](arkts-camera-camera-cameraoutput-i.md#CameraOutput)。

**继承/实现关系：** VideoOutput extends [CameraOutput](arkts-camera-camera-cameraoutput-i.md#CameraOutput)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-camera-interface VideoOutput--><!--Device-camera-interface VideoOutput-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## attachMetaSurface

```TypeScript
attachMetaSurface(surfaceId: string, type: VideoMetaType): void
```

Attach a meta surface to VideoOutput.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-VideoOutput-attachMetaSurface(surfaceId: string, type: VideoMetaType): void--><!--Device-VideoOutput-attachMetaSurface(surfaceId: string, type: VideoMetaType): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| surfaceId | string | 是 | Surface object id used for receiving meta infos. |
| type | [VideoMetaType](arkts-camera-camera-videometatype-e-sys.md) | 是 | Video meta type. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## enableAutoDeferredVideoEnhancement

```TypeScript
enableAutoDeferredVideoEnhancement(enabled: boolean): void
```

Enable auto deferred video enhancement if needed.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-VideoOutput-enableAutoDeferredVideoEnhancement(enabled: boolean): void--><!--Device-VideoOutput-enableAutoDeferredVideoEnhancement(enabled: boolean): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | Status of auto deferred video enhancement. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## enableAutoVideoFrameRate

```TypeScript
enableAutoVideoFrameRate(enabled: boolean): void
```

Enable auto frame rate for video capture.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-VideoOutput-enableAutoVideoFrameRate(enabled: boolean): void--><!--Device-VideoOutput-enableAutoVideoFrameRate(enabled: boolean): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | enable auto frame rate if TRUE. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## enableMirror

```TypeScript
enableMirror(enabled: boolean): void
```

启用/关闭镜像录像。 - 调用该接口前，需要通过[isMirrorSupported](#isMirrorSupported)查询是否支录像镜像功能。 - 启用/关闭录像镜像后，需要通过[getVideoRotation](arkts-camera-camera-videooutput-i.md#getVideoRotation)获取录像旋转角度以及 updateRotation更新旋转角度。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-VideoOutput-enableMirror(enabled: boolean): void--><!--Device-VideoOutput-enableMirror(enabled: boolean): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | 启用/关闭镜像录像。true为开启镜像录像，false为关闭镜像录像。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application.<br>**适用版本：** 12 - 14 |

## getSupportedRotations

```TypeScript
getSupportedRotations(): Array<ImageRotation>
```

Get supported video rotations.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-VideoOutput-getSupportedRotations(): Array<ImageRotation>--><!--Device-VideoOutput-getSupportedRotations(): Array<ImageRotation>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[ImageRotation](arkts-camera-camera-imagerotation-e.md)&gt; | The array of supported video rotations. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## getSupportedVideoMetaTypes

```TypeScript
getSupportedVideoMetaTypes(): Array<VideoMetaType>
```

Get supported video meta types.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-VideoOutput-getSupportedVideoMetaTypes(): Array<VideoMetaType>--><!--Device-VideoOutput-getSupportedVideoMetaTypes(): Array<VideoMetaType>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[VideoMetaType](arkts-camera-camera-videometatype-e-sys.md)&gt; | The array of supported video meta type. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## isAutoDeferredVideoEnhancementEnabled

```TypeScript
isAutoDeferredVideoEnhancementEnabled(): boolean
```

Confirm if auto deferred video enhancement is enabled.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-VideoOutput-isAutoDeferredVideoEnhancementEnabled(): boolean--><!--Device-VideoOutput-isAutoDeferredVideoEnhancementEnabled(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | TRUE if auto deferred video enhancement is enabled. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## isAutoDeferredVideoEnhancementSupported

```TypeScript
isAutoDeferredVideoEnhancementSupported(): boolean
```

Confirm if auto deferred video enhancement is supported in the specific device.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-VideoOutput-isAutoDeferredVideoEnhancementSupported(): boolean--><!--Device-VideoOutput-isAutoDeferredVideoEnhancementSupported(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | TRUE if auto deferred video enhancement is supported. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## isAutoVideoFrameRateSupported

```TypeScript
isAutoVideoFrameRateSupported(): boolean
```

Determine whether auto frame rate is supported.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-VideoOutput-isAutoVideoFrameRateSupported(): boolean--><!--Device-VideoOutput-isAutoVideoFrameRateSupported(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Is auto frame rate supported. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## isMirrorSupported

```TypeScript
isMirrorSupported(): boolean
```

查询是否支持镜像录像。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-VideoOutput-isMirrorSupported(): boolean--><!--Device-VideoOutput-isMirrorSupported(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回是否支持镜像录像，true表示支持，false表示不支持。若接口调用失败，返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application.<br>**适用版本：** 12 - 14 |

## isRotationSupported

```TypeScript
isRotationSupported(): boolean
```

Determine whether video rotation is supported.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-VideoOutput-isRotationSupported(): boolean--><!--Device-VideoOutput-isRotationSupported(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Is video rotation supported. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## offDeferredVideoEnhancementInfo

```TypeScript
offDeferredVideoEnhancementInfo(callback?: AsyncCallback<DeferredVideoEnhancementInfo>): void
```

Unsubscribes from deferred video enhancement info callback.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-VideoOutput-offDeferredVideoEnhancementInfo(callback?: AsyncCallback<DeferredVideoEnhancementInfo>): void--><!--Device-VideoOutput-offDeferredVideoEnhancementInfo(callback?: AsyncCallback<DeferredVideoEnhancementInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[DeferredVideoEnhancementInfo](arkts-camera-camera-deferredvideoenhancementinfo-i-sys.md)&gt; | 否 | Callback used to return the result. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## off_deferredVideoEnhancementInfo

```TypeScript
off(type: 'deferredVideoEnhancementInfo', callback?: AsyncCallback<DeferredVideoEnhancementInfo>): void
```

Unsubscribes from deferred video enhancement info callback.

**起始版本：** 13

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为13。

**废弃版本：** -1

<!--Device-VideoOutput-off(type: 'deferredVideoEnhancementInfo', callback?: AsyncCallback<DeferredVideoEnhancementInfo>): void--><!--Device-VideoOutput-off(type: 'deferredVideoEnhancementInfo', callback?: AsyncCallback<DeferredVideoEnhancementInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'deferredVideoEnhancementInfo' | 是 | Event type. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[DeferredVideoEnhancementInfo](arkts-camera-camera-deferredvideoenhancementinfo-i-sys.md)&gt; | 否 | Callback used to return the result. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## onDeferredVideoEnhancementInfo

```TypeScript
onDeferredVideoEnhancementInfo(callback: AsyncCallback<DeferredVideoEnhancementInfo>): void
```

Subscribes deferred video enhancement info callback.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-VideoOutput-onDeferredVideoEnhancementInfo(callback: AsyncCallback<DeferredVideoEnhancementInfo>): void--><!--Device-VideoOutput-onDeferredVideoEnhancementInfo(callback: AsyncCallback<DeferredVideoEnhancementInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[DeferredVideoEnhancementInfo](arkts-camera-camera-deferredvideoenhancementinfo-i-sys.md)&gt; | 是 | Callback used to return the result. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## on_deferredVideoEnhancementInfo

```TypeScript
on(type: 'deferredVideoEnhancementInfo', callback: AsyncCallback<DeferredVideoEnhancementInfo>): void
```

Subscribes deferred video enhancement info callback.

**起始版本：** 13

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为13。

**废弃版本：** -1

<!--Device-VideoOutput-on(type: 'deferredVideoEnhancementInfo', callback: AsyncCallback<DeferredVideoEnhancementInfo>): void--><!--Device-VideoOutput-on(type: 'deferredVideoEnhancementInfo', callback: AsyncCallback<DeferredVideoEnhancementInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'deferredVideoEnhancementInfo' | 是 | Event type. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[DeferredVideoEnhancementInfo](arkts-camera-camera-deferredvideoenhancementinfo-i-sys.md)&gt; | 是 | Callback used to return the result. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

## setRotation

```TypeScript
setRotation(rotation: ImageRotation): void
```

Set a video rotation.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-VideoOutput-setRotation(rotation: ImageRotation): void--><!--Device-VideoOutput-setRotation(rotation: ImageRotation): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rotation | [ImageRotation](arkts-camera-camera-imagerotation-e.md) | 是 | The rotation angle. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System Application. |

