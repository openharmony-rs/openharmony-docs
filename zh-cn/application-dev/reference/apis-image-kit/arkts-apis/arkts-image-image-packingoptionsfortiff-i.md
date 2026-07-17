# PackingOptionsForTiff

描述TIFF图像编码参数的选项。

**起始版本：** 26.0.0

<!--Device-image-interface PackingOptionsForTiff--><!--Device-image-interface PackingOptionsForTiff-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImagePacker

## 导入模块

```TypeScript
import { image } from '@kit.ImageKit';
```

## compression

```TypeScript
compression?: number
```

该值应为整数，目前仅支持取3、4、5，分别对应压缩算法类型：3（CCITT G3）、4（CCITT G4）、5（LZW）。

- 对于二值图像：必须为3（G3）或4（G4），自动使用4（G4）。  
- 对于Y8/RGB_888格式：自动使用LZW（5），不支持指定其他压缩算法。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PackingOptionsForTiff-compression?: int--><!--Device-PackingOptionsForTiff-compression?: int-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImagePacker

## orientation

```TypeScript
orientation?: Orientation
```

图像方向。默认值为TOP_LEFT。

**类型：** Orientation

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PackingOptionsForTiff-orientation?: Orientation--><!--Device-PackingOptionsForTiff-orientation?: Orientation-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImagePacker

## resolutionUnit

```TypeScript
resolutionUnit?: number
```

分辨率单位：1（无单位）、2（英寸）、3（厘米）。目前仅支持1、2、3。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PackingOptionsForTiff-resolutionUnit?: int--><!--Device-PackingOptionsForTiff-resolutionUnit?: int-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImagePacker

## xResolution

```TypeScript
xResolution?: number
```

水平分辨率。该值必须大于0。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PackingOptionsForTiff-xResolution?: double--><!--Device-PackingOptionsForTiff-xResolution?: double-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImagePacker

## yResolution

```TypeScript
yResolution?: number
```

垂直分辨率。该值必须大于0。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PackingOptionsForTiff-yResolution?: double--><!--Device-PackingOptionsForTiff-yResolution?: double-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImagePacker

