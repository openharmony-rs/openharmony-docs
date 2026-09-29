# ImageItem (System API)

```TypeScript
interface ImageItem
```

Image object with layout information.

@interface ImageItem

**Since:** 23

<!--Device-componentUtils-interface ImageItem--><!--Device-componentUtils-interface ImageItem-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { componentUtils } from '@kit.ArkUI';
```

## image

```TypeScript
image: image.PixelMap
```

Image Decoding Information.

**Type:** [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-ImageItem-image: image.PixelMap--><!--Device-ImageItem-image: image.PixelMap-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## rect

```TypeScript
rect: common2D.Rect
```

Information about the position and size of the box which displays the image.

**Type:** [common2D.Rect](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-common2d-rect-i.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-ImageItem-rect: common2D.Rect--><!--Device-ImageItem-rect: common2D.Rect-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## rotation

```TypeScript
rotation?: Rotation2D
```

Information about the rotation of the box which displays the image.

**Type:** [Rotation2D](arkts-arkui-componentutils-rotation2d-i-sys.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-ImageItem-rotation?: Rotation2D--><!--Device-ImageItem-rotation?: Rotation2D-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## zIndex

```TypeScript
zIndex: number
```

Information about image rendering hierarchy.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-ImageItem-zIndex: int--><!--Device-ImageItem-zIndex: int-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
