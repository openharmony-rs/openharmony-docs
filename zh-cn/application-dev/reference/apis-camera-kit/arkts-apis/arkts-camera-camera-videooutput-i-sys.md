# VideoOutput

```TypeScript
interface VideoOutput extends CameraOutput
```

录像会话中使用的输出信息，继承[CameraOutput](arkts-camera-camera-cameraoutput-i.md)。

**继承/实现关系：** VideoOutput extends [CameraOutput](arkts-camera-camera-cameraoutput-i.md)

**起始版本：** 10

<!--Device-camera-interface VideoOutput extends CameraOutput--><!--Device-camera-interface VideoOutput extends CameraOutput-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
```

## attachMetaSurface

```TypeScript
attachMetaSurface(surfaceId: string, type: VideoMetaType): void
```

将元数据surface附加到VideoOutput。

**起始版本：** 12

<!--Device-VideoOutput-attachMetaSurface(surfaceId: string, type: VideoMetaType): void--><!--Device-VideoOutput-attachMetaSurface(surfaceId: string, type: VideoMetaType): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| surfaceId | string | 是 | 用于接收元数据信息的Surface对象id。 |
| type | [VideoMetaType](arkts-camera-camera-videometatype-e-sys.md) | 是 | 视频元数据类型。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

## enableAutoDeferredVideoEnhancement

```TypeScript
enableAutoDeferredVideoEnhancement(enabled: boolean): void
```

如有需要，启用自动延迟视频增强。

**起始版本：** 13

<!--Device-VideoOutput-enableAutoDeferredVideoEnhancement(enabled: boolean): void--><!--Device-VideoOutput-enableAutoDeferredVideoEnhancement(enabled: boolean): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | 自动延迟视频增强的状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

## enableAutoVideoFrameRate

```TypeScript
enableAutoVideoFrameRate(enabled: boolean): void
```

启用视频录制的自动帧率。

**起始版本：** 18

<!--Device-VideoOutput-enableAutoVideoFrameRate(enabled: boolean): void--><!--Device-VideoOutput-enableAutoVideoFrameRate(enabled: boolean): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | 为TRUE时启用自动帧率。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## getSupportedRotations

```TypeScript
getSupportedRotations(): Array<ImageRotation>
```

获取支持的视频旋转角度。

**起始版本：** 14

<!--Device-VideoOutput-getSupportedRotations(): Array<ImageRotation>--><!--Device-VideoOutput-getSupportedRotations(): Array<ImageRotation>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[ImageRotation](arkts-camera-camera-imagerotation-e.md)&gt; | 支持的视频旋转角度数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |

## getSupportedVideoMetaTypes

```TypeScript
getSupportedVideoMetaTypes(): Array<VideoMetaType>
```

获取支持的视频元数据类型。

**起始版本：** 12

<!--Device-VideoOutput-getSupportedVideoMetaTypes(): Array<VideoMetaType>--><!--Device-VideoOutput-getSupportedVideoMetaTypes(): Array<VideoMetaType>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[VideoMetaType](arkts-camera-camera-videometatype-e-sys.md)&gt; | 支持的视频元数据类型数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

## isAutoDeferredVideoEnhancementEnabled

```TypeScript
isAutoDeferredVideoEnhancementEnabled(): boolean
```

确认是否启用了自动延迟视频增强。

**起始版本：** 13

<!--Device-VideoOutput-isAutoDeferredVideoEnhancementEnabled(): boolean--><!--Device-VideoOutput-isAutoDeferredVideoEnhancementEnabled(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果启用了自动延迟视频增强，返回TRUE。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

## isAutoDeferredVideoEnhancementSupported

```TypeScript
isAutoDeferredVideoEnhancementSupported(): boolean
```

确认特定设备是否支持自动延迟视频增强。

**起始版本：** 13

<!--Device-VideoOutput-isAutoDeferredVideoEnhancementSupported(): boolean--><!--Device-VideoOutput-isAutoDeferredVideoEnhancementSupported(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果支持自动延迟视频增强，返回TRUE。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

## isAutoVideoFrameRateSupported

```TypeScript
isAutoVideoFrameRateSupported(): boolean
```

判断是否支持自动帧率。

**起始版本：** 18

<!--Device-VideoOutput-isAutoVideoFrameRateSupported(): boolean--><!--Device-VideoOutput-isAutoVideoFrameRateSupported(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 是否支持自动帧率。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |

## isRotationSupported

```TypeScript
isRotationSupported(): boolean
```

判断是否支持视频旋转。

**起始版本：** 14

<!--Device-VideoOutput-isRotationSupported(): boolean--><!--Device-VideoOutput-isRotationSupported(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 是否支持视频旋转。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |

## off('deferredVideoEnhancementInfo')

```TypeScript
off(type: 'deferredVideoEnhancementInfo', callback?: AsyncCallback<DeferredVideoEnhancementInfo>): void
```

取消订阅延迟视频增强信息回调。

**起始版本：** 13

<!--Device-VideoOutput-off(type: 'deferredVideoEnhancementInfo', callback?: AsyncCallback<DeferredVideoEnhancementInfo>): void--><!--Device-VideoOutput-off(type: 'deferredVideoEnhancementInfo', callback?: AsyncCallback<DeferredVideoEnhancementInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'deferredVideoEnhancementInfo' | 是 | 事件类型。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[DeferredVideoEnhancementInfo](arkts-camera-camera-deferredvideoenhancementinfo-i-sys.md)&gt; | 否 | 回调函数，用于返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |

## on('deferredVideoEnhancementInfo')

```TypeScript
on(type: 'deferredVideoEnhancementInfo', callback: AsyncCallback<DeferredVideoEnhancementInfo>): void
```

订阅延迟视频增强信息回调。

**起始版本：** 13

<!--Device-VideoOutput-on(type: 'deferredVideoEnhancementInfo', callback: AsyncCallback<DeferredVideoEnhancementInfo>): void--><!--Device-VideoOutput-on(type: 'deferredVideoEnhancementInfo', callback: AsyncCallback<DeferredVideoEnhancementInfo>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'deferredVideoEnhancementInfo' | 是 | 事件类型。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[DeferredVideoEnhancementInfo](arkts-camera-camera-deferredvideoenhancementinfo-i-sys.md)&gt; | 是 | 回调函数，用于返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |

## setRotation

```TypeScript
setRotation(rotation: ImageRotation): void
```

设置视频旋转角度。

**起始版本：** 14

<!--Device-VideoOutput-setRotation(rotation: ImageRotation): void--><!--Device-VideoOutput-setRotation(rotation: ImageRotation): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rotation | [ImageRotation](arkts-camera-camera-imagerotation-e.md) | 是 | 旋转角度。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Not System Application. |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
