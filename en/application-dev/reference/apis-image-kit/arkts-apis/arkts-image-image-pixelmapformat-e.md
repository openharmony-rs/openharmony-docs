# PixelMapFormat

Enumerates the pixel formats of images.

**Since:** 7

**System capability:** SystemCapability.Multimedia.Image.Core

## UNKNOWN

```TypeScript
UNKNOWN = 0
```

Unknown format.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core

## ARGB_8888

```TypeScript
ARGB_8888 = 1
```

Indicates that each pixel is stored on 32 bits. Each pixel contains 4 components：R(8bits), G(8bits), B(8bits), A(8bits) and are stored from the higher-order to the lower-order bits.

**Since:** 18

**System capability:** SystemCapability.Multimedia.Image.Core

## RGB_565

```TypeScript
RGB_565 = 2
```

The color information consists of three components: R (Red), G (Green), and B (Blue), which occupies five bits, six bits, and five bits, respectively. The total length is 16 bits.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core

## RGBA_8888

```TypeScript
RGBA_8888 = 3
```

The color information consists of four components: R (Red), G (Green), B (Blue), and alpha. Each component occupies 8 bits, and the total length is 32 bits. It corresponds to [CAMERA_FORMAT_RGBA_8888 in CameraFormat](../../apis-camera-kit/arkts-apis/arkts-camera-camera-cameraformat-e.md).

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core

## BGRA_8888

```TypeScript
BGRA_8888 = 4
```

The color information consists of four components: B (Blue), G (Green), R (Red), and alpha. Each component occupies 8 bits, and the total length is 32 bits.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core

## RGB_888

```TypeScript
RGB_888 = 5
```

The color information consists of three components: R (Red), G (Green), and B (Blue). Each component occupies 8 bits, and the total length is 24 bits.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core

## ALPHA_8

```TypeScript
ALPHA_8 = 6
```

The color information consists of only the alpha component, which occupies eight bits. Each row of pixels is composed of one or more pixels, and the data for each row is aligned to 4 bytes. If the byte count of a row is not a multiple of 4, blank bytes are padded at the end to ensure proper alignment.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core

## RGBA_F16

```TypeScript
RGBA_F16 = 7
```

The color information consists of four components: R (Red), G (Green), B (Blue), and alpha. Each component occupies 16 bits, and the total length is 64 bits.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core

## NV21

```TypeScript
NV21 = 8
```

YVU pixel arrangement, where the V component precedes the U component. The color information consists of the luminance component Y and the interleaved chrominance components V and U. The Y component occupies 8 bits, and the UV components occupy 4 bits on average due to 4:2:0 sampling. The total length is 12 bits on average. It corresponds to [CAMERA_FORMAT_YUV_420_SP in CameraFormat](../../apis-camera-kit/arkts-apis/arkts-camera-camera-cameraformat-e.md).

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core

## NV12

```TypeScript
NV12 = 9
```

YUV pixel arrangement, where the U component precedes the V component. The color information consists of the luminance component Y and the interleaved chrominance components U and V. The Y component occupies 8 bits, and the UV components occupy 4 bits on average due to 4:2:0 sampling. The total length is 12 bits on average.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Multimedia.Image.Core

## RGBA_1010102

```TypeScript
RGBA_1010102 = 10
```

The color information consists of four components: R (Red), G (Green), B (Blue), and alpha. R, G, and B each occupy 10 bits, and alpha occupies 2 bits. The total length is 32 bits.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## YCBCR_P010

```TypeScript
YCBCR_P010 = 11
```

The color information consists of the luminance component Y and the chrominance components Cb and Cr. Each component has effective 10 bits. In storage, the Y plane uses 16 bits per pixel (10 of which are effective). The UV plane is interleaved, with every four pixels taking up 32 bits of data (each chrominance component having 10 effective bits), resulting in an average of 15 effective bits overall. It corresponds to [CAMERA_FORMAT_YCBCR_P010 in CameraFormat](../../apis-camera-kit/arkts-apis/arkts-camera-camera-cameraformat-e.md).

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## YCRCB_P010

```TypeScript
YCRCB_P010 = 12
```

The color information consists of the luminance component Y and the chrominance components Cr and Cb. Each component has effective 10 bits. In storage, the Y plane uses 16 bits per pixel (10 of which are effective). The UV plane is interleaved, with every four pixels taking up 32 bits of data (each chrominance component having 10 effective bits), resulting in an average of 15 effective bits overall. It corresponds to [CAMERA_FORMAT_YCRCB_P010 in CameraFormat](../../apis-camera-kit/arkts-apis/arkts-camera-camera-cameraformat-e.md).

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## Y8

```TypeScript
Y8 = 14
```

Indicates that each pixel is stored on 8 bits, a YUV planar format comprised of Y plane only.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## ALPHA_U8

```TypeScript
ALPHA_U8 = 15
```

Indicates that each pixel is stored on 8 bits, without 4-byte stride alignment. Each pixel contains 1 component: ALPHA(8bits) and is stored from the higher-order to the lower-order bits.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Image.Core

## ALPHA_F16

```TypeScript
ALPHA_F16 = 16
```

Indicates that each pixel is stored on 16 bits. Each pixel contains 1 component: ALPHA(16bits) and is stored from the higher-order to the lower-order bits in FP16.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Image.Core

## ASTC_4x4

```TypeScript
ASTC_4x4 = 102
```

The storage format is ASTC 4x4 format, and the memory usage is only 1/4 of RGBA_8888. This format is only used for direct display scenes and does not support pixel access or post- processing editing.

**Since:** 18

**System capability:** SystemCapability.Multimedia.Image.Core
