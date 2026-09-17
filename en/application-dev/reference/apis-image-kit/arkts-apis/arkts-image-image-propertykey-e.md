# PropertyKey

Enumerates the types of Exchangeable Image File Format (Exif) data of an image.

- The key in the format example is **image.PropertyKey.*XXX*** (where *XXX* is the name of an enumeration name, for  
example, **image.PropertyKey.NEW_SUBFILE_TYPE**).  
- The format example is used only to show how to modify values and read results. For details about how to use them,  
see [modifyImageProperty](arkts-image-image-imagesource-i.md#modifyimageproperty) (to modify a single Exif field), [modifyImageProperties](arkts-image-image-imagesource-i.md#modifyimageproperties) (to modify multiple Exif fields), [getImageProperty](arkts-image-image-imagesource-i.md#getimageproperty) (to read a single Exif field), and [getImageProperties](arkts-image-image-imagesource-i.md#getimageproperties) (to read multiple Exif fields).

**Since:** 7

**System capability:** SystemCapability.Multimedia.Image.Core

## BITS_PER_SAMPLE

```TypeScript
BITS_PER_SAMPLE = 'BitsPerSample'
```

Number of bits per sample. For example, for RGB, which has three components, the format is 8,8,8.

**Read/Write capability**: readable and writable.

**Since:** 7

**System capability:** SystemCapability.Multimedia.Image.Core

## ORIENTATION

```TypeScript
ORIENTATION = 'Orientation'
```

Image orientation.

1: **Top-left**: The image is not rotated.

2: **Top-right**: The image is flipped horizontally.

3: **Bottom-right**: The image is rotated by 180°.

4: **Bottom-left**: The image is flipped vertically.

5: **Left-top**: The image is flipped horizontally and then rotated clockwise by 270°.

6: **Right-top**: The image is rotated clockwise by 90°.

7: **Right-bottom**: The image is vertically flipped and then rotated clockwise by 90°.

8: **Left-bottom**: The image is rotated clockwise by 270°.

If an undefined value x is read, **Unknown Value x** is returned. The value of the property obtained is returned as a string. When modifying the property, you can specify the property either in the form of a number or a string.

For details about the image rotation angle, see [Obtaining the Rotation Angle of an Image](../../../media/image/image-faqs/image-rotate-faq.md).

**Read/Write capability**: readable and writable.

**Since:** 7

**System capability:** SystemCapability.Multimedia.Image.Core

## IMAGE_LENGTH

```TypeScript
IMAGE_LENGTH = 'ImageLength'
```

Image length.

**Read/Write capability**: readable and writable.

**Since:** 7

**System capability:** SystemCapability.Multimedia.Image.Core

## IMAGE_WIDTH

```TypeScript
IMAGE_WIDTH = 'ImageWidth'
```

Image width.

**Read/Write capability**: readable and writable.

**Since:** 7

**System capability:** SystemCapability.Multimedia.Image.Core

## GPS_LATITUDE

```TypeScript
GPS_LATITUDE = 'GPSLatitude'
```

Image latitude. The value must be in the format of degree,minute,second, for example, 39,54,7.542.

**Read/Write capability**: readable and writable.

**Since:** 7

**System capability:** SystemCapability.Multimedia.Image.Core

## GPS_LONGITUDE

```TypeScript
GPS_LONGITUDE = 'GPSLongitude'
```

Image longitude. The value must be in the format of degree,minute,second, for example, 116,19,42.16.

**Read/Write capability**: readable and writable.

**Since:** 7

**System capability:** SystemCapability.Multimedia.Image.Core

## GPS_LATITUDE_REF

```TypeScript
GPS_LATITUDE_REF = 'GPSLatitudeRef'
```

Latitude reference (Northern or Southern Hemisphere) of the image capture location.

78: "North".

83: "South".

**Read/Write capability**: readable and writable.

**Since:** 7

**System capability:** SystemCapability.Multimedia.Image.Core

## GPS_LONGITUDE_REF

```TypeScript
GPS_LONGITUDE_REF = 'GPSLongitudeRef'
```

Longitude reference (Eastern or Western Hemisphere) of the image capture location.

69: "East".

87: "West".

**Read/Write capability**: readable and writable.

**Since:** 7

**System capability:** SystemCapability.Multimedia.Image.Core

## DATE_TIME_ORIGINAL

```TypeScript
DATE_TIME_ORIGINAL = 'DateTimeOriginal'
```

Time when the original image data was generated, for example, 2022:09:06 15:48:00.

**Read/Write capability**: readable and writable.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Image.Core

## EXPOSURE_TIME

```TypeScript
EXPOSURE_TIME = 'ExposureTime'
```

Exposure time, for example, 1/33 seconds.

**Read/Write capability**: readable and writable.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Image.Core

## SCENE_TYPE

```TypeScript
SCENE_TYPE = 'SceneType'
```

Type of the scene, for example, portrait, scenery, motion, and night.

1: "Directly photographed", indicating that the image is directly captured by the image sensor.

**Read/Write capability**: readable and writable.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Image.Core

## ISO_SPEED_RATINGS

```TypeScript
ISO_SPEED_RATINGS = 'ISOSpeedRatings'
```

ISO sensitivity or ISO speed, for example, 400.

**Read/Write capability**: readable and writable.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Image.Core

## F_NUMBER

```TypeScript
F_NUMBER = 'FNumber'
```

F number, for example, f/1.8.

**Read/Write capability**: readable and writable.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Image.Core

## DATE_TIME

```TypeScript
DATE_TIME = 'DateTime'
```

Date and time of image creation.

**Read/Write capability**: readable and writable.

**Since:** 10

**System capability:** SystemCapability.Multimedia.Image.Core

## GPS_TIME_STAMP

```TypeScript
GPS_TIME_STAMP = 'GPSTimeStamp'
```

GPS timestamp.

**Read/Write capability**: readable and writable.

**Since:** 10

**System capability:** SystemCapability.Multimedia.Image.Core

## GPS_DATE_STAMP

```TypeScript
GPS_DATE_STAMP = 'GPSDateStamp'
```

GPS date stamp.

**Read/Write capability**: readable and writable.

**Since:** 10

**System capability:** SystemCapability.Multimedia.Image.Core

## IMAGE_DESCRIPTION

```TypeScript
IMAGE_DESCRIPTION = 'ImageDescription'
```

Image description.

**Read/Write capability**: readable and writable.

**Since:** 10

**System capability:** SystemCapability.Multimedia.Image.Core

## MAKE

```TypeScript
MAKE = 'Make'
```

Manufacturer.

**Read/Write capability**: readable and writable.

**Since:** 10

**System capability:** SystemCapability.Multimedia.Image.Core

## MODEL

```TypeScript
MODEL = 'Model'
```

Device model.

**Read/Write capability**: readable and writable.

**Since:** 10

**System capability:** SystemCapability.Multimedia.Image.Core

## PHOTO_MODE

```TypeScript
PHOTO_MODE = 'PhotoMode'
```

Photographing mode.

**Read/Write capability**: readable and writable.

**Since:** 10

**System capability:** SystemCapability.Multimedia.Image.Core

## SENSITIVITY_TYPE

```TypeScript
SENSITIVITY_TYPE = 'SensitivityType'
```

Sensitivity type.

**Read/Write capability**: readable and writable.

**Since:** 10

**System capability:** SystemCapability.Multimedia.Image.Core

## STANDARD_OUTPUT_SENSITIVITY

```TypeScript
STANDARD_OUTPUT_SENSITIVITY = 'StandardOutputSensitivity'
```

Standard output sensitivity.

**Read/Write capability**: readable and writable.

**Since:** 10

**System capability:** SystemCapability.Multimedia.Image.Core

## RECOMMENDED_EXPOSURE_INDEX

```TypeScript
RECOMMENDED_EXPOSURE_INDEX = 'RecommendedExposureIndex'
```

Recommended exposure index.

**Read/Write capability**: readable and writable.

**Since:** 10

**System capability:** SystemCapability.Multimedia.Image.Core

## ISO_SPEED

```TypeScript
ISO_SPEED = 'ISOSpeedRatings'
```

ISO speed.

**Read/Write capability**: readable and writable.

**Since:** 10

**System capability:** SystemCapability.Multimedia.Image.Core

## APERTURE_VALUE

```TypeScript
APERTURE_VALUE = 'ApertureValue'
```

Lens aperture. An example in the correct format is 4/1.

**Read/Write capability**: readable and writable.

**Since:** 10

**System capability:** SystemCapability.Multimedia.Image.Core

## EXPOSURE_BIAS_VALUE

```TypeScript
EXPOSURE_BIAS_VALUE = 'ExposureBiasValue'
```

Exposure bias.

**Read/Write capability**: readable and writable.

**Since:** 10

**System capability:** SystemCapability.Multimedia.Image.Core

## METERING_MODE

```TypeScript
METERING_MODE = 'MeteringMode'
```

Metering mode.

**Read/Write capability**: readable and writable.

**Since:** 10

**System capability:** SystemCapability.Multimedia.Image.Core

## LIGHT_SOURCE

```TypeScript
LIGHT_SOURCE = 'LightSource'
```

Light source. An example value is **Fluorescent**.

**Read/Write capability**: readable and writable.

**Since:** 10

**System capability:** SystemCapability.Multimedia.Image.Core

## FLASH

```TypeScript
FLASH = 'Flash'
```

Flash status.

**Read/Write capability**: readable and writable.

**Since:** 10

**System capability:** SystemCapability.Multimedia.Image.Core

## FOCAL_LENGTH

```TypeScript
FOCAL_LENGTH = 'FocalLength'
```

Focal length of the lens.

**Read/Write capability**: readable and writable.

**Since:** 10

**System capability:** SystemCapability.Multimedia.Image.Core

## USER_COMMENT

```TypeScript
USER_COMMENT = 'UserComment'
```

User comments.

**Read/Write capability**: readable and writable.

**Since:** 10

**System capability:** SystemCapability.Multimedia.Image.Core

## PIXEL_X_DIMENSION

```TypeScript
PIXEL_X_DIMENSION = 'PixelXDimension'
```

Pixel X dimension.

**Read/Write capability**: readable and writable.

**Since:** 10

**System capability:** SystemCapability.Multimedia.Image.Core

## PIXEL_Y_DIMENSION

```TypeScript
PIXEL_Y_DIMENSION = 'PixelYDimension'
```

Pixel Y dimension.

**Read/Write capability**: readable and writable.

**Since:** 10

**System capability:** SystemCapability.Multimedia.Image.Core

## WHITE_BALANCE

```TypeScript
WHITE_BALANCE = 'WhiteBalance'
```

White balance.

0: "Auto white balance."

1: "Manual white balance."

**Read/Write capability**: readable and writable.

**Since:** 10

**System capability:** SystemCapability.Multimedia.Image.Core

## FOCAL_LENGTH_IN_35_MM_FILM

```TypeScript
FOCAL_LENGTH_IN_35_MM_FILM = 'FocalLengthIn35mmFilm'
```

Focal length in 35mm film.

**Read/Write capability**: readable and writable.

**Since:** 10

**System capability:** SystemCapability.Multimedia.Image.Core

## CAPTURE_MODE

```TypeScript
CAPTURE_MODE = 'HwMnoteCaptureMode'
```

Capture mode.

**Read/Write capability**: readable and writable.

**Since:** 10

**System capability:** SystemCapability.Multimedia.Image.Core

## PHYSICAL_APERTURE

```TypeScript
PHYSICAL_APERTURE = 'HwMnotePhysicalAperture'
```

Physical aperture.

**Read/Write capability**: read-only

**Since:** 10

**System capability:** SystemCapability.Multimedia.Image.Core

## ROLL_ANGLE

```TypeScript
ROLL_ANGLE = 'HwMnoteRollAngle'
```

Roll angle.

**Read/Write capability**: read-only

**Since:** 11

**System capability:** SystemCapability.Multimedia.Image.Core

## PITCH_ANGLE

```TypeScript
PITCH_ANGLE = 'HwMnotePitchAngle'
```

Pitch angle.

**Read/Write capability**: read-only

**Since:** 11

**System capability:** SystemCapability.Multimedia.Image.Core

## SCENE_FOOD_CONF

```TypeScript
SCENE_FOOD_CONF = 'HwMnoteSceneFoodConf'
```

Photographing scene: food.

**Read/Write capability**: read-only

**Since:** 11

**System capability:** SystemCapability.Multimedia.Image.Core

## SCENE_STAGE_CONF

```TypeScript
SCENE_STAGE_CONF = 'HwMnoteSceneStageConf'
```

Photographing scene: stage.

**Read/Write capability**: read-only

**Since:** 11

**System capability:** SystemCapability.Multimedia.Image.Core

## SCENE_BLUE_SKY_CONF

```TypeScript
SCENE_BLUE_SKY_CONF = 'HwMnoteSceneBlueSkyConf'
```

Photographing scene: blue sky.

**Read/Write capability**: read-only

**Since:** 11

**System capability:** SystemCapability.Multimedia.Image.Core

## SCENE_GREEN_PLANT_CONF

```TypeScript
SCENE_GREEN_PLANT_CONF = 'HwMnoteSceneGreenPlantConf'
```

Photographing scene: green plant.

**Read/Write capability**: read-only

**Since:** 11

**System capability:** SystemCapability.Multimedia.Image.Core

## SCENE_BEACH_CONF

```TypeScript
SCENE_BEACH_CONF = 'HwMnoteSceneBeachConf'
```

Photographing scene: beach.

**Read/Write capability**: read-only

**Since:** 11

**System capability:** SystemCapability.Multimedia.Image.Core

## SCENE_SNOW_CONF

```TypeScript
SCENE_SNOW_CONF = 'HwMnoteSceneSnowConf'
```

Photographing scene: snow.

**Read/Write capability**: read-only

**Since:** 11

**System capability:** SystemCapability.Multimedia.Image.Core

## SCENE_SUNSET_CONF

```TypeScript
SCENE_SUNSET_CONF = 'HwMnoteSceneSunsetConf'
```

Photographing scene: sunset.

**Read/Write capability**: read-only

**Since:** 11

**System capability:** SystemCapability.Multimedia.Image.Core

## SCENE_FLOWERS_CONF

```TypeScript
SCENE_FLOWERS_CONF = 'HwMnoteSceneFlowersConf'
```

Photographing scene: flowers.

**Read/Write capability**: read-only

**Since:** 11

**System capability:** SystemCapability.Multimedia.Image.Core

## SCENE_NIGHT_CONF

```TypeScript
SCENE_NIGHT_CONF = 'HwMnoteSceneNightConf'
```

Photographing scene: night.

**Read/Write capability**: read-only

**Since:** 11

**System capability:** SystemCapability.Multimedia.Image.Core

## SCENE_TEXT_CONF

```TypeScript
SCENE_TEXT_CONF = 'HwMnoteSceneTextConf'
```

Photographing scene: text.

**Read/Write capability**: read-only

**Since:** 11

**System capability:** SystemCapability.Multimedia.Image.Core

## FACE_COUNT

```TypeScript
FACE_COUNT = 'HwMnoteFaceCount'
```

Number of faces.

**Read/Write capability**: read-only

**Since:** 11

**System capability:** SystemCapability.Multimedia.Image.Core

## FOCUS_MODE

```TypeScript
FOCUS_MODE = 'HwMnoteFocusMode'
```

Focus mode.

**Read/Write capability**: read-only

**Since:** 11

**System capability:** SystemCapability.Multimedia.Image.Core

## COMPRESSION

```TypeScript
COMPRESSION = 'Compression'
```

Compression scheme used on the image data.

1: "Uncompressed".

2: "CCITT RLE".

3: "T4/Group 3 Fax".

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## PHOTOMETRIC_INTERPRETATION

```TypeScript
PHOTOMETRIC_INTERPRETATION = 'PhotometricInterpretation'
```

Color space of the image data, for example, RGB or YCbCr.

0: "Reversed mono".

1: "Normal mono".

2: "RGB".

3: "Palette".

5: "CMYK".

6: "YCbCr".

8: "CieLAB".

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## STRIP_OFFSETS

```TypeScript
STRIP_OFFSETS = 'StripOffsets'
```

Byte offset of each strip.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## SAMPLES_PER_PIXEL

```TypeScript
SAMPLES_PER_PIXEL = 'SamplesPerPixel'
```

Number of components per pixel. The value is **3** for RGB and YCbCr images. The **JPEG** key is used in JPEG compressed data.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## ROWS_PER_STRIP

```TypeScript
ROWS_PER_STRIP = 'RowsPerStrip'
```

Number of rows per strip.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## STRIP_BYTE_COUNTS

```TypeScript
STRIP_BYTE_COUNTS = 'StripByteCounts'
```

Number of bytes in each strip after compression.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## X_RESOLUTION

```TypeScript
X_RESOLUTION = 'XResolution'
```

Number of pixels per ResolutionUnit in the image width (X) direction.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## Y_RESOLUTION

```TypeScript
Y_RESOLUTION = 'YResolution'
```

Number of pixels per ResolutionUnit in the image height (Y) direction.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## PLANAR_CONFIGURATION

```TypeScript
PLANAR_CONFIGURATION = 'PlanarConfiguration'
```

Storage format of components of each pixel, which can be chunky or planar.

1: "Chunky format": chunky format.

2: "Planar format": planar format.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## RESOLUTION_UNIT

```TypeScript
RESOLUTION_UNIT = 'ResolutionUnit'
```

Unit of measurement for XResolution and YResolution, in inches or centimeters.

2: "Inch": measured in inches.

3: "Centimeter": measured in centimeters.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## TRANSFER_FUNCTION

```TypeScript
TRANSFER_FUNCTION = 'TransferFunction'
```

Transfer function for the image, which is usually used for color correction.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## SOFTWARE

```TypeScript
SOFTWARE = 'Software'
```

Name and version number of the software used to create the image.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## ARTIST

```TypeScript
ARTIST = 'Artist'
```

Person who created the image.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## WHITE_POINT

```TypeScript
WHITE_POINT = 'WhitePoint'
```

Chromaticity coordinates of the white point, the reference for "white", in the color space of the image.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## PRIMARY_CHROMATICITIES

```TypeScript
PRIMARY_CHROMATICITIES = 'PrimaryChromaticities'
```

Chromaticities of the primaries of the image.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## YCBCR_COEFFICIENTS

```TypeScript
YCBCR_COEFFICIENTS = 'YCbCrCoefficients'
```

Coefficients for the conversion matrix that transforms image data from RGB to YCbCr.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## YCBCR_SUB_SAMPLING

```TypeScript
YCBCR_SUB_SAMPLING = 'YCbCrSubSampling'
```

Subsampling factors used for the chrominance components of a YCbCr image.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## YCBCR_POSITIONING

```TypeScript
YCBCR_POSITIONING = 'YCbCrPositioning'
```

Positioning of subsampled chrominance components relative to luminance samples.

1: "Centered": Cb/Cr chrominance components are centered relative to the luminance pixels (common practice).

2: "Co-sited": Cb/Cr and Y sampling points align at the top-left corner.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## REFERENCE_BLACK_WHITE

```TypeScript
REFERENCE_BLACK_WHITE = 'ReferenceBlackWhite'
```

Reference values for black and white points.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## COPYRIGHT

```TypeScript
COPYRIGHT = 'Copyright'
```

Copyright notice of the image.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## JPEG_INTERCHANGE_FORMAT

```TypeScript
JPEG_INTERCHANGE_FORMAT = 'JPEGInterchangeFormat'
```

Offset of the SOI marker of a JPEG interchange format bitstream.

**Read/Write capability**: read-only

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## JPEG_INTERCHANGE_FORMAT_LENGTH

```TypeScript
JPEG_INTERCHANGE_FORMAT_LENGTH = 'JPEGInterchangeFormatLength'
```

Number of bytes of the JPEG stream.

**Read/Write capability**: read-only

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## EXPOSURE_PROGRAM

```TypeScript
EXPOSURE_PROGRAM = 'ExposureProgram'
```

Class of the program used by the camera to set exposure when the image was captured.

0: "Not defined".

1: "Manual".

2: "Normal program".

3: "Aperture priority".

4: "Shutter priority".

5: "Creative program (biased toward depth of field)".

6: "Creative program (biased toward fast shutter speed)".

7: "Portrait mode (for closeup photos with the background out of focus)".

8: "Landscape mode (for landscape photos with the background in focus)".

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## SPECTRAL_SENSITIVITY

```TypeScript
SPECTRAL_SENSITIVITY = 'SpectralSensitivity'
```

Spectral sensitivity of each channel of the camera.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## OECF

```TypeScript
OECF = 'OECF'
```

Opto-Electric Conversion Function (OECF) specified in ISO 14524.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## EXIF_VERSION

```TypeScript
EXIF_VERSION = 'ExifVersion'
```

Version of the supported Exif standard.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## DATE_TIME_DIGITIZED

```TypeScript
DATE_TIME_DIGITIZED = 'DateTimeDigitized'
```

Date and time when the image was stored as digital data, in the format of YYYY:MM:DD HH:mm:ss.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## COMPONENTS_CONFIGURATION

```TypeScript
COMPONENTS_CONFIGURATION = 'ComponentsConfiguration'
```

Specific information about compressed data.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## SHUTTER_SPEED

```TypeScript
SHUTTER_SPEED = 'ShutterSpeedValue'
```

Shutter speed, expressed in Additive System of Photographic Exposure (APEX) values.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## BRIGHTNESS_VALUE

```TypeScript
BRIGHTNESS_VALUE = 'BrightnessValue'
```

Value of brightness, expressed in APEX values.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## MAX_APERTURE_VALUE

```TypeScript
MAX_APERTURE_VALUE = 'MaxApertureValue'
```

Smallest F number of the lens.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## SUBJECT_DISTANCE

```TypeScript
SUBJECT_DISTANCE = 'SubjectDistance'
```

Distance to the subject, in meters.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## SUBJECT_AREA

```TypeScript
SUBJECT_AREA = 'SubjectArea'
```

Location and area of the main subject in the entire scene.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## MAKER_NOTE

```TypeScript
MAKER_NOTE = 'MakerNote'
```

Marker used by Exif/DCF manufacturers to record any required information.

This field is read-only in API versions 12 to 19 and is readable and writable in API version 20 and later.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## SUBSEC_TIME

```TypeScript
SUBSEC_TIME = 'SubsecTime'
```

Tag used to record fractions of seconds for the **DateTime** tag.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## SUBSEC_TIME_ORIGINAL

```TypeScript
SUBSEC_TIME_ORIGINAL = 'SubsecTimeOriginal'
```

Tag used to record fractions of seconds for the **DateTimeOriginal** tag.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## SUBSEC_TIME_DIGITIZED

```TypeScript
SUBSEC_TIME_DIGITIZED = 'SubsecTimeDigitized'
```

Tag used to record fractions of seconds for the **DateTimeDigitized** tag.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## FLASHPIX_VERSION

```TypeScript
FLASHPIX_VERSION = 'FlashpixVersion'
```

FlashPix format version supported by an FPXR file. It is used to enhance device compatibility.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## COLOR_SPACE

```TypeScript
COLOR_SPACE = 'ColorSpace'
```

Color space information, which is usually recorded as a color space specifier.

1: "sRGB", indicating the standard sRGB color space. It is the typical default value.

2: "Adobe RGB", indicating the Adobe RGB color space. It is not formally defined in Exif, but commonly used in practice.

0xffff: "Uncalibrated", indicating that the color space is uncalibrated and unknown.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## RELATED_SOUND_FILE

```TypeScript
RELATED_SOUND_FILE = 'RelatedSoundFile'
```

Name of an audio file related to the image data.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## FLASH_ENERGY

```TypeScript
FLASH_ENERGY = 'FlashEnergy'
```

Strobe energy at the time the image was captured, in Beam Candle Power Seconds (BCPS).

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## SPATIAL_FREQUENCY_RESPONSE

```TypeScript
SPATIAL_FREQUENCY_RESPONSE = 'SpatialFrequencyResponse'
```

Spatial frequency table of the camera or input device.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## FOCAL_PLANE_X_RESOLUTION

```TypeScript
FOCAL_PLANE_X_RESOLUTION = 'FocalPlaneXResolution'
```

Number of pixels in the image width (X) direction per FocalPlaneResolutionUnit.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## FOCAL_PLANE_Y_RESOLUTION

```TypeScript
FOCAL_PLANE_Y_RESOLUTION = 'FocalPlaneYResolution'
```

Number of pixels in the image height (Y) direction per FocalPlaneResolutionUnit.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## FOCAL_PLANE_RESOLUTION_UNIT

```TypeScript
FOCAL_PLANE_RESOLUTION_UNIT = 'FocalPlaneResolutionUnit'
```

Unit for measuring FocalPlaneXResolution and FocalPlaneYResolution.

2: "Inch": measured in inches.

3: "Centimeter": measured in centimeters.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## SUBJECT_LOCATION

```TypeScript
SUBJECT_LOCATION = 'SubjectLocation'
```

Location of the main subject relative to the left edge.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## EXPOSURE_INDEX

```TypeScript
EXPOSURE_INDEX = 'ExposureIndex'
```

Exposure index selected at the time the image is captured.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## SENSING_METHOD

```TypeScript
SENSING_METHOD = 'SensingMethod'
```

Type of the image sensor on the camera.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## FILE_SOURCE

```TypeScript
FILE_SOURCE = 'FileSource'
```

Image source.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## CFA_PATTERN

```TypeScript
CFA_PATTERN = 'CFAPattern'
```

Color Filter Array (CFA) geometric pattern of the image sensor.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## CUSTOM_RENDERED

```TypeScript
CUSTOM_RENDERED = 'CustomRendered'
```

Special processing on image data.

0: "Normal process", indicating normal processing (no custom rendering).

1: "Custom process", indicating custom processing (such as artistic effect, beauty, and HDR).

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## EXPOSURE_MODE

```TypeScript
EXPOSURE_MODE = 'ExposureMode'
```

Exposure mode set when the image was captured.

0: "Auto exposure."

1: "Manual exposure."

2: "Auto bracket."

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## DIGITAL_ZOOM_RATIO

```TypeScript
DIGITAL_ZOOM_RATIO = 'DigitalZoomRatio'
```

Digital zoom ratio when the image was captured.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## SCENE_CAPTURE_TYPE

```TypeScript
SCENE_CAPTURE_TYPE = 'SceneCaptureType'
```

Type of the scene that was captured.

0: "Standard."

1: "Landscape."

2: "Portrait."

3: "Night scene."

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## GAIN_CONTROL

```TypeScript
GAIN_CONTROL = 'GainControl'
```

Degree of overall image gain adjustment.

0: "Normal", no gain control.

1: "Low gain up."

2: "High gain up."

3: "Low gain down."

4: "High gain down."

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## CONTRAST

```TypeScript
CONTRAST = 'Contrast'
```

Direction of contrast processing used by the camera.

0: "Normal", normal contrast.

1: "Soft", soft contrast.

2: "Hard", hard contrast.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## SATURATION

```TypeScript
SATURATION = 'Saturation'
```

Direction of saturation processing used by the camera.

0:"Normal": normal saturation.

1: "Low saturation."

2: "High saturation."

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## SHARPNESS

```TypeScript
SHARPNESS = 'Sharpness'
```

Direction of sharpness processing used by the camera.

0:"Normal": normal sharpness.

1: "Soft."

2: "Hard."

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## DEVICE_SETTING_DESCRIPTION

```TypeScript
DEVICE_SETTING_DESCRIPTION = 'DeviceSettingDescription'
```

Information about the photographing conditions of a specific camera model.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## SUBJECT_DISTANCE_RANGE

```TypeScript
SUBJECT_DISTANCE_RANGE = 'SubjectDistanceRange'
```

Distance to the subject.

0: "Unknown."

1: "Macro."

2: "Close view."

3: "Distant view."

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## IMAGE_UNIQUE_ID

```TypeScript
IMAGE_UNIQUE_ID = 'ImageUniqueID'
```

Unique identifier assigned to each image.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## GPS_VERSION_ID

```TypeScript
GPS_VERSION_ID = 'GPSVersionID'
```

GPS information version.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## GPS_ALTITUDE_REF

```TypeScript
GPS_ALTITUDE_REF = 'GPSAltitudeRef'
```

Whether the latitude is north or south latitude.

0: Sea level, which is above sea level.

1: "Sea level reference," which is below the sea level.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## GPS_ALTITUDE

```TypeScript
GPS_ALTITUDE = 'GPSAltitude'
```

Altitude based on the reference in GPSAltitudeRef.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## GPS_SATELLITES

```TypeScript
GPS_SATELLITES = 'GPSSatellites'
```

GPS satellites used for measurement.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## GPS_STATUS

```TypeScript
GPS_STATUS = 'GPSStatus'
```

Status of the GPS receiver when the image was recorded.

'A': "Measurement in progress", GPS is working, satellite signals are locked, and location data is trustworthy.

'V': "Measurement interrupted", GPS is not working, current positioning is unavailable, and location data may be missing or incorrect.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## GPS_MEASURE_MODE

```TypeScript
GPS_MEASURE_MODE = 'GPSMeasureMode'
```

GPS measurement pmode. Whether the 2D (planar) or 3D (with height) measurement mode is used for GPS positioning.

2: "2-dimensional measurement", (latitude+longitude).

3: "3-dimensional measurement", (latitude + longitude + height).

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## GPS_DOP

```TypeScript
GPS_DOP = 'GPSDOP'
```

GPS Dilution of Precision (DOP), which reflects the precision of GPS measurements taken when the photo was captured.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## GPS_SPEED_REF

```TypeScript
GPS_SPEED_REF = 'GPSSpeedRef'
```

Unit used to express the movement speed of the GPS receiver.

'K': "km/h".

'M': "mph".

'N': "knots".

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## GPS_SPEED

```TypeScript
GPS_SPEED = 'GPSSpeed'
```

Movement speed of the GPS receiver.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## GPS_TRACK_REF

```TypeScript
GPS_TRACK_REF = 'GPSTrackRef'
```

Which type of "North" is used as the reference for the direction angle.

'T': "True direction", which is the geographic North Pole direction. This is the standard used for maps and navigation systems.

'M': "Magnetic direction", which is the direction pointed to by the Earth's magnetic field. Note that magnetic declination varies by location and changes over time.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## GPS_TRACK

```TypeScript
GPS_TRACK = 'GPSTrack'
```

Movement direction of the GPS receiver. Direction of movement (heading) of the camera at the moment the photo was taken, measured in degrees.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## GPS_IMG_DIRECTION_REF

```TypeScript
GPS_IMG_DIRECTION_REF = 'GPSImgDirectionRef'
```

Reference of the direction of the image when it was captured.

'T': "True direction", which is the geographic North Pole direction. This is the standard used for maps and navigation systems.

'M': "Magnetic direction", which is the direction pointed to by the Earth's magnetic field. Note that magnetic declination varies by location and changes over time.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## GPS_IMG_DIRECTION

```TypeScript
GPS_IMG_DIRECTION = 'GPSImgDirection'
```

Direction of the image when it was captured.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## GPS_MAP_DATUM

```TypeScript
GPS_MAP_DATUM = 'GPSMapDatum'
```

Geodetic survey data used by the GPS receiver.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## GPS_DEST_LATITUDE_REF

```TypeScript
GPS_DEST_LATITUDE_REF = 'GPSDestLatitudeRef'
```

Whether the latitude of the destination point is north or south latitude.

78: "North".

83: "South".

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## GPS_DEST_LATITUDE

```TypeScript
GPS_DEST_LATITUDE = 'GPSDestLatitude'
```

Latitude of the destination point.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## GPS_DEST_LONGITUDE_REF

```TypeScript
GPS_DEST_LONGITUDE_REF = 'GPSDestLongitudeRef'
```

Whether the longitude of the destination point is east or west longitude.

69: "East".

87: "West".

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## GPS_DEST_LONGITUDE

```TypeScript
GPS_DEST_LONGITUDE = 'GPSDestLongitude'
```

Longitude of the destination point.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## GPS_DEST_BEARING_REF

```TypeScript
GPS_DEST_BEARING_REF = 'GPSDestBearingRef'
```

Reference of the bearing to the destination point.

'T': "True direction", which is the geographic North Pole direction. This is the standard used for maps and navigation systems.

'M': "Magnetic direction", which is the direction pointed to by the Earth's magnetic field. Note that magnetic declination varies by location and changes over time.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## GPS_DEST_BEARING

```TypeScript
GPS_DEST_BEARING = 'GPSDestBearing'
```

Bearing to the destination point.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## GPS_DEST_DISTANCE_REF

```TypeScript
GPS_DEST_DISTANCE_REF = 'GPSDestDistanceRef'
```

Unit used to express the distance to the destination point.

'K': "km."

'M': "miles."

'N': "nautical miles."

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## GPS_DEST_DISTANCE

```TypeScript
GPS_DEST_DISTANCE = 'GPSDestDistance'
```

Distance to the destination point.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## GPS_PROCESSING_METHOD

```TypeScript
GPS_PROCESSING_METHOD = 'GPSProcessingMethod'
```

String that records the name of the method used for positioning.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## GPS_AREA_INFORMATION

```TypeScript
GPS_AREA_INFORMATION = 'GPSAreaInformation'
```

String that records the name of the GPS area.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## GPS_DIFFERENTIAL

```TypeScript
GPS_DIFFERENTIAL = 'GPSDifferential'
```

Whether differential correction is applied to the GPS receiver. It is critical to accurate location accuracy.

0: "Without correction", which indicates that no differential correction is used.

1:"Correction applied", which indicates that differential correction is used.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## BODY_SERIAL_NUMBER

```TypeScript
BODY_SERIAL_NUMBER = 'BodySerialNumber'
```

Serial number of the camera body.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## CAMERA_OWNER_NAME

```TypeScript
CAMERA_OWNER_NAME = 'CameraOwnerName'
```

Name of the camera owner.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## COMPOSITE_IMAGE

```TypeScript
COMPOSITE_IMAGE = 'CompositeImage'
```

Whether the image is a composite image.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## COMPRESSED_BITS_PER_PIXEL

```TypeScript
COMPRESSED_BITS_PER_PIXEL = 'CompressedBitsPerPixel'
```

Number of bits per pixel. It is specific to compressed data.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## DNG_VERSION

```TypeScript
DNG_VERSION = 'DNGVersion'
```

DNG version. It encodes the DNG 4-tier version number.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## DEFAULT_CROP_SIZE

```TypeScript
DEFAULT_CROP_SIZE = 'DefaultCropSize'
```

Size of the final image area, in raw image coordinates, taking into account extra pixels around the edges of the final image.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## GAMMA

```TypeScript
GAMMA = 'Gamma'
```

Gamma value.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## ISO_SPEED_LATITUDE_YYY

```TypeScript
ISO_SPEED_LATITUDE_YYY = 'ISOSpeedLatitudeyyy'
```

ISO speed latitude yyy value of the camera or input device, which is defined in ISO 12232.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## ISO_SPEED_LATITUDE_ZZZ

```TypeScript
ISO_SPEED_LATITUDE_ZZZ = 'ISOSpeedLatitudezzz'
```

ISO speed latitude zzz value of the camera or input device, which is defined in ISO 12232.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## LENS_MAKE

```TypeScript
LENS_MAKE = 'LensMake'
```

Manufacturer of the lens.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## LENS_MODEL

```TypeScript
LENS_MODEL = 'LensModel'
```

Model of the lens.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## LENS_SERIAL_NUMBER

```TypeScript
LENS_SERIAL_NUMBER = 'LensSerialNumber'
```

Serial number of the lens.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## LENS_SPECIFICATION

```TypeScript
LENS_SPECIFICATION = 'LensSpecification'
```

Specifications of the lens.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## NEW_SUBFILE_TYPE

```TypeScript
NEW_SUBFILE_TYPE = 'NewSubfileType'
```

Data type of a subfile, such as a full-resolution image, a thumbnail, or a part of a multi-frame image. The value is a bit mask. The value 0 indicates a full-resolution image, **1** indicates a thumbnail, and **2** indicates a part of a multi-frame image.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## OFFSET_TIME

```TypeScript
OFFSET_TIME = 'OffsetTime'
```

Time with an offset from UTC when the image was captured.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## OFFSET_TIME_DIGITIZED

```TypeScript
OFFSET_TIME_DIGITIZED = 'OffsetTimeDigitized'
```

Time with an offset from UTC when the image was digitized. It helps to accurately adjust the timestamp.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## OFFSET_TIME_ORIGINAL

```TypeScript
OFFSET_TIME_ORIGINAL = 'OffsetTimeOriginal'
```

Time with an offset from UTC when the original image was created. It is critical for time-sensitive applications.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## SOURCE_EXPOSURE_TIMES_OF_COMPOSITE_IMAGE

```TypeScript
SOURCE_EXPOSURE_TIMES_OF_COMPOSITE_IMAGE = 'SourceExposureTimesOfCompositeImage'
```

Exposure time of source images of the composite image.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## SOURCE_IMAGE_NUMBER_OF_COMPOSITE_IMAGE

```TypeScript
SOURCE_IMAGE_NUMBER_OF_COMPOSITE_IMAGE = 'SourceImageNumberOfCompositeImage'
```

Number of source images of the composite image.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## SUBFILE_TYPE

```TypeScript
SUBFILE_TYPE = 'SubfileType'
```

Type of data contained in this subfile. This tag has been deprecated. Use **NewSubfileType** instead.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## GPS_H_POSITIONING_ERROR

```TypeScript
GPS_H_POSITIONING_ERROR = 'GPSHPositioningError'
```

Horizontal positioning error, in meters.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## PHOTOGRAPHIC_SENSITIVITY

```TypeScript
PHOTOGRAPHIC_SENSITIVITY = 'PhotographicSensitivity'
```

ISO sensitivity (ISO speed) used when the image was captured. It is the recommended field in Exif 2.3 and later. The earlier field, ISOSpeedRatings (Tag 0x8827), has the same data type and meaning. However, if both fields are present, the **PhotographicSensitivity** value should be used.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## BURST_NUMBER

```TypeScript
BURST_NUMBER = 'HwMnoteBurstNumber'
```

Number of burst shooting times.

**Read/Write capability**: read-only

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## FACE_CONF

```TypeScript
FACE_CONF = 'HwMnoteFaceConf'
```

Face confidence.

**Read/Write capability**: read-only

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## FACE_LEYE_CENTER

```TypeScript
FACE_LEYE_CENTER = 'HwMnoteFaceLeyeCenter'
```

Left eye centered.

**Read/Write capability**: read-only

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## FACE_MOUTH_CENTER

```TypeScript
FACE_MOUTH_CENTER = 'HwMnoteFaceMouthCenter'
```

Mouth centered.

**Read/Write capability**: read-only

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## FACE_POINTER

```TypeScript
FACE_POINTER = 'HwMnoteFacePointer'
```

Face pointer.

**Read/Write capability**: read-only

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## FACE_RECT

```TypeScript
FACE_RECT = 'HwMnoteFaceRect'
```

Face rectangle.

**Read/Write capability**: read-only

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## FACE_REYE_CENTER

```TypeScript
FACE_REYE_CENTER = 'HwMnoteFaceReyeCenter'
```

Right eye centered.

**Read/Write capability**: read-only

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## FACE_SMILE_SCORE

```TypeScript
FACE_SMILE_SCORE = 'HwMnoteFaceSmileScore'
```

Smile score of for faces.

**Read/Write capability**: read-only

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## FACE_VERSION

```TypeScript
FACE_VERSION = 'HwMnoteFaceVersion'
```

Facial recognition algorithm version.

**Read/Write capability**: read-only

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## FRONT_CAMERA

```TypeScript
FRONT_CAMERA = 'HwMnoteFrontCamera'
```

Whether the front camera is used to take a selfie.

**Read/Write capability**: read-only

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## SCENE_POINTER

```TypeScript
SCENE_POINTER = 'HwMnoteScenePointer'
```

Pointer to the scene.

**Read/Write capability**: read-only

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## SCENE_VERSION

```TypeScript
SCENE_VERSION = 'HwMnoteSceneVersion'
```

Scene algorithm version.

**Read/Write capability**: read-only

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## IS_XMAGE_SUPPORTED

```TypeScript
IS_XMAGE_SUPPORTED = 'HwMnoteIsXmageSupported'
```

Whether XMAGE is supported.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## XMAGE_MODE

```TypeScript
XMAGE_MODE = 'HwMnoteXmageMode'
```

XMAGE watermark mode.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## XMAGE_LEFT

```TypeScript
XMAGE_LEFT = 'HwMnoteXmageLeft'
```

X1 coordinate of the watermark region.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## XMAGE_TOP

```TypeScript
XMAGE_TOP = 'HwMnoteXmageTop'
```

Y1 coordinate of the watermark region.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## XMAGE_RIGHT

```TypeScript
XMAGE_RIGHT = 'HwMnoteXmageRight'
```

X2 coordinate of the watermark region.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## XMAGE_BOTTOM

```TypeScript
XMAGE_BOTTOM = 'HwMnoteXmageBottom'
```

Y2 coordinate of the watermark region.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## CLOUD_ENHANCEMENT_MODE

```TypeScript
CLOUD_ENHANCEMENT_MODE = 'HwMnoteCloudEnhancementMode'
```

Cloud enhancement mode.

**Read/Write capability**: readable and writable.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## WIND_SNAPSHOT_MODE

```TypeScript
WIND_SNAPSHOT_MODE = 'HwMnoteWindSnapshotMode'
```

Motion snapshot mode.

**Read/Write capability**: read-only

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## GIF_LOOP_COUNT

```TypeScript
GIF_LOOP_COUNT = 'GIFLoopCount'
```

Number of GIF loops. The value **0** means an infinite loop, and other values means the number of loops.

**Read/Write capability**: read-only

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core
