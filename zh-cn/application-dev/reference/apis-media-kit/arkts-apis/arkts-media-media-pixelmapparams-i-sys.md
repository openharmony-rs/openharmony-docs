# PixelMapParams

Defines the format parameters of the video thumbnail to be obtained.

**起始版本：** 12

<!--Device-media-interface PixelMapParams--><!--Device-media-interface PixelMapParams-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVImageGenerator

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

## autoFlip

```TypeScript
autoFlip?: boolean
```

Auto flip the thumbnail when video has mirror attribute (Vertical Flip or Horizontal Flip).If the value is false, the returned thumbnail will not be flipped.

**System API**: This is a system API.

**类型：** boolean

**起始版本：** 21

<!--Device-PixelMapParams-autoFlip?: boolean--><!--Device-PixelMapParams-autoFlip?: boolean-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVImageGenerator

**系统接口：** 此接口为系统接口。

## colorFormat

```TypeScript
colorFormat?: PixelFormat
```

Color format of the thumbnail.

**System API**: This is a system API.

**类型：** PixelFormat

**起始版本：** 11

<!--Device-PixelMapParams-colorFormat?: PixelFormat--><!--Device-PixelMapParams-colorFormat?: PixelFormat-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVImageGenerator

**系统接口：** 此接口为系统接口。

