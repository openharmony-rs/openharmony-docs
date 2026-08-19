# CapturePhoto

获取全质量图和未压缩图的对象。

**起始版本：** 23

<!--Device-camera-interface CapturePhoto--><!--Device-camera-interface CapturePhoto-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
import { cameraPicker } from '@kit.CameraKit';
```

## release

```TypeScript
release(): Promise<void>
```

释放输出资源。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-CapturePhoto-release(): Promise<void>--><!--Device-CapturePhoto-release(): Promise<void>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

## main

```TypeScript
main: ImageType
```

全质量图和未压缩图的对象。

**类型：** [ImageType](arkts-camera-camera-imagetype-t.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-CapturePhoto-main: ImageType--><!--Device-CapturePhoto-main: ImageType-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

