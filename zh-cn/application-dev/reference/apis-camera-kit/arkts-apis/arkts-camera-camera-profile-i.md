# Profile

相机配置信息项。

**起始版本：** 23

<!--Device-camera-interface Profile--><!--Device-camera-interface Profile-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
import { cameraPicker } from '@kit.CameraKit';
```

## format

```TypeScript
readonly format: CameraFormat
```

输出格式。

**类型：** [CameraFormat](arkts-camera-camera-cameraformat-e.md)

**起始版本：** 23

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-Profile-readonly format: CameraFormat--><!--Device-Profile-readonly format: CameraFormat-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## size

```TypeScript
readonly size: Size
```

分辨率。 设置的是相机的分辨率宽度和高度，而非实际输出图像的宽度和高度。

**类型：** Size

**起始版本：** 23

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-Profile-readonly size: Size--><!--Device-Profile-readonly size: Size-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

