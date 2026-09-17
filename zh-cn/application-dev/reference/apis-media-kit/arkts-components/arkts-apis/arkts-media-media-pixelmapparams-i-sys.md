# PixelMapParams

获取视频缩略图时，输出缩略图的格式参数。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Media.AVImageGenerator

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

## autoFlip

```TypeScript
autoFlip?: boolean
```

当视频具有镜像属性（垂直翻转或水平翻转）时，自动翻转缩略图。如果该值为false，则返回的缩略图将不会翻转。

**System API**: This is a system API.

**类型：** boolean

**起始版本：** 21

**系统能力：** SystemCapability.Multimedia.Media.AVImageGenerator

**系统接口：** 此接口为系统接口。

## colorFormat

```TypeScript
colorFormat?: PixelFormat
```

输出的缩略图颜色格式。

**System API**: This is a system API.

**类型：** [PixelFormat](arkts-media-media-pixelformat-e-sys.md)

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Media.AVImageGenerator

**系统接口：** 此接口为系统接口。
