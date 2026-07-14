# HdrStaticMetadata

静态元数据值，[HdrMetadataKey](arkts-image-hdrmetadatakey-e.md)中HDR_STATIC_METADATA关键字对应的值。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## displayPrimariesX

```TypeScript
displayPrimariesX: Array<number>
```

The X-coordinate of the primary colors. Specifies the normalized X-coordinates of the display device's three
primary colors. The values are stored in an array of length 3, in the order of red, green, and blue (r, g, b).
Each value is represented in units of 0.00002 and must fall within the range [0.0, 1.0].

**类型：** Array<number>

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## displayPrimariesY

```TypeScript
displayPrimariesY: Array<number>
```

The Y-coordinate of the primary colors. Specifies the normalized Y-coordinates of the display device's three
primary colors. The values are stored in an array of length 3, in the order of red, green, and blue (r, g, b).
Each value is represented in units of 0.00002 and must fall within the range [0.0, 1.0].

**类型：** Array<number>

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## maxContentLightLevel

```TypeScript
maxContentLightLevel: number
```

Maximum brightness of displayed content.

The value is measured in units of 1, with a maximum allowed value of 65,535.

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## maxFrameAverageLightLevel

```TypeScript
maxFrameAverageLightLevel: number
```

Maximum average brightness of displayed content.

The value is measured in units of 1, with a maximum allowed value of 65,535.

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## maxLuminance

```TypeScript
maxLuminance: number
```

Maximum luminance of the image's primary display.
The value is measured in units of 1, with a maximum allowed value of 65,535.

Unit:nit.

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## minLuminance

```TypeScript
minLuminance: number
```

Minimum luminance of the image's primary display.

The value is measured in units of 0.0001, with a maximum allowed value of 6.55535.

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## whitePointX

```TypeScript
whitePointX: number
```

The X-coordinate of the white point value. Specifies the normalized X-coordinate of the white point.

The value is represented in units of 0.00002 and must fall within the range [0.0, 1.0].

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## whitePointY

```TypeScript
whitePointY: number
```

The Y-coordinate of the white point value. Specifies the normalized Y-coordinate of the white point.

The value is represented in units of 0.00002 and must fall within the range [0.0, 1.0].

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

