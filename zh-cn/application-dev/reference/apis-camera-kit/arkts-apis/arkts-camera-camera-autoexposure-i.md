# AutoExposure

AutoExposure继承自[AutoExposureQuery](arkts-camera-camera-autoexposurequery-i.md#AutoExposureQuery)。 自动曝光类，对设备自动曝光（AE）操作。

**继承/实现关系：** AutoExposure extends [AutoExposureQuery](arkts-camera-camera-autoexposurequery-i.md#AutoExposureQuery)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-camera-interface AutoExposure--><!--Device-camera-interface AutoExposure-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## getExposureMode

```TypeScript
getExposureMode(): ExposureMode
```

获取当前曝光模式。 > **说明：** > > 若未通过[setExposureMode](#setExposureMode)接口进行设置，直接调用该接口查询当前曝光模式，会返回无效值。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-AutoExposure-getExposureMode(): ExposureMode--><!--Device-AutoExposure-getExposureMode(): ExposureMode-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ExposureMode](arkts-camera-camera-exposuremode-e.md) | 获取当前曝光模式。接口调用失败会抛出相应错误码并返回undefined，错误码类型 [CameraErrorCode]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## getExposureValue

```TypeScript
getExposureValue(): double
```

查询当前曝光值。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-AutoExposure-getExposureValue(): double--><!--Device-AutoExposure-getExposureValue(): double-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| double | 获取曝光值。曝光补偿存在步长，如步长为0.5。则设置1.2时，获取到实际生效曝光补偿为1.0。 &lt;br&gt;接口调用失败会返回相应错误码，错误码类型[CameraErrorCode]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## getMeteringPoint

```TypeScript
getMeteringPoint(): Point
```

查询曝光区域中心点。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-AutoExposure-getMeteringPoint(): Point--><!--Device-AutoExposure-getMeteringPoint(): Point-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Point | 获取当前曝光点。接口调用失败会返回相应错误码，错误码类型[CameraErrorCode]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## offExposureStateChange

```TypeScript
offExposureStateChange(callback?: Callback<ExposureState>): void
```

注销监听曝光状态事件变更。使用callback异步回调。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-AutoExposure-offExposureStateChange(callback?: Callback<ExposureState>): void--><!--Device-AutoExposure-offExposureStateChange(callback?: Callback<ExposureState>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[ExposureState](arkts-camera-camera-exposurestate-e.md)&gt; | 否 | 回调函数，如果指定参数则取消对应callback，callback对象如果为空或为匿名函数，则取消所有callback。 |

## onExposureStateChange

```TypeScript
onExposureStateChange(callback: Callback<ExposureState>): void
```

监听曝光状态事件变更。使用callback异步回调。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-AutoExposure-onExposureStateChange(callback: Callback<ExposureState>): void--><!--Device-AutoExposure-onExposureStateChange(callback: Callback<ExposureState>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[ExposureState](arkts-camera-camera-exposurestate-e.md)&gt; | 是 | 回调函数，返回当前曝光状态。 |

## setExposureBias

```TypeScript
setExposureBias(exposureBias: double): void
```

设置曝光补偿，曝光补偿值（EV）。 进行设置之前，建议先通过方法[getExposureBiasRange](arkts-camera-camera-autoexposurequery-i.md#getExposureBiasRange)查询支持的范围。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-AutoExposure-setExposureBias(exposureBias: double): void--><!--Device-AutoExposure-setExposureBias(exposureBias: double): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| exposureBias | double | 是 | 曝光补偿，[getExposureBiasRange](arkts-camera-camera-autoexposurequery-i.md#getExposureBiasRange) 查询支持的范围，如果设置超过支持范围的值，自动匹配到就近临界点。 &lt;br&gt;曝光补偿存在步长，由于设备差异，步长也存在差异。例如步长为0.5，则设置1.2时，获取到实际生效曝光补偿为1.0。 &lt;br&gt;接口调用失败会返回相应错误码，错误码类型[CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md#CameraErrorCode)。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed.<br>**适用版本：** 12+ |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## setExposureMode

```TypeScript
setExposureMode(aeMode: ExposureMode): void
```

设置曝光模式。进行设置之前，需要先检查设备是否支持指定的曝光模式，可使用方法 [isExposureModeSupported](arkts-camera-camera-autoexposurequery-i.md#isExposureModeSupported)。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-AutoExposure-setExposureMode(aeMode: ExposureMode): void--><!--Device-AutoExposure-setExposureMode(aeMode: ExposureMode): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| aeMode | [ExposureMode](arkts-camera-camera-exposuremode-e.md) | 是 | 曝光模式。传参为null或者undefined，作为0处理，曝光锁定。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400102](../errorcode-camera.md#7400102-非法操作) | Operation not allowed.<br>**适用版本：** 19+ |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## setMeteringPoint

```TypeScript
setMeteringPoint(point: Point): void
```

设置曝光区域中心点，曝光点应在0-1坐标系内，该坐标系左上角为{0，0}，右下角为{1，1}。 此坐标系是以设备充电口在右侧时的横向设备方向为基准的，例如应用的预览界面布局以设备充电口在下侧时的竖向方向为基准，布局宽高为{w，h}，且触摸点为{x，y}，则转换后的坐标点为{y/h，1-x/w}。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-AutoExposure-setMeteringPoint(point: Point): void--><!--Device-AutoExposure-setMeteringPoint(point: Point): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| point | Point | 是 | 曝光点，x、y设置范围应在[0，1]之内，超过范围，如果小于0设置0，大于1设置1。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

