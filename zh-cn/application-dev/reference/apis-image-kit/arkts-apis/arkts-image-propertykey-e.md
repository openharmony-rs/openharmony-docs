# PropertyKey

表示Exif（Exchangeable image file format）图像信息的枚举。

- 格式示例中的key为：image.PropertyKey.XXX（XXX为枚举的名称，如：image.PropertyKey.NEW_SUBFILE_TYPE） 。
- 格式示例仅用于说明修改传值和读取结果的格式。具体接口使用方法请参考：
[modifyImageProperty](arkts-image-imagesource-i.md#modifyimageproperty-1)（修改单个Exif字段）、
[modifyImageProperties](arkts-image-imagesource-i.md#modifyimageproperties-1)（修
改多个Exif字段）、
[getImageProperty](arkts-image-imagesource-i.md#getimageproperty-1)（读取单个
Exif字段）、[getImageProperties](arkts-image-imagesource-i.md#getimageproperties-1)（读取多个Exif字段）。

**起始版本：** 7

**系统能力：** SystemCapability.Multimedia.Image.Core

## BITS_PER_SAMPLE

```TypeScript
BITS_PER_SAMPLE = 'BitsPerSample'
```

像素各分量的位数，如RGB，3分量，格式是8,8,8。

**读写能力：** 可读写。

**起始版本：** 7

**系统能力：** SystemCapability.Multimedia.Image.Core

## ORIENTATION

```TypeScript
ORIENTATION = 'Orientation'
```

图片方向。

1："Top-left"，图像未旋转。

2："Top-right"，镜像水平翻转。

3："Bottom-right"，图像旋转180°。

4："Bottom-left"，镜像垂直翻转。

5："Left-top"，镜像水平翻转再顺时针旋转270°。

6："Right-top"，顺时针旋转90°。

7："Right-bottom"，镜像水平翻转再顺时针旋转90°。

8："Left-bottom"，顺时针旋转270°。

如果读到未定义值x会返回"Unknown Value x"。获取该属性时会以字符串的形式返回。修改该属性时既可以以数字形式指定，也可以以字符串形式指定。

更多关于图片旋转角度的说明可参考：[如何获取图片的旋转角度信息](../../../../media/image/image-faqs/image-rotate-faq.md)。

**读写能力：** 可读写。

**起始版本：** 7

**系统能力：** SystemCapability.Multimedia.Image.Core

## IMAGE_LENGTH

```TypeScript
IMAGE_LENGTH = 'ImageLength'
```

图片长度。单位：像素（px）。

**读写能力：** 可读写。

**起始版本：** 7

**系统能力：** SystemCapability.Multimedia.Image.Core

## IMAGE_WIDTH

```TypeScript
IMAGE_WIDTH = 'ImageWidth'
```

图片宽度。单位：像素（px）。

**读写能力：** 可读写。

**起始版本：** 7

**系统能力：** SystemCapability.Multimedia.Image.Core

## GPS_LATITUDE

```TypeScript
GPS_LATITUDE = 'GPSLatitude'
```

图片纬度。修改时应按"度，分，秒"格式传入，如"39，54，7.542"

**读写能力：** 可读写。

**起始版本：** 7

**系统能力：** SystemCapability.Multimedia.Image.Core

## GPS_LONGITUDE

```TypeScript
GPS_LONGITUDE = 'GPSLongitude'
```

图片经度。修改时应按"度，分，秒"格式传入，如"116，19，42.16"

**读写能力：** 可读写。

**起始版本：** 7

**系统能力：** SystemCapability.Multimedia.Image.Core

## GPS_LATITUDE_REF

```TypeScript
GPS_LATITUDE_REF = 'GPSLatitudeRef'
```

用于标识图像拍摄地点的纬度方向（北半球或南半球）。

78："North"。

83："South"。

**读写能力：** 可读写。

**起始版本：** 7

**系统能力：** SystemCapability.Multimedia.Image.Core

## GPS_LONGITUDE_REF

```TypeScript
GPS_LONGITUDE_REF = 'GPSLongitudeRef'
```

经度引用，例如W或E， 用于标识图像拍摄地点的经度方向（东半球或西半球）。

69："East"。

87："West"。

**读写能力：** 可读写。

**起始版本：** 7

**系统能力：** SystemCapability.Multimedia.Image.Core

## DATE_TIME_ORIGINAL

```TypeScript
DATE_TIME_ORIGINAL = 'DateTimeOriginal'
```

拍摄时间，例如2022:09:06 15:48:00。

**读写能力：** 可读写。

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Image.Core

## EXPOSURE_TIME

```TypeScript
EXPOSURE_TIME = 'ExposureTime'
```

曝光时间。单位：秒（s）。

**读写能力：** 可读写。

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Image.Core

## SCENE_TYPE

```TypeScript
SCENE_TYPE = 'SceneType'
```

拍摄场景模式，例如人像、风光、运动、夜景等。

1："Directly photographed"，图像传感器直接拍摄。

**读写能力：** 可读写。

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Image.Core

## ISO_SPEED_RATINGS

```TypeScript
ISO_SPEED_RATINGS = 'ISOSpeedRatings'
```

ISO感光度，例如400。

**读写能力：** 可读写。

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Image.Core

## F_NUMBER

```TypeScript
F_NUMBER = 'FNumber'
```

光圈值，例如f/1.8。

**读写能力：** 可读写。

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Image.Core

## DATE_TIME

```TypeScript
DATE_TIME = 'DateTime'
```

日期时间。

**读写能力：** 可读写。

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.Image.Core

## GPS_TIME_STAMP

```TypeScript
GPS_TIME_STAMP = 'GPSTimeStamp'
```

GPS时间戳。

**读写能力：** 可读写。

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.Image.Core

## GPS_DATE_STAMP

```TypeScript
GPS_DATE_STAMP = 'GPSDateStamp'
```

GPS日期戳。

**读写能力：** 可读写。

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.Image.Core

## IMAGE_DESCRIPTION

```TypeScript
IMAGE_DESCRIPTION = 'ImageDescription'
```

图像信息描述。

**读写能力：** 可读写。

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.Image.Core

## MAKE

```TypeScript
MAKE = 'Make'
```

生产商。

**读写能力：** 可读写。

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.Image.Core

## MODEL

```TypeScript
MODEL = 'Model'
```

设备型号。

**读写能力：** 可读写。

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.Image.Core

## PHOTO_MODE

```TypeScript
PHOTO_MODE = 'PhotoMode'
```

拍照模式。

**读写能力：** 可读写。

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.Image.Core

## SENSITIVITY_TYPE

```TypeScript
SENSITIVITY_TYPE = 'SensitivityType'
```

灵敏度类型。

**读写能力：** 可读写。

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.Image.Core

## STANDARD_OUTPUT_SENSITIVITY

```TypeScript
STANDARD_OUTPUT_SENSITIVITY = 'StandardOutputSensitivity'
```

标准输出灵敏度。

**读写能力：** 可读写。

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.Image.Core

## RECOMMENDED_EXPOSURE_INDEX

```TypeScript
RECOMMENDED_EXPOSURE_INDEX = 'RecommendedExposureIndex'
```

推荐曝光指数。

**读写能力：** 可读写。

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.Image.Core

## ISO_SPEED

```TypeScript
ISO_SPEED = 'ISOSpeedRatings'
```

ISO速度等级。

**读写能力：** 可读写。

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.Image.Core

## APERTURE_VALUE

```TypeScript
APERTURE_VALUE = 'ApertureValue'
```

光圈值。格式如4/1。

**读写能力：** 可读写。

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.Image.Core

## EXPOSURE_BIAS_VALUE

```TypeScript
EXPOSURE_BIAS_VALUE = 'ExposureBiasValue'
```

曝光偏差值。

**读写能力：** 可读写。

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.Image.Core

## METERING_MODE

```TypeScript
METERING_MODE = 'MeteringMode'
```

测光模式。

**读写能力：** 可读写。

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.Image.Core

## LIGHT_SOURCE

```TypeScript
LIGHT_SOURCE = 'LightSource'
```

光源。例如Fluorescent。

**读写能力：** 可读写。

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.Image.Core

## FLASH

```TypeScript
FLASH = 'Flash'
```

闪光灯，记录闪光灯状态。

**读写能力：** 可读写。

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.Image.Core

## FOCAL_LENGTH

```TypeScript
FOCAL_LENGTH = 'FocalLength'
```

焦距。单位：毫米（mm）。

**读写能力：** 可读写。

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.Image.Core

## USER_COMMENT

```TypeScript
USER_COMMENT = 'UserComment'
```

用户注释。

**读写能力：** 可读写。

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.Image.Core

## PIXEL_X_DIMENSION

```TypeScript
PIXEL_X_DIMENSION = 'PixelXDimension'
```

像素X尺寸。单位：像素（px）。

**读写能力：** 可读写。

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.Image.Core

## PIXEL_Y_DIMENSION

```TypeScript
PIXEL_Y_DIMENSION = 'PixelYDimension'
```

像素Y尺寸。单位：像素（px）。

**读写能力：** 可读写。

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.Image.Core

## WHITE_BALANCE

```TypeScript
WHITE_BALANCE = 'WhiteBalance'
```

白平衡。

0："Auto white balance"，自动白平衡。

1："Manual white balance"，手动白平衡。

**读写能力：** 可读写。

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.Image.Core

## FOCAL_LENGTH_IN_35_MM_FILM

```TypeScript
FOCAL_LENGTH_IN_35_MM_FILM = 'FocalLengthIn35mmFilm'
```

换算成35mm等效焦距。单位：毫米（mm）。

**读写能力：** 可读写。

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.Image.Core

## CAPTURE_MODE

```TypeScript
CAPTURE_MODE = 'HwMnoteCaptureMode'
```

捕获模式。

**读写能力：** 可读写。

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.Image.Core

## PHYSICAL_APERTURE

```TypeScript
PHYSICAL_APERTURE = 'HwMnotePhysicalAperture'
```

物理孔径，光圈大小。单位：毫米（mm）。

**读写能力：** 只读。

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.Image.Core

## ROLL_ANGLE

```TypeScript
ROLL_ANGLE = 'HwMnoteRollAngle'
```

滚动角度。

**读写能力：** 只读。

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Image.Core

## PITCH_ANGLE

```TypeScript
PITCH_ANGLE = 'HwMnotePitchAngle'
```

俯仰角度。

**读写能力：** 只读。

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Image.Core

## SCENE_FOOD_CONF

```TypeScript
SCENE_FOOD_CONF = 'HwMnoteSceneFoodConf'
```

拍照场景：食物。

**读写能力：** 只读。

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Image.Core

## SCENE_STAGE_CONF

```TypeScript
SCENE_STAGE_CONF = 'HwMnoteSceneStageConf'
```

拍照场景：舞台。

**读写能力：** 只读。

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Image.Core

## SCENE_BLUE_SKY_CONF

```TypeScript
SCENE_BLUE_SKY_CONF = 'HwMnoteSceneBlueSkyConf'
```

拍照场景：蓝天。

**读写能力：** 只读。

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Image.Core

## SCENE_GREEN_PLANT_CONF

```TypeScript
SCENE_GREEN_PLANT_CONF = 'HwMnoteSceneGreenPlantConf'
```

拍照场景：绿植。

**读写能力：** 只读。

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Image.Core

## SCENE_BEACH_CONF

```TypeScript
SCENE_BEACH_CONF = 'HwMnoteSceneBeachConf'
```

拍照场景：沙滩。

**读写能力：** 只读。

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Image.Core

## SCENE_SNOW_CONF

```TypeScript
SCENE_SNOW_CONF = 'HwMnoteSceneSnowConf'
```

拍照场景：下雪。

**读写能力：** 只读。

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Image.Core

## SCENE_SUNSET_CONF

```TypeScript
SCENE_SUNSET_CONF = 'HwMnoteSceneSunsetConf'
```

拍照场景：日落。

**读写能力：** 只读。

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Image.Core

## SCENE_FLOWERS_CONF

```TypeScript
SCENE_FLOWERS_CONF = 'HwMnoteSceneFlowersConf'
```

拍照场景：花。

**读写能力：** 只读。

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Image.Core

## SCENE_NIGHT_CONF

```TypeScript
SCENE_NIGHT_CONF = 'HwMnoteSceneNightConf'
```

拍照场景：夜晚。

**读写能力：** 只读。

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Image.Core

## SCENE_TEXT_CONF

```TypeScript
SCENE_TEXT_CONF = 'HwMnoteSceneTextConf'
```

拍照场景：文本。

**读写能力：** 只读。

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Image.Core

## FACE_COUNT

```TypeScript
FACE_COUNT = 'HwMnoteFaceCount'
```

人脸数量。

**读写能力：** 只读。

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Image.Core

## FOCUS_MODE

```TypeScript
FOCUS_MODE = 'HwMnoteFocusMode'
```

对焦模式。

**读写能力：** 只读。

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Image.Core

## COMPRESSION

```TypeScript
COMPRESSION = 'Compression'
```

图像压缩方案。

1："Uncompressed"。

2："CCITT RLE"。

3："T4/Group 3 Fax"。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## PHOTOMETRIC_INTERPRETATION

```TypeScript
PHOTOMETRIC_INTERPRETATION = 'PhotometricInterpretation'
```

像素构成，例如RGB或YCbCr。

0："Reversed mono"。

1："Normal mono"。

2："RGB"。

3："Palette"。

5："CMYK"。

6："YCbCr"。

8："CieLAB"。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## STRIP_OFFSETS

```TypeScript
STRIP_OFFSETS = 'StripOffsets'
```

每个strip的字节偏移量。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## SAMPLES_PER_PIXEL

```TypeScript
SAMPLES_PER_PIXEL = 'SamplesPerPixel'
```

每个像素的分量数。由于该标准适用于RGB和YCbCr图像，因此该标签的值设置为 3。在JPEG压缩数据中，使用JPEG标记代替该标签。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## ROWS_PER_STRIP

```TypeScript
ROWS_PER_STRIP = 'RowsPerStrip'
```

每个strip的图像数据行数。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## STRIP_BYTE_COUNTS

```TypeScript
STRIP_BYTE_COUNTS = 'StripByteCounts'
```

每个图像数据带的总字节数。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## X_RESOLUTION

```TypeScript
X_RESOLUTION = 'XResolution'
```

图像宽度方向的分辨率。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## Y_RESOLUTION

```TypeScript
Y_RESOLUTION = 'YResolution'
```

图像高度方向的分辨率。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## PLANAR_CONFIGURATION

```TypeScript
PLANAR_CONFIGURATION = 'PlanarConfiguration'
```

表示像素组件的记录格式，chunky格式或是planar格式。

1："Chunky format"，chunky格式。

2："Planar format"，planar格式。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## RESOLUTION_UNIT

```TypeScript
RESOLUTION_UNIT = 'ResolutionUnit'
```

用于测量XResolution和YResolution的单位，英寸或者厘米。

2："Inch"，英寸。

3："Centimeter"，厘米。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## TRANSFER_FUNCTION

```TypeScript
TRANSFER_FUNCTION = 'TransferFunction'
```

图像的传递函数，通常用于颜色校正。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## SOFTWARE

```TypeScript
SOFTWARE = 'Software'
```

用于生成图像的软件名称和版本。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## ARTIST

```TypeScript
ARTIST = 'Artist'
```

创建图像的用户名称。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## WHITE_POINT

```TypeScript
WHITE_POINT = 'WhitePoint'
```

用于指定图像的白点（white point）色度坐标，即图像颜色空间中被认为是“白色”的参考点。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## PRIMARY_CHROMATICITIES

```TypeScript
PRIMARY_CHROMATICITIES = 'PrimaryChromaticities'
```

图像的主要颜色的色度。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## YCBCR_COEFFICIENTS

```TypeScript
YCBCR_COEFFICIENTS = 'YCbCrCoefficients'
```

从RGB到YCbCr图像数据的转换矩阵系数，RGB→YCbCr转换时的加权系数。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## YCBCR_SUB_SAMPLING

```TypeScript
YCBCR_SUB_SAMPLING = 'YCbCrSubSampling'
```

色度分量与亮度分量的采样比率。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## YCBCR_POSITIONING

```TypeScript
YCBCR_POSITIONING = 'YCbCrPositioning'
```

色度分量相对于亮度分量的位置。

1："Centered"，中心对齐（Centered），Cb/Cr分量的采样点相对于亮度像素点是居中对齐（常见）。

2："Co-sited"，左上对齐（Co-sited）Cb/Cr分量和 Y 分量的采样点对齐在左上角。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## REFERENCE_BLACK_WHITE

```TypeScript
REFERENCE_BLACK_WHITE = 'ReferenceBlackWhite'
```

参考黑点值和白点值。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## COPYRIGHT

```TypeScript
COPYRIGHT = 'Copyright'
```

图像的版权信息。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## JPEG_INTERCHANGE_FORMAT

```TypeScript
JPEG_INTERCHANGE_FORMAT = 'JPEGInterchangeFormat'
```

JPEG压缩缩略图数据开始字节（SOI）的偏移。

**读写能力：** 只读。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## JPEG_INTERCHANGE_FORMAT_LENGTH

```TypeScript
JPEG_INTERCHANGE_FORMAT_LENGTH = 'JPEGInterchangeFormatLength'
```

JPEG压缩缩略图数据的字节数。

**读写能力：** 只读。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## EXPOSURE_PROGRAM

```TypeScript
EXPOSURE_PROGRAM = 'ExposureProgram'
```

拍照时相机用来设置曝光的程序的类别。

0："Not defined"。

1："Manual"。

2："Normal program"。

3："Aperture priority"。

4："Shutter priority"。

5："Creative program (biased toward depth of field)"。

6："Creative program (biased toward fast shutter speed)"。

7："Portrait mode (for closeup photos with the background out of focus)"。

8："Landscape mode (for landscape photos with the background in focus)"。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## SPECTRAL_SENSITIVITY

```TypeScript
SPECTRAL_SENSITIVITY = 'SpectralSensitivity'
```

表示所用相机的每个通道的光谱灵敏度。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## OECF

```TypeScript
OECF = 'OECF'
```

表示ISO 14524中规定的光电转换函数（OECF）。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## EXIF_VERSION

```TypeScript
EXIF_VERSION = 'ExifVersion'
```

支持的Exif标准版本。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## DATE_TIME_DIGITIZED

```TypeScript
DATE_TIME_DIGITIZED = 'DateTimeDigitized'
```

图像作为数字数据存储的日期和时间，格式为YYYY:MM:DD HH:mm:ss。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## COMPONENTS_CONFIGURATION

```TypeScript
COMPONENTS_CONFIGURATION = 'ComponentsConfiguration'
```

压缩数据的特定信息。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## SHUTTER_SPEED

```TypeScript
SHUTTER_SPEED = 'ShutterSpeedValue'
```

快门速度，以APEX（摄影曝光的加法系统）值表示。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## BRIGHTNESS_VALUE

```TypeScript
BRIGHTNESS_VALUE = 'BrightnessValue'
```

图像的亮度值，以APEX单位表示。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## MAX_APERTURE_VALUE

```TypeScript
MAX_APERTURE_VALUE = 'MaxApertureValue'
```

最小F数镜头。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## SUBJECT_DISTANCE

```TypeScript
SUBJECT_DISTANCE = 'SubjectDistance'
```

测量单位为米的主体距离。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## SUBJECT_AREA

```TypeScript
SUBJECT_AREA = 'SubjectArea'
```

该标签指示整个场景中主要主体的位置和区域。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## MAKER_NOTE

```TypeScript
MAKER_NOTE = 'MakerNote'
```

Exif/DCF制造商使用的标签，用于记录任何所需信息。

在API version 12-19，该字段为只读；从API version 20开始，该字段可读写。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## SUBSEC_TIME

```TypeScript
SUBSEC_TIME = 'SubsecTime'
```

用于为DateTime标签记录秒的分数的标签。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## SUBSEC_TIME_ORIGINAL

```TypeScript
SUBSEC_TIME_ORIGINAL = 'SubsecTimeOriginal'
```

用于为DateTimeOriginal标签记录秒的分数的标签。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## SUBSEC_TIME_DIGITIZED

```TypeScript
SUBSEC_TIME_DIGITIZED = 'SubsecTimeDigitized'
```

用于为DateTimeDigitized标签记录秒的分数的标签。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## FLASHPIX_VERSION

```TypeScript
FLASHPIX_VERSION = 'FlashpixVersion'
```

该标签表示FPXR文件支持的Flashpix格式版本，增强了设备兼容性。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## COLOR_SPACE

```TypeScript
COLOR_SPACE = 'ColorSpace'
```

色彩空间信息标签，通常记录为色彩空间指定符。

1："sRGB"，sRGB标准色彩空间（常见默认值）。

2："Adobe RGB"，exif中未定义，但大量相机使用。

0xffff："Uncalibrated"，表示未校准，颜色空间不明确。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## RELATED_SOUND_FILE

```TypeScript
RELATED_SOUND_FILE = 'RelatedSoundFile'
```

与图像数据相关的音频文件的名称。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## FLASH_ENERGY

```TypeScript
FLASH_ENERGY = 'FlashEnergy'
```

图像捕获时的闪光能量，以BCPS表示。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## SPATIAL_FREQUENCY_RESPONSE

```TypeScript
SPATIAL_FREQUENCY_RESPONSE = 'SpatialFrequencyResponse'
```

相机或输入设备的空间频率表。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## FOCAL_PLANE_X_RESOLUTION

```TypeScript
FOCAL_PLANE_X_RESOLUTION = 'FocalPlaneXResolution'
```

图像宽度中每FocalPlaneResolutionUnit的像素。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## FOCAL_PLANE_Y_RESOLUTION

```TypeScript
FOCAL_PLANE_Y_RESOLUTION = 'FocalPlaneYResolution'
```

图像高度中每FocalPlaneResolutionUnit的像素。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## FOCAL_PLANE_RESOLUTION_UNIT

```TypeScript
FOCAL_PLANE_RESOLUTION_UNIT = 'FocalPlaneResolutionUnit'
```

测量FocalPlaneXResolution和FocalPlaneYResolution的单位。

2："Inch"，英寸。

3："Centimeter"，厘米。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## SUBJECT_LOCATION

```TypeScript
SUBJECT_LOCATION = 'SubjectLocation'
```

主要对象相对于左边缘的位置。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## EXPOSURE_INDEX

```TypeScript
EXPOSURE_INDEX = 'ExposureIndex'
```

捕获时选定的曝光指数。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## SENSING_METHOD

```TypeScript
SENSING_METHOD = 'SensingMethod'
```

相机上的图像传感器类型。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## FILE_SOURCE

```TypeScript
FILE_SOURCE = 'FileSource'
```

表明图像来源。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## CFA_PATTERN

```TypeScript
CFA_PATTERN = 'CFAPattern'
```

图像传感器的色彩滤光片（CFA）几何图案。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## CUSTOM_RENDERED

```TypeScript
CUSTOM_RENDERED = 'CustomRendered'
```

指示图像数据上的特殊处理。

0："Normal process"，正常处理（未自定义渲染）。

1："Custom process"，自定义处理（如艺术效果、美颜、HDR）。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## EXPOSURE_MODE

```TypeScript
EXPOSURE_MODE = 'ExposureMode'
```

拍摄时设置的曝光模式。

0："Auto exposure"，自动曝光（Auto）。

1："Manual exposure"，手动曝光（Manual）。

2："Auto bracket"，自动曝光优先（Auto bracket）。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## DIGITAL_ZOOM_RATIO

```TypeScript
DIGITAL_ZOOM_RATIO = 'DigitalZoomRatio'
```

捕获时的数字变焦比率。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## SCENE_CAPTURE_TYPE

```TypeScript
SCENE_CAPTURE_TYPE = 'SceneCaptureType'
```

捕获的场景类型。

0："Standard"，标准。

1："Landscape"，风景。

2："Portrait"，人像。

3："Night scene"，夜景。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## GAIN_CONTROL

```TypeScript
GAIN_CONTROL = 'GainControl'
```

整体图像增益调整的程度。

0："Normal"，无增益控制。

1："Low gain up"，低增益提升。

2："High gain up"，高增益提升。

3："Low gain down"， 低增益降低。

4："High gain down"，高增益降低。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## CONTRAST

```TypeScript
CONTRAST = 'Contrast'
```

相机应用的对比度处理方向。

0："Normal"，正常对比度。

1："Soft"，软对比度。

2："Hard"，硬对比度。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## SATURATION

```TypeScript
SATURATION = 'Saturation'
```

相机应用的饱和度处理方向。

0："Normal"，正常。

1："Low saturation"，低饱和度。

2："High saturation"，高饱和度。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## SHARPNESS

```TypeScript
SHARPNESS = 'Sharpness'
```

相机应用的锐度处理方向。

0："Normal"，正常（Normal）。

1："Soft"，柔和（Soft）。

2："Hard"，硬（Hard）。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## DEVICE_SETTING_DESCRIPTION

```TypeScript
DEVICE_SETTING_DESCRIPTION = 'DeviceSettingDescription'
```

特定相机模型的拍照条件信息。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## SUBJECT_DISTANCE_RANGE

```TypeScript
SUBJECT_DISTANCE_RANGE = 'SubjectDistanceRange'
```

表示主体到相机的距离范围。

0："Unknown"，未知。

1："Macro"，宏观。

2："Close view"，近景。

3："Distant view"，远景。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## IMAGE_UNIQUE_ID

```TypeScript
IMAGE_UNIQUE_ID = 'ImageUniqueID'
```

为每张图片唯一分配的标识符。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## GPS_VERSION_ID

```TypeScript
GPS_VERSION_ID = 'GPSVersionID'
```

GPS信息版本号。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## GPS_ALTITUDE_REF

```TypeScript
GPS_ALTITUDE_REF = 'GPSAltitudeRef'
```

用于GPS高度的参照高度。

0："Sea level"，海平面以上（Above Sea Level）。

1："Sea level reference"，海平面以下（Below Sea Level）。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## GPS_ALTITUDE

```TypeScript
GPS_ALTITUDE = 'GPSAltitude'
```

基于GPSAltitudeRef的高度。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## GPS_SATELLITES

```TypeScript
GPS_SATELLITES = 'GPSSatellites'
```

用于测量的GPS卫星。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## GPS_STATUS

```TypeScript
GPS_STATUS = 'GPSStatus'
```

录制图像时GPS接收器的状态。

'A'："Measurement in progress"，GPS有效，已成功锁定卫星信号，位置数据可信；

'V'："Measurement interrupted，GPS无效，当前未能定位，位置数据可能为空或不准。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## GPS_MEASURE_MODE

```TypeScript
GPS_MEASURE_MODE = 'GPSMeasureMode'
```

GPS测量模式。用于表示图像拍摄时GPS定位使用的测量模式，即是使用2D（平面）定位还是3D（含高度）定位。

2："2-dimensional measurement"，2D测量（纬度+经度）。

3："3-dimensional measurement"，3D测量（纬度+经度+高度）。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## GPS_DOP

```TypeScript
GPS_DOP = 'GPSDOP'
```

GPS DOP（数据精度等级），用于表示拍摄时GPS测量结果的定位精度水平。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## GPS_SPEED_REF

```TypeScript
GPS_SPEED_REF = 'GPSSpeedRef'
```

用来表示GPS接收器移动速度的单位。

'K'："km/h"。

'M'："mph"。

'N'："knots"。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## GPS_SPEED

```TypeScript
GPS_SPEED = 'GPSSpeed'
```

GPS接收器的移动速度。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## GPS_TRACK_REF

```TypeScript
GPS_TRACK_REF = 'GPSTrackRef'
```

GPS接收机移动方向的参照，用于说明这个角度是以哪个“北”为参考。

'T'："True direction"，真北：地理极点方向，适合地图、导航。

'M'："Magnetic direction"， 磁北：受地磁影响，磁偏角因地区和时间不同而变化。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## GPS_TRACK

```TypeScript
GPS_TRACK = 'GPSTrack'
```

GPS接收机的移动方向。用于记录拍摄设备在拍照时的移动方向（行进方向），单位是角度（deg）

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## GPS_IMG_DIRECTION_REF

```TypeScript
GPS_IMG_DIRECTION_REF = 'GPSImgDirectionRef'
```

图像方向的参照。

'T'："True direction"，真北：地理极点方向，适合地图、导航。

'M'："Magnetic direction"， 磁北：受地磁影响，磁偏角因地区和时间不同而变化。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## GPS_IMG_DIRECTION

```TypeScript
GPS_IMG_DIRECTION = 'GPSImgDirection'
```

拍摄时图像的方向。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## GPS_MAP_DATUM

```TypeScript
GPS_MAP_DATUM = 'GPSMapDatum'
```

GPS接收器使用的大地测量数据。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## GPS_DEST_LATITUDE_REF

```TypeScript
GPS_DEST_LATITUDE_REF = 'GPSDestLatitudeRef'
```

目的地点的纬度参照。

78："North"。

83："South"。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## GPS_DEST_LATITUDE

```TypeScript
GPS_DEST_LATITUDE = 'GPSDestLatitude'
```

目的地点的纬度。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## GPS_DEST_LONGITUDE_REF

```TypeScript
GPS_DEST_LONGITUDE_REF = 'GPSDestLongitudeRef'
```

目的地点的经度参照。

69："East"。

87："West"。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## GPS_DEST_LONGITUDE

```TypeScript
GPS_DEST_LONGITUDE = 'GPSDestLongitude'
```

目的地点的经度。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## GPS_DEST_BEARING_REF

```TypeScript
GPS_DEST_BEARING_REF = 'GPSDestBearingRef'
```

指向目的地点的方位参照。

'T'："True direction"，真北：地理极点方向，适合地图、导航。

'M'："Magnetic direction"，磁北：受地磁影响，磁偏角因地区和时间不同而变化。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## GPS_DEST_BEARING

```TypeScript
GPS_DEST_BEARING = 'GPSDestBearing'
```

目的地方位。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## GPS_DEST_DISTANCE_REF

```TypeScript
GPS_DEST_DISTANCE_REF = 'GPSDestDistanceRef'
```

目标点距离的测量单位。

'K'："km"，公里。

'M'："miles"，英里。

'N'："nautical miles"，海里。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## GPS_DEST_DISTANCE

```TypeScript
GPS_DEST_DISTANCE = 'GPSDestDistance'
```

到目的地点的距离。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## GPS_PROCESSING_METHOD

```TypeScript
GPS_PROCESSING_METHOD = 'GPSProcessingMethod'
```

记录定位方法名的字符串。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## GPS_AREA_INFORMATION

```TypeScript
GPS_AREA_INFORMATION = 'GPSAreaInformation'
```

记录GPS区域名的字符串。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## GPS_DIFFERENTIAL

```TypeScript
GPS_DIFFERENTIAL = 'GPSDifferential'
```

此字段表示GPS数据是否应用了差分校正，对于精确的位置准确性至关重要。

0："Without correction"，没有使用差分校正。

1："Correction applied"，使用差分校正。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## BODY_SERIAL_NUMBER

```TypeScript
BODY_SERIAL_NUMBER = 'BodySerialNumber'
```

相机机身的序列号。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## CAMERA_OWNER_NAME

```TypeScript
CAMERA_OWNER_NAME = 'CameraOwnerName'
```

相机所有者的姓名。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## COMPOSITE_IMAGE

```TypeScript
COMPOSITE_IMAGE = 'CompositeImage'
```

表示图像是否为合成图像。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## COMPRESSED_BITS_PER_PIXEL

```TypeScript
COMPRESSED_BITS_PER_PIXEL = 'CompressedBitsPerPixel'
```

用于压缩图像的压缩模式。单位：每像素位数（bit/px）。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## DNG_VERSION

```TypeScript
DNG_VERSION = 'DNGVersion'
```

DNG版本标签编码了符合DNG规范的四级版本号。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## DEFAULT_CROP_SIZE

```TypeScript
DEFAULT_CROP_SIZE = 'DefaultCropSize'
```

DefaultCropSize指定了原始坐标中的最终图像大小，考虑了额外的边缘像素。单位：像素（px）。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## GAMMA

```TypeScript
GAMMA = 'Gamma'
```

表示系数伽马的值。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## ISO_SPEED_LATITUDE_YYY

```TypeScript
ISO_SPEED_LATITUDE_YYY = 'ISOSpeedLatitudeyyy'
```

该标签指示摄像机或输入设备的ISO速度纬度yyy值，该值在ISO 12232中定义。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## ISO_SPEED_LATITUDE_ZZZ

```TypeScript
ISO_SPEED_LATITUDE_ZZZ = 'ISOSpeedLatitudezzz'
```

该标签指示摄像机或输入设备的ISO速度纬度zzz值，该值在ISO 12232中定义。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## LENS_MAKE

```TypeScript
LENS_MAKE = 'LensMake'
```

镜头的制造商。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## LENS_MODEL

```TypeScript
LENS_MODEL = 'LensModel'
```

镜头的型号名称。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## LENS_SERIAL_NUMBER

```TypeScript
LENS_SERIAL_NUMBER = 'LensSerialNumber'
```

镜头的序列号。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## LENS_SPECIFICATION

```TypeScript
LENS_SPECIFICATION = 'LensSpecification'
```

使用的镜头规格。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## NEW_SUBFILE_TYPE

```TypeScript
NEW_SUBFILE_TYPE = 'NewSubfileType'
```

在Exif中，"NewSubfileType"字段用于标识子文件的数据类型，如全分辨率图像、缩略图或多帧图像的一部分。其值是位掩码，0代表全分辨率图像，1代表缩略图，2代表多帧图像的一部分。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## OFFSET_TIME

```TypeScript
OFFSET_TIME = 'OffsetTime'
```

在Exif中，OffsetTime字段表示与UTC（协调世界时）的时间偏移，用于确定照片拍摄的本地时间。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## OFFSET_TIME_DIGITIZED

```TypeScript
OFFSET_TIME_DIGITIZED = 'OffsetTimeDigitized'
```

此标签记录图像数字化时的UTC偏移量，有助于准确调整时间戳。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## OFFSET_TIME_ORIGINAL

```TypeScript
OFFSET_TIME_ORIGINAL = 'OffsetTimeOriginal'
```

此标签记录原始图像创建时的UTC偏移量，对于时间敏感的应用至关重要。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## SOURCE_EXPOSURE_TIMES_OF_COMPOSITE_IMAGE

```TypeScript
SOURCE_EXPOSURE_TIMES_OF_COMPOSITE_IMAGE = 'SourceExposureTimesOfCompositeImage'
```

合成图像的源图像曝光时间。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## SOURCE_IMAGE_NUMBER_OF_COMPOSITE_IMAGE

```TypeScript
SOURCE_IMAGE_NUMBER_OF_COMPOSITE_IMAGE = 'SourceImageNumberOfCompositeImage'
```

用于合成图像的源图像数量。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## SUBFILE_TYPE

```TypeScript
SUBFILE_TYPE = 'SubfileType'
```

此标签指示此子文件中的数据类型。标签已弃用，请使用NewSubfileType替代。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## GPS_H_POSITIONING_ERROR

```TypeScript
GPS_H_POSITIONING_ERROR = 'GPSHPositioningError'
```

此标签指示水平定位误差。单位：米（m）。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## PHOTOGRAPHIC_SENSITIVITY

```TypeScript
PHOTOGRAPHIC_SENSITIVITY = 'PhotographicSensitivity'
```

用于表示图像拍摄时所用的感光度值（ISO 值），也叫ISO Speed。该字段是Exif 2.3后的推荐字段，ISOSpeedRatings（Tag 0x8827）是早期使用的字段，类型和含义相同，若两个字段都存在，以
`PhotographicSensitivity` 为主。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## BURST_NUMBER

```TypeScript
BURST_NUMBER = 'HwMnoteBurstNumber'
```

连拍次数。

**读写能力：** 只读。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## FACE_CONF

```TypeScript
FACE_CONF = 'HwMnoteFaceConf'
```

人脸置信度。

**读写能力：** 只读。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## FACE_LEYE_CENTER

```TypeScript
FACE_LEYE_CENTER = 'HwMnoteFaceLeyeCenter'
```

左眼中心。

**读写能力：** 只读。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## FACE_MOUTH_CENTER

```TypeScript
FACE_MOUTH_CENTER = 'HwMnoteFaceMouthCenter'
```

嘴中心。

**读写能力：** 只读。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## FACE_POINTER

```TypeScript
FACE_POINTER = 'HwMnoteFacePointer'
```

脸部指针。

**读写能力：** 只读。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## FACE_RECT

```TypeScript
FACE_RECT = 'HwMnoteFaceRect'
```

脸部矩形。

**读写能力：** 只读。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## FACE_REYE_CENTER

```TypeScript
FACE_REYE_CENTER = 'HwMnoteFaceReyeCenter'
```

右眼中心。

**读写能力：** 只读。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## FACE_SMILE_SCORE

```TypeScript
FACE_SMILE_SCORE = 'HwMnoteFaceSmileScore'
```

FaceCount张人脸的笑脸分数。

**读写能力：** 只读。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## FACE_VERSION

```TypeScript
FACE_VERSION = 'HwMnoteFaceVersion'
```

人脸算法版本信息。

**读写能力：** 只读。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## FRONT_CAMERA

```TypeScript
FRONT_CAMERA = 'HwMnoteFrontCamera'
```

是否是前置相机自拍。

**读写能力：** 只读。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## SCENE_POINTER

```TypeScript
SCENE_POINTER = 'HwMnoteScenePointer'
```

场景指针。

**读写能力：** 只读。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## SCENE_VERSION

```TypeScript
SCENE_VERSION = 'HwMnoteSceneVersion'
```

场景算法版本信息。

**读写能力：** 只读。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## IS_XMAGE_SUPPORTED

```TypeScript
IS_XMAGE_SUPPORTED = 'HwMnoteIsXmageSupported'
```

是否支持XMAGE。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## XMAGE_MODE

```TypeScript
XMAGE_MODE = 'HwMnoteXmageMode'
```

XMAGE水印模式。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## XMAGE_LEFT

```TypeScript
XMAGE_LEFT = 'HwMnoteXmageLeft'
```

水印区域X1坐标。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## XMAGE_TOP

```TypeScript
XMAGE_TOP = 'HwMnoteXmageTop'
```

水印区域Y1坐标。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## XMAGE_RIGHT

```TypeScript
XMAGE_RIGHT = 'HwMnoteXmageRight'
```

水印区域X2坐标。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## XMAGE_BOTTOM

```TypeScript
XMAGE_BOTTOM = 'HwMnoteXmageBottom'
```

水印区域Y2坐标。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## CLOUD_ENHANCEMENT_MODE

```TypeScript
CLOUD_ENHANCEMENT_MODE = 'HwMnoteCloudEnhancementMode'
```

云增强模式。

**读写能力：** 可读写。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## WIND_SNAPSHOT_MODE

```TypeScript
WIND_SNAPSHOT_MODE = 'HwMnoteWindSnapshotMode'
```

运动快拍模式。

**读写能力：** 只读。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## GIF_LOOP_COUNT

```TypeScript
GIF_LOOP_COUNT = 'GIFLoopCount'
```

GIF图片循环次数。0表示无限循环，其他值表示循环次数。

**读写能力：** 只读。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

