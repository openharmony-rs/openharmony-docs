# CaptureSession

拍照会话类，保存一次相机运行所需要的所有资源[CameraInput](arkts-camera-camera-camerainput-i.md#CameraInput)、[CameraOutput](arkts-camera-camera-cameraoutput-i.md#CameraOutput)，并向相机设备申请完成相 机功能(录像，拍照)。 > **说明：** > > 从 API version 10开始支持，从API version 11开始废弃。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** 11

**替代接口：** [VideoSession](arkts-camera-camera-videosession-i.md#VideoSession)

<!--Device-camera-interface CaptureSession--><!--Device-camera-interface CaptureSession-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## addInput

```TypeScript
addInput(cameraInput: CameraInput): void
```

把[CameraInput](arkts-camera-camera-camerainput-i.md#CameraInput)加入到会话。 > **说明：** > > 从 API version 10开始支持，从API version 11开始废弃。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** 11

**替代接口：** [addInput](arkts-camera-camera-session-i.md#addInput)

<!--Device-CaptureSession-addInput(cameraInput: CameraInput): void--><!--Device-CaptureSession-addInput(cameraInput: CameraInput): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| cameraInput | [CameraInput](arkts-camera-camera-camerainput-i.md) | 是 | 需要添加的CameraInput实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed. |

## addOutput

```TypeScript
addOutput(cameraOutput: CameraOutput): void
```

把[CameraOutput](arkts-camera-camera-cameraoutput-i.md#CameraOutput)加入到会话。 > **说明：** > > 从 API version 10开始支持，从API version 11开始废弃。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** 11

**替代接口：** [addOutput](arkts-camera-camera-session-i.md#addOutput)

<!--Device-CaptureSession-addOutput(cameraOutput: CameraOutput): void--><!--Device-CaptureSession-addOutput(cameraOutput: CameraOutput): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| cameraOutput | [CameraOutput](arkts-camera-camera-cameraoutput-i.md) | 是 | 需要添加的CameraOutput实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed. |

## beginConfig

```TypeScript
beginConfig(): void
```

开始配置会话。 > **说明：** > > 从 API version 10开始支持，从API version 11开始废弃。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** 11

**替代接口：** [beginConfig](arkts-camera-camera-session-i.md#beginConfig)

<!--Device-CaptureSession-beginConfig(): void--><!--Device-CaptureSession-beginConfig(): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400105](../errorcode-camera.md#7400105-会话配置被锁定) | Session config locked. |

## commitConfig

```TypeScript
commitConfig(callback: AsyncCallback<void>): void
```

提交配置信息，通过注册回调函数获取结果。使用callback异步回调。 > **说明：** > > 从 API version 10开始支持，从API version 11开始废弃。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** 11

**替代接口：** [commitConfig](arkts-camera-camera-session-i.md#commitConfig)(callback: AsyncCallback&lt;void&gt;)

<!--Device-CaptureSession-commitConfig(callback: AsyncCallback<void>): void--><!--Device-CaptureSession-commitConfig(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当提交配置信息成功，err为undefined，否则为错误对象。错误码类型 [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md#CameraErrorCode) |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

## commitConfig

```TypeScript
commitConfig(): Promise<void>
```

提交配置信息。使用Promise异步回调。 > **说明：** > > 从 API version 10开始支持，从API version 11开始废弃。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** 11

**替代接口：** [commitConfig](arkts-camera-camera-session-i.md#commitConfig)()

<!--Device-CaptureSession-commitConfig(): Promise<void>--><!--Device-CaptureSession-commitConfig(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

## getActiveVideoStabilizationMode

```TypeScript
getActiveVideoStabilizationMode(): VideoStabilizationMode
```

查询当前正在使用的视频防抖模式。 > **说明：** > > 从 API version 10开始支持，从API version 11开始废弃。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** 11

**替代接口：** [getActiveVideoStabilizationMode](arkts-camera-camera-stabilization-i.md#getActiveVideoStabilizationMode)

<!--Device-CaptureSession-getActiveVideoStabilizationMode(): VideoStabilizationMode--><!--Device-CaptureSession-getActiveVideoStabilizationMode(): VideoStabilizationMode-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [VideoStabilizationMode](arkts-camera-camera-videostabilizationmode-e.md) | 视频防抖是否正在使用。接口调用失败会返回相应错误码，错误码类型 [CameraErrorCode]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## getExposureBiasRange

```TypeScript
getExposureBiasRange(): Array<number>
```

查询曝光补偿范围。 > **说明：** > > 从 API version 10开始支持，从API version 11开始废弃。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** 11

**替代接口：** [getExposureBiasRange](arkts-camera-camera-autoexposurequery-i.md#getExposureBiasRange)

<!--Device-CaptureSession-getExposureBiasRange(): Array<number>--><!--Device-CaptureSession-getExposureBiasRange(): Array<number>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;number&gt; | 获取补偿范围的数组。接口调用失败会返回相应错误码，错误码类型[CameraErrorCode]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## getExposureMode

```TypeScript
getExposureMode(): ExposureMode
```

获取当前曝光模式。 > **说明：** > > 从 API version 10开始支持，从API version 11开始废弃。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** 11

**替代接口：** [getExposureMode](arkts-camera-camera-autoexposure-i.md#getExposureMode)

<!--Device-CaptureSession-getExposureMode(): ExposureMode--><!--Device-CaptureSession-getExposureMode(): ExposureMode-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ExposureMode](arkts-camera-camera-exposuremode-e.md) | 获取当前曝光模式。接口调用失败会返回相应错误码，错误码类型[CameraErrorCode]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## getExposureValue

```TypeScript
getExposureValue(): number
```

查询当前的曝光值。 > **说明：** > > 从 API version 10开始支持，从API version 11开始废弃。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** 11

**替代接口：** [getExposureValue](arkts-camera-camera-autoexposure-i.md#getExposureValue)

<!--Device-CaptureSession-getExposureValue(): number--><!--Device-CaptureSession-getExposureValue(): number-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 获取曝光值。曝光补偿存在步长，如步长为0.5。则设置1.2时，获取到实际生效曝光补偿为1.0。接口调用失败会返回相应错误码，错误码类型 [CameraErrorCode]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## getFlashMode

```TypeScript
getFlashMode(): FlashMode
```

获取当前设备的闪光灯模式。 > **说明：** > > 从 API version 10开始支持，从API version 11开始废弃。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** 11

**替代接口：** [getFlashMode](arkts-camera-camera-flash-i.md#getFlashMode)

<!--Device-CaptureSession-getFlashMode(): FlashMode--><!--Device-CaptureSession-getFlashMode(): FlashMode-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FlashMode](arkts-camera-camera-flashmode-e.md) | 获取当前设备的闪光灯模式。接口调用失败会返回相应错误码，错误码类型[CameraErrorCode]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## getFocalLength

```TypeScript
getFocalLength(): number
```

查询焦距值。 > **说明：** > > 从 API version 10开始支持，从API version 11开始废弃。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** 11

**替代接口：** [getFocalLength](arkts-camera-camera-focus-i.md#getFocalLength)

<!--Device-CaptureSession-getFocalLength(): number--><!--Device-CaptureSession-getFocalLength(): number-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 用于获取当前焦距。接口调用失败会返回相应错误码，错误码类型[CameraErrorCode]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## getFocusMode

```TypeScript
getFocusMode(): FocusMode
```

获取当前的对焦模式。 > **说明：** > > 从 API version 10开始支持，从API version 11开始废弃。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** 11

**替代接口：** [getFocusMode](arkts-camera-camera-focus-i.md#getFocusMode)

<!--Device-CaptureSession-getFocusMode(): FocusMode--><!--Device-CaptureSession-getFocusMode(): FocusMode-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| FocusMode | 获取当前设备的焦距模式。接口调用失败会返回相应错误码，错误码类型[CameraErrorCode]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## getFocusPoint

```TypeScript
getFocusPoint(): Point
```

查询焦点。 > **说明：** > > 从 API version 10开始支持，从API version 11开始废弃。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** 11

**替代接口：** [getFocusPoint](arkts-camera-camera-focus-i.md#getFocusPoint)

<!--Device-CaptureSession-getFocusPoint(): Point--><!--Device-CaptureSession-getFocusPoint(): Point-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Point | 用于获取当前焦点。接口调用失败会返回相应错误码，错误码类型[CameraErrorCode]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## getMeteringPoint

```TypeScript
getMeteringPoint(): Point
```

查询曝光区域中心点。 > **说明：** > > 从 API version 10开始支持，从API version 11开始废弃。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** 11

**替代接口：** [getMeteringPoint](arkts-camera-camera-autoexposure-i.md#getMeteringPoint)

<!--Device-CaptureSession-getMeteringPoint(): Point--><!--Device-CaptureSession-getMeteringPoint(): Point-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Point | 获取当前曝光点。接口调用失败会返回相应错误码，错误码类型[CameraErrorCode]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## getZoomRatio

```TypeScript
getZoomRatio(): number
```

获取当前的变焦比。 > **说明：** > > 从 API version 10开始支持，从API version 11开始废弃。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** 11

**替代接口：** [getZoomRatio](arkts-camera-camera-zoom-i.md#getZoomRatio)

<!--Device-CaptureSession-getZoomRatio(): number--><!--Device-CaptureSession-getZoomRatio(): number-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 获取当前的变焦比结果。接口调用失败会返回相应错误码，错误码类型[CameraErrorCode]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## getZoomRatioRange

```TypeScript
getZoomRatioRange(): Array<number>
```

获取支持的变焦范围。 > **说明：** > > 从 API version 10开始支持，从API version 11开始废弃。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** 11

**替代接口：** [getZoomRatioRange](arkts-camera-camera-zoomquery-i.md#getZoomRatioRange)

<!--Device-CaptureSession-getZoomRatioRange(): Array<number>--><!--Device-CaptureSession-getZoomRatioRange(): Array<number>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;number&gt; | 用于获取可变焦距比范围，返回的数组包括其最小值和最大值。接口调用失败会返回相应错误码，错误码类型 [CameraErrorCode]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## hasFlash

```TypeScript
hasFlash(): boolean
```

检测是否有闪光灯。 > **说明：** > > 从 API version 10开始支持，从API version 11开始废弃。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** 11

**替代接口：** [hasFlash](arkts-camera-camera-flashquery-i.md#hasFlash)

<!--Device-CaptureSession-hasFlash(): boolean--><!--Device-CaptureSession-hasFlash(): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 设备支持闪光灯。true表示支持，false表示不支持。接口调用失败会返回相应错误码，错误码类型 [CameraErrorCode]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## isExposureModeSupported

```TypeScript
isExposureModeSupported(aeMode: ExposureMode): boolean
```

查询曝光模式是否支持。 > **说明：** > > 从 API version 10开始支持，从API version 11开始废弃。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** 11

**替代接口：** [isExposureModeSupported](arkts-camera-camera-autoexposurequery-i.md#isExposureModeSupported)

<!--Device-CaptureSession-isExposureModeSupported(aeMode: ExposureMode): boolean--><!--Device-CaptureSession-isExposureModeSupported(aeMode: ExposureMode): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| aeMode | [ExposureMode](arkts-camera-camera-exposuremode-e.md) | 是 | 曝光模式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 获取是否支持曝光模式。true表示支持，false表示不支持。接口调用失败会返回相应错误码，错误码类型 [CameraErrorCode]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## isFlashModeSupported

```TypeScript
isFlashModeSupported(flashMode: FlashMode): boolean
```

检测闪光灯模式是否支持。 > **说明：** > > 从 API version 10开始支持，从API version 11开始废弃。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** 11

**替代接口：** [isFlashModeSupported](arkts-camera-camera-flashquery-i.md#isFlashModeSupported)

<!--Device-CaptureSession-isFlashModeSupported(flashMode: FlashMode): boolean--><!--Device-CaptureSession-isFlashModeSupported(flashMode: FlashMode): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| flashMode | [FlashMode](arkts-camera-camera-flashmode-e.md) | 是 | 指定闪光灯模式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 检测闪光灯模式是否支持。true表示支持，false表示不支持。接口调用失败会返回相应错误码，错误码类型 [CameraErrorCode]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## isFocusModeSupported

```TypeScript
isFocusModeSupported(afMode: FocusMode): boolean
```

查询对焦模式是否支持。 > **说明：** > > 从 API version 10开始支持，从API version 11开始废弃。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** 11

**替代接口：** [isFocusModeSupported](arkts-camera-camera-focusquery-i.md#isFocusModeSupported)

<!--Device-CaptureSession-isFocusModeSupported(afMode: FocusMode): boolean--><!--Device-CaptureSession-isFocusModeSupported(afMode: FocusMode): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| afMode | FocusMode | 是 | 指定的焦距模式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 检测对焦模式是否支持。true表示支持，false表示不支持。接口调用失败会返回相应错误码，错误码类型 [CameraErrorCode]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## isVideoStabilizationModeSupported

```TypeScript
isVideoStabilizationModeSupported(vsMode: VideoStabilizationMode): boolean
```

查询是否支持指定的视频防抖模式。 > **说明：** > > 从 API version 10开始支持，从API version 11开始废弃。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** 11

**替代接口：** [isVideoStabilizationModeSupported](arkts-camera-camera-stabilizationquery-i.md#isVideoStabilizationModeSupported)

<!--Device-CaptureSession-isVideoStabilizationModeSupported(vsMode: VideoStabilizationMode): boolean--><!--Device-CaptureSession-isVideoStabilizationModeSupported(vsMode: VideoStabilizationMode): boolean-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| vsMode | [VideoStabilizationMode](arkts-camera-camera-videostabilizationmode-e.md) | 是 | 视频防抖模式。传参为null或者undefined，作为0处理，超级防抖模式关闭。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回视频防抖模式是否支持。true表示支持，false表示不支持。接口调用失败会返回相应错误码，错误码类型 [CameraErrorCode]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## off_error

```TypeScript
off(type: 'error', callback?: ErrorCallback): void
```

注销监听拍照会话的错误事件，通过注册回调函数获取结果。 > **说明：** > > 从 API version 10开始支持，从API version 11开始废弃。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** 11

**替代接口：** [off](arkts-camera-camera-videosession-i.md#off_error)(type: 'error', callback?: ErrorCallback)

<!--Device-CaptureSession-off(type: 'error', callback?: ErrorCallback): void--><!--Device-CaptureSession-off(type: 'error', callback?: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 监听事件，固定为'error'，session创建成功之后可监听该接口。 |
| callback | [ErrorCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-errorcallback-t.md) | 否 | 回调函数，如果指定参数则取消对应callback（callback对象不可是匿名函数），否则取消所有callback。 |

## off_focusStateChange

```TypeScript
off(type: 'focusStateChange', callback?: AsyncCallback<FocusState>): void
```

注销监听相机聚焦的状态变化。 > **说明：** > > 从 API version 10开始支持，从API version 11开始废弃。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** 11

**替代接口：** [off](arkts-camera-camera-videosession-i.md#off_error)(type: 'focusStateChange', callback?: AsyncCallback&lt;FocusState&gt;)

<!--Device-CaptureSession-off(type: 'focusStateChange', callback?: AsyncCallback<FocusState>): void--><!--Device-CaptureSession-off(type: 'focusStateChange', callback?: AsyncCallback<FocusState>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'focusStateChange' | 是 | 监听事件，固定为'focusStateChange'，session 创建成功可监听。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[FocusState](arkts-camera-camera-focusstate-e.md)&gt; | 否 | 回调函数，如果指定参数则取消对应callback（callback对象不可是匿名函数），否则取消所有callback。 |

## on_error

```TypeScript
on(type: 'error', callback: ErrorCallback): void
```

监听拍照会话的错误事件，通过注册回调函数获取结果。使用callback异步回调。 > **说明：** > > 当前注册监听接口，不支持在on监听的回调方法里，调用off注销回调。 > > 从 API version 10开始支持，从API version 11开始废弃。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** 11

**替代接口：** [on](arkts-camera-camera-videosession-i.md#on_error)(type: 'error', callback: ErrorCallback)

<!--Device-CaptureSession-on(type: 'error', callback: ErrorCallback): void--><!--Device-CaptureSession-on(type: 'error', callback: ErrorCallback): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'error' | 是 | 监听事件，固定为'error'，session创建成功之后可监听该接口。session调用相关接口出现错误时会触发该事件，比如调用 [beginConfig](#beginConfig)， [commitConfig](#commitConfig)，[addInput](#addInput)等接 口发生错误时返回错误信息。 |
| callback | [ErrorCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-errorcallback-t.md) | 是 | 回调函数，用于获取错误信息。返回错误码，错误码类型[CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md#CameraErrorCode)。 |

## on_focusStateChange

```TypeScript
on(type: 'focusStateChange', callback: AsyncCallback<FocusState>): void
```

监听相机聚焦的状态变化，通过注册回调函数获取结果。使用callback异步回调。 > **说明：** > > 从 API version 10开始支持，从API version 11开始废弃。 > > 当前注册监听接口，不支持在on监听的回调方法里，调用off注销回调。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** 11

**替代接口：** [on](arkts-camera-camera-videosession-i.md#on_error)(type: 'focusStateChange', callback: AsyncCallback&lt;FocusState&gt;)

<!--Device-CaptureSession-on(type: 'focusStateChange', callback: AsyncCallback<FocusState>): void--><!--Device-CaptureSession-on(type: 'focusStateChange', callback: AsyncCallback<FocusState>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'focusStateChange' | 是 | 监听事件，固定为'focusStateChange'，session 创建成功可监听。仅当自动对焦模式时,且相机对焦状态发生改变时可触发该事件。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[FocusState](arkts-camera-camera-focusstate-e.md)&gt; | 是 | 回调函数，用于获取当前对焦状态。 |

## release

```TypeScript
release(callback: AsyncCallback<void>): void
```

释放会话资源，通过注册回调函数获取结果。使用callback异步回调。 > **说明：** > > 从 API version 10开始支持，从API version 11开始废弃。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** 11

**替代接口：** [release](arkts-camera-camera-session-i.md#release)(callback: AsyncCallback&lt;void&gt;)

<!--Device-CaptureSession-release(callback: AsyncCallback<void>): void--><!--Device-CaptureSession-release(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当释放会话资源成功，err为undefined，否则为错误对象。错误码类型 [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md#CameraErrorCode)。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

## release

```TypeScript
release(): Promise<void>
```

释放会话资源。使用Promise异步回调。 > **说明：** > > 从 API version 10开始支持，从API version 11开始废弃。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** 11

**替代接口：** [release](arkts-camera-camera-session-i.md#release)()

<!--Device-CaptureSession-release(): Promise<void>--><!--Device-CaptureSession-release(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

## removeInput

```TypeScript
removeInput(cameraInput: CameraInput): void
```

移除[CameraInput](arkts-camera-camera-camerainput-i.md#CameraInput)。 > **说明：** > > 从 API version 10开始支持，从API version 11开始废弃。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** 11

**替代接口：** [removeInput](arkts-camera-camera-session-i.md#removeInput)

<!--Device-CaptureSession-removeInput(cameraInput: CameraInput): void--><!--Device-CaptureSession-removeInput(cameraInput: CameraInput): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| cameraInput | [CameraInput](arkts-camera-camera-camerainput-i.md) | 是 | 需要移除的CameraInput实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed. |

## removeOutput

```TypeScript
removeOutput(cameraOutput: CameraOutput): void
```

从会话中移除[CameraOutput](arkts-camera-camera-cameraoutput-i.md#CameraOutput)。 > **说明：** > > 从 API version 10开始支持，从API version 11开始废弃。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** 11

**替代接口：** [removeOutput](arkts-camera-camera-session-i.md#removeOutput)

<!--Device-CaptureSession-removeOutput(cameraOutput: CameraOutput): void--><!--Device-CaptureSession-removeOutput(cameraOutput: CameraOutput): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| cameraOutput | [CameraOutput](arkts-camera-camera-cameraoutput-i.md) | 是 | 需要移除的CameraOutput实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400101](../errorcode-camera.md#7400101-无效入参) | Parameter missing or parameter type incorrect. |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed. |

## setExposureBias

```TypeScript
setExposureBias(exposureBias: number): void
```

设置曝光补偿，曝光补偿值（EV）。 进行设置之前，建议先通过方法[getExposureBiasRange](#getExposureBiasRange)查询支持的范围。 > **说明：** > > 从 API version 10开始支持，从API version 11开始废弃。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** 11

**替代接口：** [setExposureBias](arkts-camera-camera-autoexposure-i.md#setExposureBias)

<!--Device-CaptureSession-setExposureBias(exposureBias: number): void--><!--Device-CaptureSession-setExposureBias(exposureBias: number): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| exposureBias | number | 是 | 曝光补偿，[getExposureBiasRange](arkts-camera-camera-autoexposurequery-i.md#getExposureBiasRange) 查询支持的范围，如果设置超过支持范围的值，自动匹配到就近临界点。曝光补偿存在步长，如步长为0.5。则设置1.2时，获取到实际生效曝光补偿为1.0。接口调用失败会返回相应错误码，错误码类型 [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md#CameraErrorCode)。传参为null或者undefined，作为0处理，曝光补偿设置0。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## setExposureMode

```TypeScript
setExposureMode(aeMode: ExposureMode): void
```

设置曝光模式。进行设置之前，需要先检查设备是否支持指定的曝光模式，可使用方法 [isExposureModeSupported](#isExposureModeSupported)。 > **说明：** > > 从 API version 10开始支持，从API version 11开始废弃。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** 11

**替代接口：** [setExposureMode](arkts-camera-camera-autoexposure-i.md#setExposureMode)

<!--Device-CaptureSession-setExposureMode(aeMode: ExposureMode): void--><!--Device-CaptureSession-setExposureMode(aeMode: ExposureMode): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| aeMode | [ExposureMode](arkts-camera-camera-exposuremode-e.md) | 是 | 曝光模式。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## setFlashMode

```TypeScript
setFlashMode(flashMode: FlashMode): void
```

设置闪光灯模式。 进行设置之前，需要先检查： 1. 设备是否支持闪光灯，可使用方法[hasFlash](#hasFlash)。 2. 设备是否支持指定的闪光灯模式，可使用方法[isFlashModeSupported](#isFlashModeSupported)。 > **说明：** > > 从 API version 10开始支持，从API version 11开始废弃。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** 11

**替代接口：** [setFlashMode](arkts-camera-camera-flash-i.md#setFlashMode)

<!--Device-CaptureSession-setFlashMode(flashMode: FlashMode): void--><!--Device-CaptureSession-setFlashMode(flashMode: FlashMode): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| flashMode | [FlashMode](arkts-camera-camera-flashmode-e.md) | 是 | 指定闪光灯模式。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## setFocusMode

```TypeScript
setFocusMode(afMode: FocusMode): void
```

设置对焦模式。 进行设置之前，需要先检查设备是否支持指定的焦距模式，可使用方法[isFocusModeSupported](#isFocusModeSupported)。 > **说明：** > > 从 API version 10开始支持，从API version 11开始废弃。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** 11

**替代接口：** [setFocusMode](arkts-camera-camera-focus-i.md#setFocusMode)

<!--Device-CaptureSession-setFocusMode(afMode: FocusMode): void--><!--Device-CaptureSession-setFocusMode(afMode: FocusMode): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| afMode | FocusMode | 是 | 指定的焦距模式。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## setFocusPoint

```TypeScript
setFocusPoint(point: Point): void
```

设置焦点，焦点应在0-1坐标系内，该坐标系左上角为{0，0}，右下角为{1，1}。 此坐标系是以设备充电口在右侧时的横向设备方向为基准的，例如应用的预览界面布局以设备充电口在下侧时的竖向方向为基准，布局宽高为{w，h}，且触碰点为{x，y}，则转换后的坐标点为{y/h，1-x/w}。 > **说明：** > > 从 API version 10开始支持，从API version 11开始废弃。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** 11

**替代接口：** [setFocusPoint](arkts-camera-camera-focus-i.md#setFocusPoint)

<!--Device-CaptureSession-setFocusPoint(point: Point): void--><!--Device-CaptureSession-setFocusPoint(point: Point): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| point | Point | 是 | 焦点。x,y设置范围应在[0,1]之内，超过范围，如果小于0设置0，大于1设置1。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## setMeteringPoint

```TypeScript
setMeteringPoint(point: Point): void
```

设置曝光区域中心点，曝光点应位于0-1坐标系内，该坐标系左上角为{0，0}，右下角为{1，1}。 此坐标系是以设备充电口在右侧时的横向设备方向为基准的，例如应用的预览界面布局以设备充电口在下侧时的竖向方向为基准，布局宽高为{w，h}，且触碰点为{x，y}，则转换后的坐标点为{y/h，1-x/w}。 > **说明：** > > 从 API version 10开始支持，从API version 11开始废弃。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** 11

**替代接口：** [setMeteringPoint](arkts-camera-camera-autoexposure-i.md#setMeteringPoint)

<!--Device-CaptureSession-setMeteringPoint(point: Point): void--><!--Device-CaptureSession-setMeteringPoint(point: Point): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| point | Point | 是 | 曝光点，x,y设置范围应在[0,1]之内，超过范围，如果小于0设置0，大于1设置1。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## setVideoStabilizationMode

```TypeScript
setVideoStabilizationMode(mode: VideoStabilizationMode): void
```

设置视频防抖模式。需要先检查设备是否支持对应的防抖模式，可以通过 [isVideoStabilizationModeSupported](#isVideoStabilizationModeSupported)方法判断所设置的模式是否支持。 > **说明：** > > 从 API version 10开始支持，从API version 11开始废弃。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** 11

**替代接口：** [setVideoStabilizationMode](arkts-camera-camera-stabilization-i.md#setVideoStabilizationMode)

<!--Device-CaptureSession-setVideoStabilizationMode(mode: VideoStabilizationMode): void--><!--Device-CaptureSession-setVideoStabilizationMode(mode: VideoStabilizationMode): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [VideoStabilizationMode](arkts-camera-camera-videostabilizationmode-e.md) | 是 | 需要设置的视频防抖模式。传参为null或者undefined，作为0处理，超级防抖模式关闭。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## setZoomRatio

```TypeScript
setZoomRatio(zoomRatio: number): void
```

设置变焦比，变焦精度最高为小数点后两位，如果设置超过支持的精度范围，则只保留精度范围内数值。 > **说明：** > > 从 API version 10开始支持，从API version 11开始废弃。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** 11

**替代接口：** [setZoomRatio](arkts-camera-camera-zoom-i.md#setZoomRatio)

<!--Device-CaptureSession-setZoomRatio(zoomRatio: number): void--><!--Device-CaptureSession-setZoomRatio(zoomRatio: number): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| zoomRatio | number | 是 | 可变焦距比，通过[getZoomRatioRange](arkts-camera-camera-zoomquery-i.md#getZoomRatioRange)获取支持的变焦范围，如果设置 超过支持范围的值，则只保留精度范围内数值。传参为null或者undefined，作为0处理，变焦设置最小值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## start

```TypeScript
start(callback: AsyncCallback<void>): void
```

开始会话工作，通过注册回调函数获取结果。使用callback异步回调。 > **说明：** > > 从 API version 10开始支持，从API version 11开始废弃。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** 11

**替代接口：** [start](arkts-camera-camera-session-i.md#start)(callback: AsyncCallback&lt;void&gt;)

<!--Device-CaptureSession-start(callback: AsyncCallback<void>): void--><!--Device-CaptureSession-start(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当开始会话工作成功，err为undefined，否则为错误对象。错误码类型 [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md#CameraErrorCode)。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

## start

```TypeScript
start(): Promise<void>
```

开始会话工作。使用Promise异步回调。 > **说明：** > > 从 API version 10开始支持，从API version 11开始废弃。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** 11

**替代接口：** [start](arkts-camera-camera-session-i.md#start)()

<!--Device-CaptureSession-start(): Promise<void>--><!--Device-CaptureSession-start(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

## stop

```TypeScript
stop(callback: AsyncCallback<void>): void
```

停止会话工作，通过注册回调函数获取结果。使用callback异步回调。 > **说明：** > > 从 API version 10开始支持，从API version 11开始废弃。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** 11

**替代接口：** [stop](arkts-camera-camera-session-i.md#stop)(callback: AsyncCallback&lt;void&gt;)

<!--Device-CaptureSession-stop(callback: AsyncCallback<void>): void--><!--Device-CaptureSession-stop(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当停止会话工作成功，err为undefined，否则为错误对象。错误码类型 [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md#CameraErrorCode)。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

## stop

```TypeScript
stop(): Promise<void>
```

停止会话工作。使用Promise异步回调。 > **说明：** > > 从 API version 10开始支持，从API version 11开始废弃。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** 11

**替代接口：** [stop](arkts-camera-camera-session-i.md#stop)()

<!--Device-CaptureSession-stop(): Promise<void>--><!--Device-CaptureSession-stop(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

