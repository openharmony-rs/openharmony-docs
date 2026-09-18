# PixelMapParams

获取视频缩略图时，输出缩略图的格式参数。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Media.AVImageGenerator

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

## height

```TypeScript
height?: number
```

输出的缩略图高度，单位为像素（px）。应保证大于0且不大于原始视频高度。否则返回的缩略图不会进行缩放。

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Media.AVImageGenerator

## width

```TypeScript
width?: number
```

输出的缩略图宽度，单位为像素（px）。应保证大于0且不大于原始视频宽度。否则返回的缩略图不会进行缩放。

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Media.AVImageGenerator
