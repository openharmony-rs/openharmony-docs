# ImageItem（系统接口）

带有布局信息的图像对象。

**起始版本：** 23

<!--Device-componentUtils-interface ImageItem--><!--Device-componentUtils-interface ImageItem-End-->

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

**类型：** image.PixelMap

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageItem-image: image.PixelMap--><!--Device-ImageItem-image: image.PixelMap-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## rect

```TypeScript
rect: common2D.Rect
```

显示图像的框的位置和大小信息。

**类型：** common2D.Rect

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageItem-rect: common2D.Rect--><!--Device-ImageItem-rect: common2D.Rect-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## rotation

```TypeScript
rotation?: Rotation2D
```

显示图像的框的旋转信息。

**类型：** Rotation2D

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageItem-rotation?: Rotation2D--><!--Device-ImageItem-rotation?: Rotation2D-End-->

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

<!--Device-ImageItem-zIndex: int--><!--Device-ImageItem-zIndex: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

