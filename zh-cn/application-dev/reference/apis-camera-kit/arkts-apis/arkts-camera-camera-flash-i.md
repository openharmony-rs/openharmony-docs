# Flash

Flash继承自[FlashQuery](arkts-camera-camera-flashquery-i.md#FlashQuery)。 闪光灯类，对设备闪光灯操作。

**继承/实现关系：** Flash extends [FlashQuery](arkts-camera-camera-flashquery-i.md#FlashQuery)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-camera-interface Flash--><!--Device-camera-interface Flash-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## getFlashMode

```TypeScript
getFlashMode(): FlashMode
```

获取当前设备的闪光灯模式。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-Flash-getFlashMode(): FlashMode--><!--Device-Flash-getFlashMode(): FlashMode-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FlashMode](arkts-camera-camera-flashmode-e.md) | 获取当前设备的闪光灯模式。接口调用失败会抛出相应错误码并返回undefined，错误码类型 [CameraErrorCode]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

## offFlashStateChange

```TypeScript
offFlashStateChange(callback?: Callback<FlashState>): void
```

取消订阅闪光灯状态变化事件回调。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-Flash-offFlashStateChange(callback?: Callback<FlashState>): void--><!--Device-Flash-offFlashStateChange(callback?: Callback<FlashState>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[FlashState](arkts-camera-camera-flashstate-e.md)&gt; | 否 | 回调函数，如果指定参数则取消对应callback（callback对象不可是匿名函数），否则取消所有callback。 |

## onFlashStateChange

```TypeScript
onFlashStateChange(callback: Callback<FlashState>): void
```

订阅闪光灯状态变化事件回调。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-Flash-onFlashStateChange(callback: Callback<FlashState>): void--><!--Device-Flash-onFlashStateChange(callback: Callback<FlashState>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[FlashState](arkts-camera-camera-flashstate-e.md)&gt; | 是 | 回调函数，用于获取闪光灯状态变化信息。 |

## setFlashMode

```TypeScript
setFlashMode(flashMode: FlashMode): void
```

设置闪光灯模式。 进行设置之前，需要先检查： 1. 设备是否支持闪光灯，可使用方法[hasFlash](arkts-camera-camera-flashquery-i.md#hasFlash)。 2. 设备是否支持指定的闪光灯模式，可使用方法[isFlashModeSupported](arkts-camera-camera-flashquery-i.md#isFlashModeSupported)。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-Flash-setFlashMode(flashMode: FlashMode): void--><!--Device-Flash-setFlashMode(flashMode: FlashMode): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| flashMode | [FlashMode](arkts-camera-camera-flashmode-e.md) | 是 | 指定闪光灯模式。传参为null或者undefined，作为0处理，闪光灯关闭。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400103](../errorcode-camera.md#7400103-会话未配置) | Session not config. |

