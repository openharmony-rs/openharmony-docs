# HdrComposeOptions

Picture合成HDR时可配置的参数选项。

**起始版本：** 23

<!--Device-image-interface HdrComposeOptions--><!--Device-image-interface HdrComposeOptions-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## 导入模块

```TypeScript
import { image } from '@kit.ImageKit';
```

## desiredPixelFormat

```TypeScript
desiredPixelFormat?: PixelMapFormat
```

用于合成图像的像素格式，支持RGBA_1010102、YCBCR_P010和YCRCB_P010格式。

**类型：** PixelMapFormat

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-HdrComposeOptions-desiredPixelFormat?: PixelMapFormat--><!--Device-HdrComposeOptions-desiredPixelFormat?: PixelMapFormat-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

