# HdrStaticMetadata

静态元数据值，[HdrMetadataKey](arkts-image-image-hdrmetadatakey-e.md#HdrMetadataKey)中HDR_STATIC_METADATA关键字对应的值。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-image-interface HdrStaticMetadata--><!--Device-image-interface HdrStaticMetadata-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## displayPrimariesX

```TypeScript
displayPrimariesX: Array<double>
```

The X-coordinate of the primary colors. Specifies the normalized X-coordinates of the display device's three primary colors. The values are stored in an array of length 3, in the order of red, green, and blue (r, g, b). Each value is represented in units of 0.00002 and must fall within the range [0.0, 1.0].

**类型：** Array&lt;double&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-HdrStaticMetadata-displayPrimariesX: Array<double>--><!--Device-HdrStaticMetadata-displayPrimariesX: Array<double>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## displayPrimariesY

```TypeScript
displayPrimariesY: Array<double>
```

The Y-coordinate of the primary colors. Specifies the normalized Y-coordinates of the display device's three primary colors. The values are stored in an array of length 3, in the order of red, green, and blue (r, g, b). Each value is represented in units of 0.00002 and must fall within the range [0.0, 1.0].

**类型：** Array&lt;double&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-HdrStaticMetadata-displayPrimariesY: Array<double>--><!--Device-HdrStaticMetadata-displayPrimariesY: Array<double>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## maxContentLightLevel

```TypeScript
maxContentLightLevel: double
```

Maximum brightness of displayed content. The value is measured in units of 1, with a maximum allowed value of 65,535.

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-HdrStaticMetadata-maxContentLightLevel: double--><!--Device-HdrStaticMetadata-maxContentLightLevel: double-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## maxFrameAverageLightLevel

```TypeScript
maxFrameAverageLightLevel: double
```

Maximum average brightness of displayed content. The value is measured in units of 1, with a maximum allowed value of 65,535.

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-HdrStaticMetadata-maxFrameAverageLightLevel: double--><!--Device-HdrStaticMetadata-maxFrameAverageLightLevel: double-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## maxLuminance

```TypeScript
maxLuminance: double
```

Maximum luminance of the image's primary display. The value is measured in units of 1, with a maximum allowed value of 65,535. Unit:nit.

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-HdrStaticMetadata-maxLuminance: double--><!--Device-HdrStaticMetadata-maxLuminance: double-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## minLuminance

```TypeScript
minLuminance: double
```

Minimum luminance of the image's primary display. The value is measured in units of 0.0001, with a maximum allowed value of 6.55535.

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-HdrStaticMetadata-minLuminance: double--><!--Device-HdrStaticMetadata-minLuminance: double-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## whitePointX

```TypeScript
whitePointX: double
```

The X-coordinate of the white point value. Specifies the normalized X-coordinate of the white point. The value is represented in units of 0.00002 and must fall within the range [0.0, 1.0].

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-HdrStaticMetadata-whitePointX: double--><!--Device-HdrStaticMetadata-whitePointX: double-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## whitePointY

```TypeScript
whitePointY: double
```

The Y-coordinate of the white point value. Specifies the normalized Y-coordinate of the white point. The value is represented in units of 0.00002 and must fall within the range [0.0, 1.0].

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-HdrStaticMetadata-whitePointY: double--><!--Device-HdrStaticMetadata-whitePointY: double-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

