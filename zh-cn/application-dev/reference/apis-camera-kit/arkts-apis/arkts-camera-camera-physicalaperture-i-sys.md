# PhysicalAperture（系统接口）

物理光圈对象。

**起始版本：** 23

<!--Device-camera-interface PhysicalAperture--><!--Device-camera-interface PhysicalAperture-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
import { cameraPicker } from '@kit.CameraKit';
```

## apertures

```TypeScript
apertures: Array<double>
```

支持的物理光圈值。

**类型：** Array&lt;double&gt;

**起始版本：** 23

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-PhysicalAperture-apertures: Array<double>--><!--Device-PhysicalAperture-apertures: Array<double>-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## zoomRange

```TypeScript
zoomRange: ZoomRange
```

特定物理光圈的变焦范围。

**类型：** [ZoomRange](arkts-camera-camera-zoomrange-i-sys.md)

**起始版本：** 23

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-PhysicalAperture-zoomRange: ZoomRange--><!--Device-PhysicalAperture-zoomRange: ZoomRange-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

