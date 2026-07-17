# PixelMapParams

Defines the format parameters of the video thumbnail to be obtained.

**起始版本：** 12

<!--Device-media-interface PixelMapParams--><!--Device-media-interface PixelMapParams-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVImageGenerator

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

## height

```TypeScript
height?: number
```

Height of the thumbnail. Unit: px.The value must be greater than 0 and less than or equal to the height of the original video.Otherwise, the returned thumbnail will not be scaled.

**类型：** number

**起始版本：** 12

<!--Device-PixelMapParams-height?: int--><!--Device-PixelMapParams-height?: int-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVImageGenerator

## width

```TypeScript
width?: number
```

Width of the thumbnail. Unit: px.The value must be greater than 0 and less than or equal to the width of the original video.Otherwise, the returned thumbnail will not be scaled.

**类型：** number

**起始版本：** 12

<!--Device-PixelMapParams-width?: int--><!--Device-PixelMapParams-width?: int-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVImageGenerator

