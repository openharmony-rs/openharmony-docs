# CapturePhoto

获取全质量图和未压缩图的对象。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-camera-interface CapturePhoto--><!--Device-camera-interface CapturePhoto-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## release

```TypeScript
release(): Promise<void>
```

Releases output resources. This API uses a promise to return the result. Model constraint: This API can be used only in the stage model.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-CapturePhoto-release(): Promise<void>--><!--Device-CapturePhoto-release(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

## main

```TypeScript
main: ImageType
```

Object of the full-quality image and the uncompressed image.

**类型：** ImageType

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-CapturePhoto-main: ImageType--><!--Device-CapturePhoto-main: ImageType-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

