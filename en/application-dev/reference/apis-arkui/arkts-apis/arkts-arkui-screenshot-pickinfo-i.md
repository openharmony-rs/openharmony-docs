# PickInfo

```TypeScript
interface PickInfo
```

Describes the screenshot options.

**Since:** 12

<!--Device-screenshot-interface PickInfo--><!--Device-screenshot-interface PickInfo-End-->

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## Modules to Import

```TypeScript
import { screenshot } from '@kit.ArkUI';
```

## pickRect

```TypeScript
pickRect: Rect
```

Region of the screen to capture.

**Type:** [Rect](arkts-arkui-screenshot-rect-i.md)

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-PickInfo-pickRect: Rect--><!--Device-PickInfo-pickRect: Rect-End-->

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## pixelMap

```TypeScript
pixelMap: image.PixelMap
```

PixelMap object of the captured image.

**Type:** [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-PickInfo-pixelMap: image.PixelMap--><!--Device-PickInfo-pixelMap: image.PixelMap-End-->

**System capability:** SystemCapability.WindowManager.WindowManager.Core
