# WatermarkConfiguration

```TypeScript
interface WatermarkConfiguration
```

添加水印的配置参数。水印位置以视频左上角为原点计算。

**起始版本：** 26.0.0

<!--Device-media-interface WatermarkConfiguration--><!--Device-media-interface WatermarkConfiguration-End-->

**系统能力：** SystemCapability.Multimedia.Media.Core

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

## height

```TypeScript
height?: number
```

水印图片的高度。取值为正整数，取值范围为[1, 4096]，单位为像素（px）。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WatermarkConfiguration-height?: int--><!--Device-WatermarkConfiguration-height?: int-End-->

**系统能力：** SystemCapability.Multimedia.Media.Core

## left

```TypeScript
left: number
```

水印相对于视频左侧位置的偏移量。取值为整数，单位为像素（px）。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WatermarkConfiguration-left: int--><!--Device-WatermarkConfiguration-left: int-End-->

**系统能力：** SystemCapability.Multimedia.Media.Core

## top

```TypeScript
top: number
```

水印相对于视频顶部位置的偏移量。取值为整数，单位为像素（px）。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WatermarkConfiguration-top: int--><!--Device-WatermarkConfiguration-top: int-End-->

**系统能力：** SystemCapability.Multimedia.Media.Core

## width

```TypeScript
width?: number
```

水印图片的宽度。取值为正整数，取值范围为[1, 4096]，单位为像素（px）。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WatermarkConfiguration-width?: int--><!--Device-WatermarkConfiguration-width?: int-End-->

**系统能力：** SystemCapability.Multimedia.Media.Core
