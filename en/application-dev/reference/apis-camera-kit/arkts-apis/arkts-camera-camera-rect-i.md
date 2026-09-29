# Rect

```TypeScript
interface Rect
```

Describes a rectangle. The coordinate system for the returned detection points is based on the landscape device orientation, with the charging port on the right. In this coordinate system, the top-left corner is (0, 0), and the bottom-right corner is (1, 1). Here, **topLeftX** and **topLeftY** represent the coordinates of the top-left corner of the rectangle, whereas **width** and **height** represent the width and height of the rectangle, respectively. When cropping or selecting a face region based on specific requirements, the x and y coordinates of the rectangle must be multiplied by the width and height of the actual camera preview output stream to obtain the cropped face region.

The width and height of the actual preview stream refer to the resolution of the camera output stream. For details, see **size** in [profile](arkts-camera-camera-profile-i.md).

For details about how to obtain the preview stream data, see [Dual-Channel Preview (ArkTS)](../../../media/camera/camera-dual-channel-preview.md).

**Since:** 10

<!--Device-camera-interface Rect--><!--Device-camera-interface Rect-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

## Modules to Import

```TypeScript
import { camera } from '@kit.CameraKit';
```

## height

```TypeScript
height: number
```

Height of the rectangle, in the range of [0, 1].

**Type:** number

**Since:** 10

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 19.

<!--Device-Rect-height: double--><!--Device-Rect-height: double-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

## topLeftX

```TypeScript
topLeftX: number
```

X coordinate of the top-left corner of the rectangle, in the range of [0, 1].

**Type:** number

**Since:** 10

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 19.

<!--Device-Rect-topLeftX: double--><!--Device-Rect-topLeftX: double-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

## topLeftY

```TypeScript
topLeftY: number
```

Y coordinate of the top-left corner of the rectangle, in the range of [0, 1].

**Type:** number

**Since:** 10

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 19.

<!--Device-Rect-topLeftY: double--><!--Device-Rect-topLeftY: double-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

## width

```TypeScript
width: number
```

Width of the rectangle, in the range of [0, 1].

**Type:** number

**Since:** 10

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 19.

<!--Device-Rect-width: double--><!--Device-Rect-width: double-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core
