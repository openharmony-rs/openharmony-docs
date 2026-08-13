# CameraOutput

会话中[Session](arkts-camera-camera-session-i.md#Session)使用的输出信息，output的基类。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-camera-interface CameraOutput--><!--Device-camera-interface CameraOutput-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## release

```TypeScript
release(callback: AsyncCallback<void>): void
```

释放输出资源，通过注册回调函数获取结果。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-CameraOutput-release(callback: AsyncCallback<void>): void--><!--Device-CameraOutput-release(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当释放输出资源成功，err为undefined，否则为错误对象。错误码类型 [CameraErrorCode](arkts-camera-camera-cameraerrorcode-e.md#CameraErrorCode)。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

## release

```TypeScript
release(): Promise<void>
```

释放输出资源。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-CameraOutput-release(): Promise<void>--><!--Device-CameraOutput-release(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7400201](../errorcode-camera.md#7400201-相机服务异常) | Camera service fatal error. |

