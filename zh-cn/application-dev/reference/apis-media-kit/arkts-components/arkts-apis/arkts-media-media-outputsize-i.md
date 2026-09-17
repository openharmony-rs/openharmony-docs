# OutputSize

用于获取视频缩略图时，来定义输出图像大小。

**起始版本：** 20

**系统能力：** SystemCapability.Multimedia.Media.AVImageGenerator

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

## height

```TypeScript
height?: number
```

输出的缩略图高度，单位为像素（px）。如果该值小于0，高度是视频的原始高度。如果值为0或未分配任何值，缩放比例同宽度比例。如果宽度和高度均未分配任意值，则输出原始视频帧的宽度和高度。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.Multimedia.Media.AVImageGenerator

## width

```TypeScript
width?:number
```

输出的缩略图宽度，单位为像素（px）。如果该值小于0，宽度是视频的原始宽度。如果值为0或未分配任何值，缩放比例同高度比例。如果宽度和高度均未分配任意值，则输出原始视频帧的宽度和高度。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.Multimedia.Media.AVImageGenerator
