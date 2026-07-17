# DecodingOptionsForPicture

图像解码设置选项。

**起始版本：** 13

<!--Device-image-interface DecodingOptionsForPicture--><!--Device-image-interface DecodingOptionsForPicture-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

## 导入模块

```TypeScript
import { image } from '@kit.ImageKit';
```

## desiredAuxiliaryPictures

```TypeScript
desiredAuxiliaryPictures: Array<AuxiliaryPictureType>
```

设置AuxiliaryPicture类型，当未指定或传入空的Array时，系统会解码所有可用的AuxiliaryPicture类型。

如果不希望解码任何辅助图，可以直接解码为PixelMap，使用PixelMap创建仅包含主图的Picture。

**类型：** Array<AuxiliaryPictureType>

**起始版本：** 13

<!--Device-DecodingOptionsForPicture-desiredAuxiliaryPictures: Array<AuxiliaryPictureType>--><!--Device-DecodingOptionsForPicture-desiredAuxiliaryPictures: Array<AuxiliaryPictureType>-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

## desiredPixelFormat

```TypeScript
desiredPixelFormat?: PixelMapFormat
```

解码的像素格式。默认值为RGBA_8888。

仅支持设置：RGBA_8888、BGRA_8888、RGB_565、NV12及NV21。

当设置其他不支持的像素格式时，返回解码失败。

**类型：** PixelMapFormat

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DecodingOptionsForPicture-desiredPixelFormat?: PixelMapFormat--><!--Device-DecodingOptionsForPicture-desiredPixelFormat?: PixelMapFormat-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

## desiredSizeForMainPixelMap

```TypeScript
desiredSizeForMainPixelMap?: Size
```

期望输出主图大小（必须为正整数），默认为主图原始尺寸。单位：像素（px）。

若主图原始尺寸与指定尺寸不一致，则会进行拉伸/缩放到指定尺寸。

辅助图的宽度与高度均与主图按照同比例进行相应拉伸/缩放。

**类型：** Size

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DecodingOptionsForPicture-desiredSizeForMainPixelMap?: Size--><!--Device-DecodingOptionsForPicture-desiredSizeForMainPixelMap?: Size-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

