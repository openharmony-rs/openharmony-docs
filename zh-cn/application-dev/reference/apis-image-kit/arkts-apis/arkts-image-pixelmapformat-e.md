# PixelMapFormat

表示图片像素格式的枚举。

**起始版本：** 7

**系统能力：** SystemCapability.Multimedia.Image.Core

## UNKNOWN

```TypeScript
UNKNOWN = 0
```

未知格式。

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## ARGB_8888

```TypeScript
ARGB_8888 = 1
```

颜色信息由透明度（Alpha）与R（Red）、G（Green）、B（Blue）四部分组成，每个部分占8位，总共占32位，按照从高位到低位的顺序储存。该格式当前仅支持PixelMap的接口。

**起始版本：** 18

**系统能力：** SystemCapability.Multimedia.Image.Core

## RGB_565

```TypeScript
RGB_565 = 2
```

颜色信息由R（Red）、G（Green）、B（Blue）三部分组成，R占5位，G占6位，B占5位，总共占16位，按照从高位到低位的顺序储存。

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## RGBA_8888

```TypeScript
RGBA_8888 = 3
```

颜色信息由R（Red）、G（Green）、B（Blue）与透明度（Alpha）四部分组成，每个部分占8位，总共占32位，按照从高位到低位的顺序储存。对应
[相机服务CameraFormat中的CAMERA_FORMAT_RGBA_8888](@ohos.multimedia.camera:camera.CameraFormat)。

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## BGRA_8888

```TypeScript
BGRA_8888 = 4
```

颜色信息由B（Blue）、G（Green）、R（Red）与透明度（Alpha）四部分组成，每个部分占8位，总共占32位，按照从高位到低位的顺序储存。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## RGB_888

```TypeScript
RGB_888 = 5
```

颜色信息由R（Red）、G（Green）、B（Blue）三部分组成，每个部分占8位，总共占24位，按照从高位到低位的顺序储存。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## ALPHA_8

```TypeScript
ALPHA_8 = 6
```

颜色信息仅包含透明度（Alpha），每个像素占8位，按照从高位到低位的顺序储存。一个或多个像素组成一行像素，每行像素数据按4字节对齐，如果一行像素所占的字节数不是4的整数倍，则在行末填充空白字节以满足对齐要求。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## RGBA_F16

```TypeScript
RGBA_F16 = 7
```

颜色信息由R（Red）、G（Green）、B（Blue）与透明度（Alpha）四部分组成，每个部分占16位，总共占64位，按照从高位到低位的顺序以FP16半精度浮点数的形式储存。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## NV21

```TypeScript
NV21 = 8
```

YVU像素排列，V分量在U分量之前。颜色信息由亮度分量Y和交错排列的色度分量V和U组成，其中Y分量占8位，UV分量因4:2:0采样平均占4位，总共平均占12位，按照从高位到低位的顺序储存。对应
[相机服务CameraFormat中的CAMERA_FORMAT_YUV_420_SP](@ohos.multimedia.camera:camera.CameraFormat)。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## NV12

```TypeScript
NV12 = 9
```

YUV像素排列，U分量在V分量之前。颜色信息由亮度分量Y和交错排列的色度分量U和V组成，其中Y分量占8位，UV分量因4:2:0采样平均占4位，总共平均占12位，按照从高位到低位的顺序储存。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## RGBA_1010102

```TypeScript
RGBA_1010102 = 10
```

颜色信息由R（Red）、G（Green）、B（Blue）与透明度（Alpha）四部分组成，其中R、G、B分别占10位，透明度占2位，总共占32位，按照从高位到低位的顺序储存。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## YCBCR_P010

```TypeScript
YCBCR_P010 = 11
```

颜色信息由亮度分量Y和色度分量Cb与Cr组成，每个分量有效10位，实际存储时，Y平面每个像素占16位数据（10位有效），UV平面交错排列，每4个像素占32位数据（每色度分量10位有效），平均有效占15位，按照从高位到低位的顺序
储存。对应[相机服务CameraFormat中的CAMERA_FORMAT_YCBCR_P010](@ohos.multimedia.camera:camera.CameraFormat)。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## YCRCB_P010

```TypeScript
YCRCB_P010 = 12
```

颜色信息由亮度分量Y和色度分量Cr与Cb组成，每个分量有效10位，实际存储时，Y平面每个像素占16位数据（10位有效），UV平面交错排列，每4个像素占32位数据（每色度分量10位有效），平均有效占15位，按照从高位到低位的顺序
储存。对应[相机服务CameraFormat中的CAMERA_FORMAT_YCRCB_P010](@ohos.multimedia.camera:camera.CameraFormat)。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## Y8

```TypeScript
Y8 = 14
```

仅包含Y平面（亮度）的单通道灰度格式，每个像素占8位，按照从高位到低位的顺序储存。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## ALPHA_U8

```TypeScript
ALPHA_U8 = 15
```

Indicates that each pixel is stored on 8 bits, without 4-byte stride alignment.
Each pixel contains 1 component: ALPHA(8bits) and is stored from the higher-order to the lower-order bits.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## ALPHA_F16

```TypeScript
ALPHA_F16 = 16
```

Indicates that each pixel is stored on 16 bits.
Each pixel contains 1 component: ALPHA(16bits) and is stored from the higher-order to the lower-order bits in
FP16.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## ASTC_4x4

```TypeScript
ASTC_4x4 = 102
```

The storage format is ASTC 4x4 format, and the memory usage is only 1/4 of RGBA_8888.
This format is only used for direct display scenes and does not support pixel access or post-
processing editing.

**起始版本：** 18

**系统能力：** SystemCapability.Multimedia.Image.Core

