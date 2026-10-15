# HdrStaticMetadata

```TypeScript
interface HdrStaticMetadata
```

静态元数据值，[HdrMetadataKey](arkts-image-image-hdrmetadatakey-e.md)中HDR_STATIC_METADATA关键字对应的值。

**起始版本：** 12

<!--Device-image-interface HdrStaticMetadata--><!--Device-image-interface HdrStaticMetadata-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## 导入模块

```TypeScript
import { image } from '@kit.ImageKit';
```

## displayPrimariesX

```TypeScript
displayPrimariesX: Array<number>
```

归一化后显示设备三基色的X坐标。数组的长度为3，按R、G、B顺序存储，以0.00002为单位，取值范围是[0.0, 0.99998]。

**类型：** Array&lt;number&gt;

**起始版本：** 12

<!--Device-HdrStaticMetadata-displayPrimariesX: Array<double>--><!--Device-HdrStaticMetadata-displayPrimariesX: Array<double>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## displayPrimariesY

```TypeScript
displayPrimariesY: Array<number>
```

归一化后显示设备三基色的Y坐标。数组的长度为3，按R、G、B顺序存储，以0.00002为单位，取值范围是[0.0, 0.99998]。

**类型：** Array&lt;number&gt;

**起始版本：** 12

<!--Device-HdrStaticMetadata-displayPrimariesY: Array<double>--><!--Device-HdrStaticMetadata-displayPrimariesY: Array<double>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## maxContentLightLevel

```TypeScript
maxContentLightLevel: number
```

显示内容的最大亮度。浮点数，以1为单位，取值范围是[0, 65535]。单位：尼特（nit）。

**类型：** number

**起始版本：** 12

<!--Device-HdrStaticMetadata-maxContentLightLevel: double--><!--Device-HdrStaticMetadata-maxContentLightLevel: double-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## maxFrameAverageLightLevel

```TypeScript
maxFrameAverageLightLevel: number
```

显示内容的最大平均亮度。浮点数，以1为单位，取值范围是[0, 65535]。单位：尼特（nit）。

**类型：** number

**起始版本：** 12

<!--Device-HdrStaticMetadata-maxFrameAverageLightLevel: double--><!--Device-HdrStaticMetadata-maxFrameAverageLightLevel: double-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## maxLuminance

```TypeScript
maxLuminance: number
```

图像主监视器最大亮度。浮点数，以1为单位，取值范围是[0, 65535]。单位：尼特（nit）。

**类型：** number

**起始版本：** 12

<!--Device-HdrStaticMetadata-maxLuminance: double--><!--Device-HdrStaticMetadata-maxLuminance: double-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## minLuminance

```TypeScript
minLuminance: number
```

图像主监视器最小亮度。以0.0001为单位，取值范围是[0, 6.5535]。单位：尼特（nit）。

**类型：** number

**起始版本：** 12

<!--Device-HdrStaticMetadata-minLuminance: double--><!--Device-HdrStaticMetadata-minLuminance: double-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## whitePointX

```TypeScript
whitePointX: number
```

归一化后白点值的X坐标。以0.00002为单位，取值范围是[0.0, 0.99998]。

**类型：** number

**起始版本：** 12

<!--Device-HdrStaticMetadata-whitePointX: double--><!--Device-HdrStaticMetadata-whitePointX: double-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## whitePointY

```TypeScript
whitePointY: number
```

归一化后白点值的Y坐标。以0.00002为单位，取值范围是[0.0, 0.99998]。

**类型：** number

**起始版本：** 12

<!--Device-HdrStaticMetadata-whitePointY: double--><!--Device-HdrStaticMetadata-whitePointY: double-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core
