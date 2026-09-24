# ImageItem (System API)

```TypeScript
interface ImageItem
```

Image information for AI-generated images.

@interface ImageItem

**Since:** 23

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { imageGeneration } from '@kit.ArkUI';
```

## image

```TypeScript
image?: image.PixelMap
```

Image decoding information for preview in the page of ImageGeneratorDialog.

<p>**NOTE:**  Displayed within the canvas in the ImageGeneratorDialog; if not provided, the image will be decoded from the url. </p>

**Type:** [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## isHandwrite

```TypeScript
isHandwrite?: boolean
```

whether the image type is a hand-drawn line art.

<p>**NOTE:**  it is recommended to be provided in Hand-drawn line art scenarios to achieve better results. </p>

**Type:** boolean

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## rect

```TypeScript
rect?: common2D.Rect
```

The size and position of the container used to display images in the preview canvas.

<p>**NOTE:**  it is recommended to be provided in multi-image fusion scenarios to achieve better results. </p>

**Type:** [common2D.Rect](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-common2d-rect-i.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## rotation

```TypeScript
rotation?: componentUtils.Rotation2D
```

The rotation of the container used to display images in the preview canvas.

<p>**NOTE:**  it is recommended to be provided in multi-image fusion scenarios to achieve better results. </p>

**Type:** [componentUtils.Rotation2D](arkts-arkui-componentutils-rotation2d-i-sys.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## url

```TypeScript
url?: ResourceStr
```

Original image path information for image generation;

<p>**NOTE:**  for high-resolution scenarios, it is best to provide the original image path; if not provided, the image.PixelMap will be used for image generation. </p>

**Type:** [ResourceStr](arkts-arkui-resourcestr-t.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## zIndex

```TypeScript
zIndex?: number
```

In scenarios with multiple images, information about image rendering hierarchy.

<p>**NOTE:**  it is recommended to be provided in multi-image fusion scenarios to achieve better results. </p>

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
