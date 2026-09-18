# FocusTrackingInfo（系统接口）

Describes the focus tracking information, which is obtained by calling VideoSessionForSys. [on('focusTrackingInfoAvailable')](arkts-camera-camera-videosession-i-sys.md#onfocustrackinginfoavailable).

**起始版本：** 15

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { camera } from '@kit.CameraKit';
```

## trackingMode

```TypeScript
trackingMode: FocusTrackingMode
```

Tracing mode.

**类型：** [FocusTrackingMode](arkts-camera-camera-focustrackingmode-e-sys.md)

**起始版本：** 15

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## trackingRegion

```TypeScript
trackingRegion: Rect
```

Tracking region.

**类型：** [Rect](arkts-camera-camera-rect-i.md)

**起始版本：** 15

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。
