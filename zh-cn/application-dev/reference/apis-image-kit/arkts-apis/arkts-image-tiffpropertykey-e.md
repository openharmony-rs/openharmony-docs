# TiffPropertyKey

表示TIFF图片信息的枚举。

> **说明：**
>
> 返回字段类型具体参考[TiffMetadata](../../../../reference/apis-image-kit/arkts-apis-image-TiffMetadata.md)。
> | 名称 | 值 | 说明 |
> | ---- | -- | ---- |
> | DOCUMENT_NAME | 'TiffDocumentName' | 文档或图像的名称。 |
> | PHOTOMETRIC_INTERPRETATION | 'TiffPhotometricInterpretation' | 定义像素颜色的解释方式（如RGB、灰度）。 |
> | ORIENTATION | 'TiffOrientation' | 图像方向。

- 1表示"Top-left"，图像未旋转。
- 2表示"Top-right"，镜像水平翻转。
- 3表示"Bottom-right"，图像旋转180°。
- 4表示"Bottom-left"，镜像垂直翻转。
- 5表示"Left-top"，镜像水平翻转后再顺时针旋转270°。
- 6表示"Right-top"，顺时针旋转90°。
- 7表示"Right-bottom"，镜像水平翻转后再顺时针旋转90°。
- 8表示"Left-bottom"，顺时针旋转270°。

若读到未定义值，会返回 `Unknown Value x`，其中 `x` 表示该标签的原始取值。 |
| RESOLUTION_UNIT | 'TiffResolutionUnit' | XResolution（水平分辨率）和YResolution（垂直分辨率）的单位，取值为英寸（Inch）或厘米（Centimeter）。 |
| COPYRIGHT | 'TiffCopyright' | 图像的版权信息。 |
| DATE_TIME | 'TiffDateTime' | 与图像关联的日期和时间（通常为最后修改时间）。 |
| IMAGE_DESCRIPTION | 'TiffImageDescription' | 图像信息描述。 |
| Y_RESOLUTION | 'TiffYResolution' | 垂直方向分辨率（每分辨率单位的像素数）。 |
| X_RESOLUTION | 'TiffXResolution' | 水平方向分辨率（每分辨率单位的像素数）。 |
| WHITE_POINT | 'TiffWhitePoint' | 用于指定图像的白点（white point）色度坐标，即图像颜色空间中被认为是“白色”的参考点。 |
| TILE_LENGTH | 'TiffTileLength' | 每个图像分块的高度。单位：像素（px）。 |
| TRANSFER_FUNCTION | 'TiffTransferFunction' | 图像的传递函数，通常用于颜色校正。 |
| TILE_WIDTH | 'TiffTileWidth' | 每个图像分块的宽度。单位：像素（px）。 |
| MAKE | 'TiffMake' | 拍摄设备制造商。 |
| MODEL | 'TiffModel' | 拍摄设备型号名称或编号。 |
| HOST_COMPUTER | 'TiffHostComputer' | 用于图像处理的主机或系统。 |
| COMPRESSION | 'TiffCompression' | TIFF图像数据所用的压缩方案。

- 1表示无压缩。
- 5表示LZW（基于字典的无损压缩算法）。
- 7表示JPEG基线。
- 8表示Deflate（基于LZ77+Huffman的无损压缩算法） |
| SOFTWARE | 'TiffSoftware' | 用于生成图像的软件名称和版本。 |
| PRIMARY_CHROMATICITIES | 'TiffPrimaryChromaticities' | 图像中RGB三原色的色度坐标。 |
| ARTIST | 'TiffArtist' | 创建图像的用户名称。 |

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Multimedia.Image.Core

## COMPRESSION

```TypeScript
COMPRESSION = 'TiffCompression'
```

Compression scheme used for image data (e.g., None, LZW, JPEG, Deflate).

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## PHOTOMETRIC_INTERPRETATION

```TypeScript
PHOTOMETRIC_INTERPRETATION = 'TiffPhotometricInterpretation'
```

Defines how pixel colors are interpreted (e.g., RGB, grayscale).

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## TRANSFER_FUNCTION

```TypeScript
TRANSFER_FUNCTION = 'TiffTransferFunction'
```

Tone transfer curve mapping pixel values to output intensity.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## ORIENTATION

```TypeScript
ORIENTATION = 'TiffOrientation'
```

Indicates image orientation for correct display rotation/flip.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## X_RESOLUTION

```TypeScript
X_RESOLUTION = 'TiffXResolution'
```

Horizontal resolution (pixels per resolution unit).

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## Y_RESOLUTION

```TypeScript
Y_RESOLUTION = 'TiffYResolution'
```

Vertical resolution (pixels per resolution unit).

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## RESOLUTION_UNIT

```TypeScript
RESOLUTION_UNIT = 'TiffResolutionUnit'
```

Unit for X/Y resolution.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## WHITE_POINT

```TypeScript
WHITE_POINT = 'TiffWhitePoint'
```

Chromaticity coordinates of the reference white point.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## PRIMARY_CHROMATICITIES

```TypeScript
PRIMARY_CHROMATICITIES = 'TiffPrimaryChromaticities'
```

Chromaticity coordinates of the RGB primaries.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## TILE_LENGTH

```TypeScript
TILE_LENGTH = 'TiffTileLength'
```

Height of each image tile in pixels.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## TILE_WIDTH

```TypeScript
TILE_WIDTH = 'TiffTileWidth'
```

Width of each image tile in pixels.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## DOCUMENT_NAME

```TypeScript
DOCUMENT_NAME = 'TiffDocumentName'
```

Name of the document or image.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## IMAGE_DESCRIPTION

```TypeScript
IMAGE_DESCRIPTION = 'TiffImageDescription'
```

Description of the image content.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## ARTIST

```TypeScript
ARTIST = 'TiffArtist'
```

Name of the image creator or artist.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## COPYRIGHT

```TypeScript
COPYRIGHT = 'TiffCopyright'
```

Copyright notice for the image.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## DATE_TIME

```TypeScript
DATE_TIME = 'TiffDateTime'
```

Date and time associated with the image (typically last modification).

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## MAKE

```TypeScript
MAKE = 'TiffMake'
```

Manufacturer of the capture device.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## MODEL

```TypeScript
MODEL = 'TiffModel'
```

Model name/number of the capture device.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## SOFTWARE

```TypeScript
SOFTWARE = 'TiffSoftware'
```

Software used to create or process the image.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## HOST_COMPUTER

```TypeScript
HOST_COMPUTER = 'TiffHostComputer'
```

Host computer/system used for image processing.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

