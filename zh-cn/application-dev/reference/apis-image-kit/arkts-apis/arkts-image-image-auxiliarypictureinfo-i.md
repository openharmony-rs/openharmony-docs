# AuxiliaryPictureInfo

表示辅助图的图像信息。

**起始版本：** 13

<!--Device-image-interface AuxiliaryPictureInfo--><!--Device-image-interface AuxiliaryPictureInfo-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## 导入模块

```TypeScript
import { image } from '@kit.ImageKit';
```

## auxiliaryPictureType

```TypeScript
auxiliaryPictureType: AuxiliaryPictureType
```

辅助图的图像类型。

**类型：** AuxiliaryPictureType

**起始版本：** 13

<!--Device-AuxiliaryPictureInfo-auxiliaryPictureType: AuxiliaryPictureType--><!--Device-AuxiliaryPictureInfo-auxiliaryPictureType: AuxiliaryPictureType-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## colorSpace

```TypeScript
colorSpace: colorSpaceManager.ColorSpaceManager
```

目标色彩空间。

**类型：** colorSpaceManager.ColorSpaceManager

**起始版本：** 13

<!--Device-AuxiliaryPictureInfo-colorSpace: colorSpaceManager.ColorSpaceManager--><!--Device-AuxiliaryPictureInfo-colorSpace: colorSpaceManager.ColorSpaceManager-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## pixelFormat

```TypeScript
pixelFormat: PixelMapFormat
```

像素格式。

**类型：** PixelMapFormat

**起始版本：** 13

<!--Device-AuxiliaryPictureInfo-pixelFormat: PixelMapFormat--><!--Device-AuxiliaryPictureInfo-pixelFormat: PixelMapFormat-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## rowStride

```TypeScript
rowStride: number
```

行跨距。单位：字节（Byte）。应大于或等于图像每行像素数据所占的字节数，不满足时数据读取异常。

**类型：** number

**起始版本：** 13

<!--Device-AuxiliaryPictureInfo-rowStride: int--><!--Device-AuxiliaryPictureInfo-rowStride: int-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## size

```TypeScript
size: Size
```

图片大小。

**类型：** Size

**起始版本：** 13

<!--Device-AuxiliaryPictureInfo-size: Size--><!--Device-AuxiliaryPictureInfo-size: Size-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

