# ImageItem（系统接口）

带有布局信息的图像对象。

@interface ImageItem

**起始版本：** 23

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { componentUtils } from '@kit.ArkUI';
```

## image

```TypeScript
image: image.PixelMap
```

图像解码信息。

**类型：** [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## rect

```TypeScript
rect: common2D.Rect
```

显示图像的框的位置和大小信息。

**类型：** [common2D.Rect](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-common2d-rect-i.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## rotation

```TypeScript
rotation?: Rotation2D
```

显示图像的框的旋转信息。

**类型：** [Rotation2D](arkts-arkui-componentutils-rotation2d-i-sys.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## zIndex

```TypeScript
zIndex: number
```

图像渲染层次结构信息。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。
