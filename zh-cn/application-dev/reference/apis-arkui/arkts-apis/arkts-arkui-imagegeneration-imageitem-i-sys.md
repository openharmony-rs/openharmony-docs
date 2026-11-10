# ImageItem（系统接口）

```TypeScript
interface ImageItem
```

AI生成图像的图像信息。

**起始版本：** 23

<!--Device-imageGeneration-interface ImageItem--><!--Device-imageGeneration-interface ImageItem-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { imageGeneration } from '@kit.ArkUI';
```

## image

```TypeScript
image?: image.PixelMap
```

ImageGeneratorDialog页面中预览的图片解码信息。

<p>**注意**：在ImageGeneratorDialog中画布内显示；如果未提供该参数，则将从URL解码图像。</p>

**类型：** [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageItem-image?: image.PixelMap--><!--Device-ImageItem-image?: image.PixelMap-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## isHandwrite

```TypeScript
isHandwrite?: boolean
```

图像类型是否为手绘线条艺术。

<p>**注意**：建议在手绘线稿场景中使用，以获得更好的效果。&lt;/p

**类型：** boolean

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageItem-isHandwrite?: boolean--><!--Device-ImageItem-isHandwrite?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## rect

```TypeScript
rect?: common2D.Rect
```

用于在预览画布中显示图像的容器的大小和位置。

建议在多图像融合场景中提供该功能，以获得更好的效果。

**类型：** [common2D.Rect](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-common2d-rect-i.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageItem-rect?: common2D.Rect--><!--Device-ImageItem-rect?: common2D.Rect-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## rotation

```TypeScript
rotation?: componentUtils.Rotation2D
```

The rotation of the container used to display images in the preview canvas.

建议在多图像融合场景中提供该功能，以获得更好的效果。

**类型：** [componentUtils.Rotation2D](arkts-arkui-componentutils-rotation2d-i-sys.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageItem-rotation?: componentUtils.Rotation2D--><!--Device-ImageItem-rotation?: componentUtils.Rotation2D-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## url

```TypeScript
url?: ResourceStr
```

图像生成的原始图像路径信息；

<p>**注意**：对于高分辨率场景，最好提供原始图像路径；如果未提供，则将使用 image.PixelMap 进行图像生成。</p>

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageItem-url?: ResourceStr--><!--Device-ImageItem-url?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## zIndex

```TypeScript
zIndex?: number
```

在多图像场景中，关于图像渲染层次结构的信息。

<p>**注意**：建议在多图像融合场景中使用，以获得更好的效果。&lt;/p

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageItem-zIndex?: int--><!--Device-ImageItem-zIndex?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。
