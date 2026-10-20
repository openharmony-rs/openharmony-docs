# EventCallbackInfo

```TypeScript
interface EventCallbackInfo
```

Defines the event callback information.

**Since:** 18

<!--Device-abilityConnectionManager-interface EventCallbackInfo--><!--Device-abilityConnectionManager-interface EventCallbackInfo-End-->

**System capability:** SystemCapability.DistributedSched.AppCollaboration

## Modules to Import

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
```

## image

```TypeScript
image?: image.PixelMap
```

Received image. If this parameter is not passed, it indicates that no image is received or the image information is unavailable.

**Type:** [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

<!--Device-EventCallbackInfo-image?: image.PixelMap--><!--Device-EventCallbackInfo-image?: image.PixelMap-End-->

**System capability:** SystemCapability.DistributedSched.AppCollaboration

**System API:** This is a system API.
