# SketchStatusData（系统接口）

```TypeScript
interface SketchStatusData
```

定义画中画状态数据。

**起始版本：** 11

<!--Device-camera-interface SketchStatusData--><!--Device-camera-interface SketchStatusData-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
```

## centerPointOffset

```TypeScript
centerPointOffset: Point
```

画中画偏移。

**类型：** [Point](arkts-camera-camera-point-i.md)

**起始版本：** 20

<!--Device-SketchStatusData-centerPointOffset: Point--><!--Device-SketchStatusData-centerPointOffset: Point-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## sketchRatio

```TypeScript
sketchRatio: number
```

画中画变焦比。

**类型：** number

**起始版本：** 11

<!--Device-SketchStatusData-sketchRatio: double--><!--Device-SketchStatusData-sketchRatio: double-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## status

```TypeScript
status: number
```

画中画状态。取值为0（已停止）、1（已开始）、2（正在停止）、3（正在开始）。

**类型：** number

**起始版本：** 11

<!--Device-SketchStatusData-status: int--><!--Device-SketchStatusData-status: int-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。
