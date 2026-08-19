# CaptureStartInfo

拍照开始信息。

**起始版本：** 23

<!--Device-camera-interface CaptureStartInfo--><!--Device-camera-interface CaptureStartInfo-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
import { cameraPicker } from '@kit.CameraKit';
```

## captureId

```TypeScript
captureId: int
```

拍照的ID。

**类型：** int

**起始版本：** 23

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-CaptureStartInfo-captureId: int--><!--Device-CaptureStartInfo-captureId: int-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

## time

```TypeScript
time: long
```

预估的单次拍照底层出sensor采集帧时间，如果上报-1，代表没有预估时间。

**类型：** long

**起始版本：** 23

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-CaptureStartInfo-time: long--><!--Device-CaptureStartInfo-time: long-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

