# PreviewOutput

预览输出类。继承[CameraOutput](arkts-camera-camera-cameraoutput-i.md#CameraOutput)。

**继承/实现关系：** PreviewOutput extends [CameraOutput](arkts-camera-camera-cameraoutput-i.md#CameraOutput)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-camera-interface PreviewOutput--><!--Device-camera-interface PreviewOutput-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## enableBandwidthCompression

```TypeScript
enableBandwidthCompression(enabled: boolean): void
```

使能预览带宽压缩。 使能之前，可先使用方法[isBandwidthCompressionSupported](#isBandwidthCompressionSupported)对设备是否支持预览 带宽压缩进行检查。 > **说明：** > > 该接口只能在使用[Session.commitConfig](arkts-camera-camera-session-i.md#commitConfig)接口之前调用，否则会影响预览流 > 出流格式。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-PreviewOutput-enableBandwidthCompression(enabled: boolean): void--><!--Device-PreviewOutput-enableBandwidthCompression(enabled: boolean): void-End-->

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

## getActiveFrameRate

```TypeScript
getActiveFrameRate(): FrameRateRange
```

获取已设置的帧率范围。 使用[setFrameRate](#setFrameRate)接口对预览流设置过帧率后可查询。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-PreviewOutput-getActiveFrameRate(): FrameRateRange--><!--Device-PreviewOutput-getActiveFrameRate(): FrameRateRange-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FrameRateRange](arkts-camera-camera-frameraterange-i.md) | 帧率范围 |

## getActiveProfile

```TypeScript
getActiveProfile(): Profile
```

获取当前生效的配置信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-PreviewOutput-getActiveProfile(): Profile--><!--Device-PreviewOutput-getActiveProfile(): Profile-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Profile](arkts-camera-camera-profile-i.md) | 当前生效的配置信息 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

## getPreviewRotation

```TypeScript
getPreviewRotation(displayRotation?: int): ImageRotation
```

获取预览旋转角度。 - 设备自然方向：设备默认使用方向。例如，直板机默认使用方向为竖屏（充电口向下）。 - 相机镜头角度：值等于相机图像顺时针旋转到设备自然方向的角度。例如，直板机后置相机传感器是横屏安装的，所以需要顺时针旋转90度到设备自然方向。 - [屏幕旋转角度](https://developer.huawei.com/consumer/cn/doc/best-practices/bpta-multi-device-window-direction#section737072712182)： 显示设备的屏幕顺时针旋转角度。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-PreviewOutput-getPreviewRotation(displayRotation?: int): ImageRotation--><!--Device-PreviewOutput-getPreviewRotation(displayRotation?: int): ImageRotation-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| displayRotation | int | 否 | 显示设备的屏幕旋转角度，通过 [display.getDefaultDisplaySync](../../apis-arkui/arkts-apis/arkts-arkui-display-getdefaultdisplaysync-f.md#getDefaultDisplaySync)获得。 &lt;br&gt; 从API version 23开始，入参displayRotation为可选参数，当不传入参数时，由系统获取displayRotation进行预览旋转角度计算。 &lt;br&gt; 单位为度数（degree），取值范围为[0, 360]。<br>**起始版本：** 23 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ImageRotation](arkts-camera-camera-imagerotation-e.md) | 返回预览旋转角度。若接口调用失败，返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect.<br>**适用版本：** 12 - 22 |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

## getSupportedFrameRates

```TypeScript
getSupportedFrameRates(): Array<FrameRateRange>
```

查询支持的帧率范围。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-PreviewOutput-getSupportedFrameRates(): Array<FrameRateRange>--><!--Device-PreviewOutput-getSupportedFrameRates(): Array<FrameRateRange>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[FrameRateRange](arkts-camera-camera-frameraterange-i.md)&gt; | 支持的帧率范围列表。若接口调用失败，返回undefined。 |

## isBandwidthCompressionSupported

```TypeScript
isBandwidthCompressionSupported(): boolean
```

检查是否支持预览带宽压缩（指通过编码减少数据量，降低其在传输链路中的带宽占用）。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-PreviewOutput-isBandwidthCompressionSupported(): boolean--><!--Device-PreviewOutput-isBandwidthCompressionSupported(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 是否支持预览带宽压缩。true表示支持，false表示不支持。 |

## isLogViewAssistSupported

```TypeScript
isLogViewAssistSupported(): boolean
```

LOG视频下，查询是否支持辅助监看功能。辅助监看开启后，预览画面还原至原色域，录制出的视频仍然是LOG视频格式。 > **说明：** > > 辅助监看效果仅支持1080P及以下分辨率。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-PreviewOutput-isLogViewAssistSupported(): boolean--><!--Device-PreviewOutput-isLogViewAssistSupported(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 是否支持辅助监看功能。true表示支持，false表示不支持。 |

## offError

```TypeScript
offError(callback?: ErrorCallback): void
```

Unsubscribes from error events.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-PreviewOutput-offError(callback?: ErrorCallback): void--><!--Device-PreviewOutput-offError(callback?: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [ErrorCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-errorcallback-t.md) | 否 | Callback used to get the preview output errors. |

## offFrameEnd

```TypeScript
offFrameEnd(callback?: AsyncCallback<void>): void
```

Unsubscribes from frame end event callback.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-PreviewOutput-offFrameEnd(callback?: AsyncCallback<void>): void--><!--Device-PreviewOutput-offFrameEnd(callback?: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 否 | Callback used to return the result. |

## offFrameStart

```TypeScript
offFrameStart(callback?: AsyncCallback<void>): void
```

Unsubscribes from frame start event callback.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-PreviewOutput-offFrameStart(callback?: AsyncCallback<void>): void--><!--Device-PreviewOutput-offFrameStart(callback?: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 否 | Callback used to return the result. |

## off_error

```TypeScript
off(type: 'error', callback?: ErrorCallback): void
```

注销监听预览输出的错误事件。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-PreviewOutput-off(type: 'error', callback?: ErrorCallback): void--><!--Device-PreviewOutput-off(type: 'error', callback?: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 监听事件，固定为'error'，previewOutput创建成功可监听。 |
| callback | [ErrorCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-errorcallback-t.md) | 否 | 回调函数，如果指定参数则取消对应callback（callback对象不可是匿名函数），否则取消所有callback。 |

## off_frameEnd

```TypeScript
off(type: 'frameEnd', callback?: AsyncCallback<void>): void
```

注销监听预览帧结束。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-PreviewOutput-off(type: 'frameEnd', callback?: AsyncCallback<void>): void--><!--Device-PreviewOutput-off(type: 'frameEnd', callback?: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'frameEnd' | 是 | 监听事件，固定为'frameEnd'，previewOutput创建成功可监听。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 否 | 回调函数，如果指定参数则取消对应callback（callback对象不可是匿名函数），否则取消所有callback。 |

## off_frameStart

```TypeScript
off(type: 'frameStart', callback?: AsyncCallback<void>): void
```

注销预览帧启动的监听。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-PreviewOutput-off(type: 'frameStart', callback?: AsyncCallback<void>): void--><!--Device-PreviewOutput-off(type: 'frameStart', callback?: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'frameStart' | 是 | 监听事件，固定为'frameStart'，previewOutput创建成功可监听。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 否 | 回调函数，如果指定参数则取消对应callback（callback对象不可是匿名函数），否则取消所有callback。 |

## onError

```TypeScript
onError(callback: ErrorCallback): void
```

Subscribes to error events.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-PreviewOutput-onError(callback: ErrorCallback): void--><!--Device-PreviewOutput-onError(callback: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [ErrorCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-errorcallback-t.md) | 是 | Callback used to get the preview output errors. |

## onFrameEnd

```TypeScript
onFrameEnd(callback: AsyncCallback<void>): void
```

Subscribes frame end event callback.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-PreviewOutput-onFrameEnd(callback: AsyncCallback<void>): void--><!--Device-PreviewOutput-onFrameEnd(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | Callback used to return the result. |

## onFrameStart

```TypeScript
onFrameStart(callback: AsyncCallback<void>): void
```

Subscribes frame start event callback.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-PreviewOutput-onFrameStart(callback: AsyncCallback<void>): void--><!--Device-PreviewOutput-onFrameStart(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | Callback used to return the result. |

## on_error

```TypeScript
on(type: 'error', callback: ErrorCallback): void
```

监听预览输出的错误事件，通过注册回调函数获取结果。使用callback异步回调。 > **说明：** > > 当前注册监听接口，不支持在on监听的回调方法里，调用off注销回调。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-PreviewOutput-on(type: 'error', callback: ErrorCallback): void--><!--Device-PreviewOutput-on(type: 'error', callback: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 监听事件，固定为'error'，previewOutput创建成功可监听。预览接口使用错误时触发该事件，比如调用 [Session.start](arkts-camera-camera-session-i.md#start)，[CameraOutput.release](arkts-camera-camera-cameraoutput-i.md#release)等接口发 生错误时返回对应错误信息。 |
| callback | [ErrorCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-errorcallback-t.md) | 是 | 回调函数，用于获取错误信息。返回错误码，错误码类型[CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md#CameraErrorCode)。 |

## on_frameEnd

```TypeScript
on(type: 'frameEnd', callback: AsyncCallback<void>): void
```

监听预览帧结束，通过注册回调函数获取结果。使用callback异步回调。 > **说明：** > > 当前注册监听接口，不支持在on监听的回调方法里，调用off注销回调。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-PreviewOutput-on(type: 'frameEnd', callback: AsyncCallback<void>): void--><!--Device-PreviewOutput-on(type: 'frameEnd', callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'frameEnd' | 是 | 监听事件，固定为'frameEnd'，previewOutput创建成功可监听。预览完全结束最后一帧时触发该事件并返回。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数，用于获取结果。只要有该事件返回就证明预览结束。 |

## on_frameStart

```TypeScript
on(type: 'frameStart', callback: AsyncCallback<void>): void
```

监听预览帧启动，通过注册回调函数获取结果。使用callback异步回调。 > **说明：** > > 当前注册监听接口，不支持在on监听的回调方法里，调用off注销回调。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-PreviewOutput-on(type: 'frameStart', callback: AsyncCallback<void>): void--><!--Device-PreviewOutput-on(type: 'frameStart', callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'frameStart' | 是 | 监听事件，固定为'frameStart'，previewOutput创建成功可监听。底层第一次开始曝光时触发该事件并返回。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数，用于获取结果。只要有该事件返回就证明预览开始。 |

## setFrameRate

```TypeScript
setFrameRate(minFps: int, maxFps: int): void
```

设置预览流帧率范围，设置的范围必须在支持的帧率范围内。 进行设置前，可通过[getSupportedFrameRates](#getSupportedFrameRates)接口查询支持的帧率范围。 > **说明：** > > 仅在[PhotoSession](arkts-camera-camera-photosession-i.md#PhotoSession)或[VideoSession](arkts-camera-camera-videosession-i.md#VideoSession)模式下支持。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-PreviewOutput-setFrameRate(minFps: int, maxFps: int): void--><!--Device-PreviewOutput-setFrameRate(minFps: int, maxFps: int): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| minFps | int | 是 | 最小帧率（单位：fps），当传入的最大值小于最小值时，传参异常，接口不生效。 |
| maxFps | int | 是 | 最大帧率（单位：fps），当传入的最小值大于最大值时，传参异常，接口不生效。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400110](../errorcode-camera.md#7400110-与当前配置存在冲突) | Unresolved conflicts with current configurations. |

## setLogViewAssistEnable

```TypeScript
setLogViewAssistEnable(enable: boolean): void
```

LOG视频下，使能辅助监看之前，可先使用方法[isLogViewAssistSupported](#isLogViewAssistSupported)查询设备是否支持预览辅助 监看。 > **说明：** > > - 该接口只能在使用[Session.commitConfig](arkts-camera-camera-session-i.md#commitConfig)接口之后调用。 > > - 预览辅助监看效果仅支持1080P及以下分辨率。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-PreviewOutput-setLogViewAssistEnable(enable: boolean): void--><!--Device-PreviewOutput-setLogViewAssistEnable(enable: boolean): void-End-->

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

## setPreviewRotation

```TypeScript
setPreviewRotation(previewRotation: ImageRotation, isDisplayLocked?: boolean): void
```

设置预览旋转角度。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-PreviewOutput-setPreviewRotation(previewRotation: ImageRotation, isDisplayLocked?: boolean): void--><!--Device-PreviewOutput-setPreviewRotation(previewRotation: ImageRotation, isDisplayLocked?: boolean): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| previewRotation | [ImageRotation](arkts-camera-camera-imagerotation-e.md) | 是 | 预览旋转角度 |
| isDisplayLocked | boolean | 否 | Surface在屏幕旋转时是否锁定方向，未设置时默认取值为false，即不锁定方向。true表示锁定方向，false表示不锁定方向。详情请参考 SurfaceRotationOptions |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

## start

```TypeScript
start(callback: AsyncCallback<void>): void
```

开始输出预览流，通过注册回调函数获取结果。使用callback异步回调。 > **说明：** > > 从 API version 10开始支持，从API version 11开始废弃。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** 11

**替代接口：** [start](arkts-camera-camera-session-i.md#start)(callback: AsyncCallback&lt;void&gt;)

<!--Device-PreviewOutput-start(callback: AsyncCallback<void>): void--><!--Device-PreviewOutput-start(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当开始输出预览流成功，err为undefined，否则为错误对象。错误码类型 [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md#CameraErrorCode)。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## start

```TypeScript
start(): Promise<void>
```

开始输出预览流。使用Promise异步回调。 > **说明：** > > 从 API version 10开始支持，从API version 11开始废弃。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** 11

**替代接口：** [start](arkts-camera-camera-session-i.md#start)()

<!--Device-PreviewOutput-start(): Promise<void>--><!--Device-PreviewOutput-start(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## stop

```TypeScript
stop(callback: AsyncCallback<void>): void
```

停止输出预览流，通过注册回调函数获取结果。使用callback异步回调。 > **说明：** > > 从 API version 10开始支持，从API version 11开始废弃。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** 11

**替代接口：** [stop](arkts-camera-camera-session-i.md#stop)(callback: AsyncCallback&lt;void&gt;)

<!--Device-PreviewOutput-stop(callback: AsyncCallback<void>): void--><!--Device-PreviewOutput-stop(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当停止输出预览流成功，err为undefined，否则为错误对象。 |

## stop

```TypeScript
stop(): Promise<void>
```

停止输出预览流。使用Promise异步回调。 > **说明：** > > 从 API version 10开始支持，从API version 11开始废弃。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** 11

**替代接口：** [stop](arkts-camera-camera-session-i.md#stop)()

<!--Device-PreviewOutput-stop(): Promise<void>--><!--Device-PreviewOutput-stop(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

