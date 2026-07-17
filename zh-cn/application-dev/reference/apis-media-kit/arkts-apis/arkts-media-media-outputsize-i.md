# OutputSize

This interface is used to define the output image size.

**起始版本：** 20

<!--Device-media-interface OutputSize--><!--Device-media-interface OutputSize-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVImageGenerator

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

## height

```TypeScript
height?: number
```

The expected output frame image height.If the value is less than 0, the height will be the orginal height of the video.If the value is 0 or no value is assigned, the scaling ratio will follow the specified width.If both width and height is not assigned, the output will be the original size of video frame.

**类型：** number

**起始版本：** 20

<!--Device-OutputSize-height?: int--><!--Device-OutputSize-height?: int-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVImageGenerator

## width

```TypeScript
width?:number
```

The expected output frame image width.If the value is less than 0, the width will be the orginal width of the video.If the value is 0 or no value is assigned, the scaling ratio will follow the specified height.If both width and height is not assigned, the output will be the original size of video frame.

**类型：** number

**起始版本：** 20

<!--Device-OutputSize-width?:int--><!--Device-OutputSize-width?:int-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVImageGenerator

