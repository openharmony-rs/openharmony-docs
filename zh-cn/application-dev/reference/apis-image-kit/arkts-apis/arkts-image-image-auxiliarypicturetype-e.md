# AuxiliaryPictureType

表示辅助图的图像类型的枚举。

辅助图不直接参与图片显示，且并非所有图片中都含有辅助图。

在获取和使用特定辅助图前，应首先调用Picture的[getAuxiliaryPicture](arkts-image-image-picture-i.md#getauxiliarypicture-1)方法尝试获取该辅助图。

**起始版本：** 13

<!--Device-image-enum AuxiliaryPictureType--><!--Device-image-enum AuxiliaryPictureType-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## GAINMAP

```TypeScript
GAINMAP = 1
```

增益图（Gain Map）。

用于更准确地生成HDR图像。

HDR合成通常需要同时使用SDR主图、增益图和HDR元数据（[getMetadata](arkts-image-image-pixelmap-i.md#getmetadata-1)）共同计算亮度映射关系。

**起始版本：** 13

<!--Device-AuxiliaryPictureType-GAINMAP = 1--><!--Device-AuxiliaryPictureType-GAINMAP = 1-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## DEPTH_MAP

```TypeScript
DEPTH_MAP = 2
```

深度图（Depth Map）。

用于存储每个像素与摄像头之间的距离信息，提供场景的三维结构。

可用于3D重建、背景分离和场景理解等任务。

**起始版本：** 13

<!--Device-AuxiliaryPictureType-DEPTH_MAP = 2--><!--Device-AuxiliaryPictureType-DEPTH_MAP = 2-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## UNREFOCUS_MAP

```TypeScript
UNREFOCUS_MAP = 3
```

未重对焦原图（UnReFocus Map）。

用于保存拍摄时未重对焦的图片像素内容。

可用于人像虚化等后期处理，便于用户自由选择焦点区域。

**起始版本：** 13

<!--Device-AuxiliaryPictureType-UNREFOCUS_MAP = 3--><!--Device-AuxiliaryPictureType-UNREFOCUS_MAP = 3-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## LINEAR_MAP

```TypeScript
LINEAR_MAP = 4
```

线性图（Linear Map）。

以线性方式记录光照、颜色或其他视觉要素，为图像处理提供补充信息。

可用于视觉效果增强与色彩后期处理。

**起始版本：** 13

<!--Device-AuxiliaryPictureType-LINEAR_MAP = 4--><!--Device-AuxiliaryPictureType-LINEAR_MAP = 4-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## FRAGMENT_MAP

```TypeScript
FRAGMENT_MAP = 5
```

水印裁剪图（Fragment Map）。

记录原图中被水印遮挡的区域，可能是从原图裁剪得到，也可能只是填充特定数值的像素数据作为占位符。

可用于水印移除、原图恢复等场景。

**起始版本：** 13

<!--Device-AuxiliaryPictureType-FRAGMENT_MAP = 5--><!--Device-AuxiliaryPictureType-FRAGMENT_MAP = 5-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## LHDR_GAINMAP

```TypeScript
LHDR_GAINMAP = 10
```

特殊增益图（LHDR Gain Map）。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AuxiliaryPictureType-LHDR_GAINMAP = 10--><!--Device-AuxiliaryPictureType-LHDR_GAINMAP = 10-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

