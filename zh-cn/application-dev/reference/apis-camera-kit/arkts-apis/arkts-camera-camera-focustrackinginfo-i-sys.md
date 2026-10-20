# FocusTrackingInfo（系统接口）

```TypeScript
interface FocusTrackingInfo
```

描述焦点跟踪信息，通过调用VideoSessionForSys的[on('focusTrackingInfoAvailable')](arkts-camera-camera-videosession-i-sys.md#onfocustrackinginfoavailable)获取。

**起始版本：** 15

<!--Device-camera-interface FocusTrackingInfo--><!--Device-camera-interface FocusTrackingInfo-End-->

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

跟踪模式。

**类型：** [FocusTrackingMode](arkts-camera-camera-focustrackingmode-e-sys.md)

**起始版本：** 15

<!--Device-FocusTrackingInfo-trackingMode: FocusTrackingMode--><!--Device-FocusTrackingInfo-trackingMode: FocusTrackingMode-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。

## trackingRegion

```TypeScript
trackingRegion: Rect
```

跟踪区域。

**类型：** [Rect](arkts-camera-camera-rect-i.md)

**起始版本：** 15

<!--Device-FocusTrackingInfo-trackingRegion: Rect--><!--Device-FocusTrackingInfo-trackingRegion: Rect-End-->

**系统能力：** SystemCapability.Multimedia.Camera.Core

**系统接口：** 此接口为系统接口。
