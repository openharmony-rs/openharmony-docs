# FrameShutterInfo

```TypeScript
interface FrameShutterInfo
```

Describes the frame shutter information.

**Since:** 10

<!--Device-camera-interface FrameShutterInfo--><!--Device-camera-interface FrameShutterInfo-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

## Modules to Import

```TypeScript
import { camera } from '@kit.CameraKit';
```

## captureId

```TypeScript
captureId: number
```

ID of this capture action.

**Type:** number

**Since:** 10

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 19.

<!--Device-FrameShutterInfo-captureId: int--><!--Device-FrameShutterInfo-captureId: int-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core

## timestamp

```TypeScript
timestamp: number
```

Timestamp when the frame shutter event is triggered, in milliseconds.

**Type:** number

**Since:** 10

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 19.

<!--Device-FrameShutterInfo-timestamp: long--><!--Device-FrameShutterInfo-timestamp: long-End-->

**System capability:** SystemCapability.Multimedia.Camera.Core
