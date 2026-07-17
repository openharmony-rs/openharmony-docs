# HdrDecomposeOptions（系统接口）

HDR PixelMap分解为Picture的配置选项，分解后的Picture包含一张SDR主图和一张增益图（GainMap）。

**起始版本：** 26.0.0

<!--Device-image-interface HdrDecomposeOptions--><!--Device-image-interface HdrDecomposeOptions-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { image } from '@kit.ImageKit';
```

## desiredPixelFormat

```TypeScript
desiredPixelFormat?: PixelMapFormat
```

分解后SDR PixelMap和增益图的像素格式。支持RGBA_8888、NV12、NV21。默认值为RGBA_8888。

**类型：** PixelMapFormat

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-HdrDecomposeOptions-desiredPixelFormat?: PixelMapFormat--><!--Device-HdrDecomposeOptions-desiredPixelFormat?: PixelMapFormat-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**系统接口：** 此接口为系统接口。

## isFullSizeGainmap

```TypeScript
isFullSizeGainmap?: boolean
```

是否生成全尺寸增益图。

true表示生成全尺寸增益图，增益图尺寸和主图一致；false表示不生成全尺寸增益图，增益图尺寸是主图的一半。默认值为false。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-HdrDecomposeOptions-isFullSizeGainmap?: boolean--><!--Device-HdrDecomposeOptions-isFullSizeGainmap?: boolean-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

**系统接口：** 此接口为系统接口。

