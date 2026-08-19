# ImageItem（系统接口）

Image object with layout information.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

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

Image Decoding Information.

**类型：** image.PixelMap

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageItem-image: image.PixelMap--><!--Device-ImageItem-image: image.PixelMap-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## rect

```TypeScript
rect: common2D.Rect
```

Information about the position and size of the box which displays the image.

**类型：** common2D.Rect

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageItem-rect: common2D.Rect--><!--Device-ImageItem-rect: common2D.Rect-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## rotation

```TypeScript
rotation?: Rotation2D
```

Information about the rotation of the box which displays the image.

**类型：** [Rotation2D](arkts-arkui-componentutils-rotation2d-i-sys.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageItem-rotation?: Rotation2D--><!--Device-ImageItem-rotation?: Rotation2D-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## zIndex

```TypeScript
zIndex: int
```

Information about image rendering hierarchy.

**类型：** int

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ImageItem-zIndex: int--><!--Device-ImageItem-zIndex: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

