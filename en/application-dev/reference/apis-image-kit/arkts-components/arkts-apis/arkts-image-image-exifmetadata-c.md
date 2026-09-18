# ExifMetadata

ExifMetadata implements Metadata

Exchangeable Image File Format (Exif) metadata.

**Inheritance/Implementation:** ExifMetadata implements [Metadata](arkts-image-image-metadata-i.md)

**Since:** 23

**System capability:** SystemCapability.Multimedia.Image.Core

## Modules to Import

```TypeScript
import { image } from '@kit.ImageKit';
```

## clone

```TypeScript
clone(): Promise<ExifMetadata>
```

Clones the Exif metadata. This API returns the result asynchronously through a promise.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ExifMetadata](arkts-image-image-exifmetadata-c.md)&gt; | Promise used to return the Exif metadata instance if the operation is successful. |

## createInstance

```TypeScript
static createInstance(): ExifMetadata
```

Creates an empty [ExifMetadata](arkts-image-image-exifmetadata-c.md) instance.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

**Return value:**

| Type | Description |
| --- | --- |
| [ExifMetadata](arkts-image-image-exifmetadata-c.md) | Empty **ExifMetadata** instance. |

## getAllProperties

```TypeScript
getAllProperties(): Promise<Record<string, string | null>>
```

Obtains all properties and their values from the image metadata. This API returns the result asynchronously through a promise.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Record&lt;string, string &#124; null&gt;&gt; | Promise used to return the values of all properties. |

## getBlob

```TypeScript
getBlob(): Promise<ArrayBuffer>
```

Obtains the metadata in binary format. This API uses a promise to return the result.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;ArrayBuffer&gt; | Promise that returns the binary data of the metadata. |

## getProperties

```TypeScript
getProperties(key: Array<string>): Promise<Record<string, string | null>>
```

Obtains the property values from image metadata. This API returns the result asynchronously through a promise.

For details about the properties, see [PropertyKey](arkts-image-image-propertykey-e.md).

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | Array&lt;string&gt; | Yes | Names of the properties to query. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Record&lt;string, string &#124; null&gt;&gt; | Promise used to return the obtained image metadata property values. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7600202](../errorcode-image.md#7600202-unsupported-metadata-readwrite-operation) | Unsupported metadata. Possible causes: unsupported metadata type. |

## setBlob

```TypeScript
setBlob(blob: ArrayBuffer): Promise<void>
```

Replaces the current metadata with binary data. This API uses a promise to return the result.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| blob | ArrayBuffer | Yes | Binary data used to replace the metadata. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7600206](../errorcode-image.md#7600206-invalid-parameter) | Invalid parameter. Possible causes: The blob is empty or has a length of 0. |

## setProperties

```TypeScript
setProperties(records: Record<string, string | null>): Promise<void>
```

Sets the values of specified properties in image metadata in batches. This API returns the result asynchronously through a promise.

For details about the properties, see [PropertyKey](arkts-image-image-propertykey-e.md).

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| records | Record&lt;string, string &#124; null&gt; | Yes | Set of key-value pairs representing properties and corresponding values of the **ExifMetadata** object. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7600202](../errorcode-image.md#7600202-unsupported-metadata-readwrite-operation) | Unsupported metadata. Possible causes: unsupported metadata type. |

## apertureValue

```TypeScript
apertureValue?: number
```

Lens aperture. The unit is APEX.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## artist

```TypeScript
artist?: string
```

Name of the person who creates the image.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## bitsPerSample

```TypeScript
bitsPerSample?: number[]
```

Number of bits for each pixel component. For example, RGB has 3 components with a format of 8,8,8.

**Type:** number[]

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## bodySerialNumber

```TypeScript
bodySerialNumber?: string
```

Serial number of the camera body.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## brightnessValue

```TypeScript
brightnessValue?: number
```

Image brightness. The unit is APEX.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## cameraOwnerName

```TypeScript
cameraOwnerName?: string
```

Name of the camera owner.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## cfaPattern

```TypeScript
cfaPattern?: ArrayBuffer
```

Color filter array (CFA) geometric pattern of the image sensor.

**Type:** ArrayBuffer

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## colorSpace

```TypeScript
colorSpace?: number
```

Color space information, which is usually recorded as a color space descriptor. The value range is all integers.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## componentsConfiguration

```TypeScript
componentsConfiguration?: string
```

Information about the compressed data.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## compositeImage

```TypeScript
compositeImage?: number
```

Whether the image is a composite image. The value range is all integers.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## compressedBitsPerPixel

```TypeScript
compressedBitsPerPixel?: number
```

Image compression scheme. The unit is bit/pixel.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## compression

```TypeScript
compression?: number
```

Algorithm standard for image compression. The value range is all integers.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## contrast

```TypeScript
contrast?: number
```

Contrast optimization policy applied by the camera. For example, standard processing and contrast reduction. The value range is all integers.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## copyright

```TypeScript
copyright?: string
```

Copyright notice of the image.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## customRendered

```TypeScript
customRendered?: number
```

Special processing of image data, such as HDR composition and AI scene enhancement. The value range is all integers.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## dateTime

```TypeScript
dateTime?: string
```

Date and time when the image is created. In this standard, it refers to the file date and time. The value format is *YYYY:MM:DD HH:MM:SS* (24-hour clock). For example, 2025:12:15 18:44:59.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## dateTimeDigitized

```TypeScript
dateTimeDigitized?: string
```

Date and time when the image is stored as digital data. For example, if a DSC captures an image and records the file at the same time, the values of **DateTimeOriginal** and **DateTimeDigitized** are the same. The value format is *YYYY:MM:DD HH:MM:SS* (24-hour clock).

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## dateTimeOriginal

```TypeScript
dateTimeOriginal?: string
```

Date and time when the original image data is generated. For a digital still camera (DSC), the date and time when a photo is taken are recorded. The value format is *YYYY:MM:DD HH:MM:SS* (24-hour clock).

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## deviceSettingDescription

```TypeScript
deviceSettingDescription?: ArrayBuffer
```

Capture condition information of a specific camera model.

**Type:** ArrayBuffer

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## digitalZoomRatio

```TypeScript
digitalZoomRatio?: number
```

Digital zoom ratio used when the image is captured.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## exifVersion

```TypeScript
exifVersion?: string
```

Version of the supported Exif standard.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## exposureBiasValue

```TypeScript
exposureBiasValue?: number
```

Exposure bias.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## exposureIndex

```TypeScript
exposureIndex?: number
```

Exposure index selected at the time the image is captured.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## exposureMode

```TypeScript
exposureMode?: number
```

Exposure mode. The value range is all integers.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## exposureProgram

```TypeScript
exposureProgram?: number
```

Class used for exposure setting when the camera captures a photo. The value range is all integers.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## exposureTime

```TypeScript
exposureTime?: number
```

Exposure time.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## fileSource

```TypeScript
fileSource?: ArrayBuffer
```

Image source.

**Type:** ArrayBuffer

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## flash

```TypeScript
flash?: number
```

Flash. The value range is all integers.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## flashEnergy

```TypeScript
flashEnergy?: number
```

Flash energy at the time the image is captured. The unit is beam candlepower seconds (BCPS).

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## flashpixVersion

```TypeScript
flashpixVersion?: string
```

FlashPix format version supported by the FlashPix Extension Resource (FPXR), which is used to enhance device compatibility.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## fNumber

```TypeScript
fNumber?: number
```

F number, for example, f/1.8.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## focalLength

```TypeScript
focalLength?: number
```

Focal length of the lens, in milliseconds.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## focalLengthIn35mmFilm

```TypeScript
focalLengthIn35mmFilm?: number
```

Focal length of the 35 mm film. The value should be an integer.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## focalPlaneResolutionUnit

```TypeScript
focalPlaneResolutionUnit?: number
```

Measurement unit of **FocalPlaneXResolution** and **FocalPlaneYResolution**. The value range is all integers.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## focalPlaneXResolution

```TypeScript
focalPlaneXResolution?: number
```

Number of pixels per unit physical length in the X-axis of the sensor's physical plane.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## focalPlaneYResolution

```TypeScript
focalPlaneYResolution?: number
```

Number of pixels per unit physical length in the Y-axis of the sensor's physical plane.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## gainControl

```TypeScript
gainControl?: number
```

Degree of overall image gain adjustment. The value range is all integers.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## gamma

```TypeScript
gamma?: number
```

Gamma value of each component.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## gpsAltitude

```TypeScript
gpsAltitude?: number
```

GPS altitude based on **GPSAltitudeRef**.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## gpsAltitudeRef

```TypeScript
gpsAltitudeRef?: number
```

GPS altitude reference. The value range is all integers.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## gpsAreaInformation

```TypeScript
gpsAreaInformation?: string
```

String of the GPS area name.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## gpsDateStamp

```TypeScript
gpsDateStamp?: string
```

GPS date stamp.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## gpsDestBearing

```TypeScript
gpsDestBearing?: number
```

Bearing to the destination.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## gpsDestBearingRef

```TypeScript
gpsDestBearingRef?: string
```

Bearing reference to the destination.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## gpsDestDistance

```TypeScript
gpsDestDistance?: number
```

Distance to the destination.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## gpsDestDistanceRef

```TypeScript
gpsDestDistanceRef?: string
```

Unit used to express the distance to the destination.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## gpsDestLatitude

```TypeScript
gpsDestLatitude?: number[]
```

Latitude of the destination.

**Type:** number[]

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## gpsDestLatitudeRef

```TypeScript
gpsDestLatitudeRef?: string
```

Latitude reference of the destination.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## gpsDestLongitude

```TypeScript
gpsDestLongitude?: number[]
```

Longitude of the destination.

**Type:** number[]

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## gpsDestLongitudeRef

```TypeScript
gpsDestLongitudeRef?: string
```

Longitude reference of the destination.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## gpsDifferential

```TypeScript
gpsDifferential?: number
```

Whether differential correction has been applied to the GPS data, which is crucial for precise positioning accuracy. The value range is all integers.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## gpsDop

```TypeScript
gpsDop?: number
```

Dilution of Precision (DOP) of the GPS data.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## gpsHPositioningError

```TypeScript
gpsHPositioningError?: number
```

Horizontal positioning error, in meters.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## gpsImgDirection

```TypeScript
gpsImgDirection?: number
```

Image orientation at the time of capture.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## gpsImgDirectionRef

```TypeScript
gpsImgDirectionRef?: string
```

Reference of the image orientation.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## gpsLatitude

```TypeScript
gpsLatitude?: number[]
```

GPS latitude. The latitude is represented by three RATIONAL values (numeric values stored in fractional form), corresponding to degrees, minutes, and seconds, in the **dd/1, mm/1, ss/1** format. When using degrees and minutes, the minutes are stored with up to two decimal places, in the **dd/1, mmmm/100, 0/1** format.

**Type:** number[]

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## gpsLatitudeRef

```TypeScript
gpsLatitudeRef?: string
```

GPS latitude reference. For example, **N** indicates north latitude, and **S** indicates south latitude.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## gpsLongitude

```TypeScript
gpsLongitude?: number[]
```

GPS longitude. The longitude is represented by three RATIONAL values (numeric values stored in fractional form), corresponding to degrees, minutes, and seconds, in the **dd/1, mm/1, ss/1** format. When using degrees and minutes, the minutes are stored with up to two decimal places, in the **dd/1, mmmm/100, 0/1** format.

**Type:** number[]

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## gpsLongitudeRef

```TypeScript
gpsLongitudeRef?: string
```

GPS longitude reference. For example, **E** indicates east longitude, and **W** indicates west longitude.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## gpsMapDatum

```TypeScript
gpsMapDatum?: string
```

Geodetic data used by the GPS receiver.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## gpsMeasureMode

```TypeScript
gpsMeasureMode?: string
```

GPS measurement mode.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## gpsProcessingMethod

```TypeScript
gpsProcessingMethod?: string
```

Name of the positioning method.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## gpsSatellites

```TypeScript
gpsSatellites?: string
```

GPS satellite used for measurement. Generally, the value is the GPS satellite's pseudo-random noise (PRN) number.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## gpsSpeed

```TypeScript
gpsSpeed?: number
```

Speed of the GPS receiver.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## gpsSpeedRef

```TypeScript
gpsSpeedRef?: string
```

Speed unit of the GPS receiver.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## gpsStatus

```TypeScript
gpsStatus?: string
```

Status of the GPS receiver when the image is recorded.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## gpsTimestamp

```TypeScript
gpsTimestamp?: number[]
```

GPS timestamp.

**Type:** number[]

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## gpsTrack

```TypeScript
gpsTrack?: number
```

Movement direction of the GPS receiver.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## gpsTrackRef

```TypeScript
gpsTrackRef?: string
```

Reference for the GPS receiver movement direction.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## gpsVersionID

```TypeScript
gpsVersionID?: number[]
```

GPS information format version identifier.

**Type:** number[]

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## imageDescription

```TypeScript
imageDescription?: string
```

Image description.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## imageLength

```TypeScript
imageLength?: number
```

Image length. The unit is px.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## imageUniqueId

```TypeScript
imageUniqueId?: string
```

Unique ID assigned to each image.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## imageWidth

```TypeScript
imageWidth?: number
```

Image width. The unit is px.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## isoSpeedLatitudeyyy

```TypeScript
isoSpeedLatitudeyyy?: number
```

Maximum dynamic range recordable by the camera sensor in a single exposure. The unit is EV. The value should be an integer.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## isoSpeedLatitudezzz

```TypeScript
isoSpeedLatitudezzz?: number
```

Highlight retention capacity of the camera sensor in overexposure. The unit is EV. The value should be an integer.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## isoSpeedRatings

```TypeScript
isoSpeedRatings?: number
```

ISO speed and latitude of the camera or input device, which are specified in ISO 12232. The value range is all integers.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## jpegInterchangeFormat

```TypeScript
jpegInterchangeFormat?: number
```

Start of Image (SOI) marker of the JPEG bitstream in interchange format. The value range is all integers.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## jpegInterchangeFormatLength

```TypeScript
jpegInterchangeFormatLength?: number
```

Number of bytes in the JPEG stream. The value range is all integers.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## lensMake

```TypeScript
lensMake?: string
```

Manufacturer of the lens.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## lensModel

```TypeScript
lensModel?: string
```

Model of the lens.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## lensSerialNumber

```TypeScript
lensSerialNumber?: string
```

Serial number of the lens.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## lensSpecification

```TypeScript
lensSpecification?: number[]
```

Specifications of the lens.

**Type:** number[]

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## lightSource

```TypeScript
lightSource?: number
```

Light source. The value range is all integers.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## make

```TypeScript
make?: string
```

Manufacturer name of the capture device.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## makerNote

```TypeScript
makerNote?: ArrayBuffer
```

Information required by the Exif/Design rule for Camera File system (DCF) writer manufacturer.

**Type:** ArrayBuffer

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## maxApertureValue

```TypeScript
maxApertureValue?: number
```

Minimum aperture value of the lens.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## meteringMode

```TypeScript
meteringMode?: number
```

Metering mode. The value range is all integers.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## model

```TypeScript
model?: string
```

Camera model.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## newSubfileType

```TypeScript
newSubfileType?: number
```

Data type of a subfile (for example, basic types such as text or image, rather than specific storage formats). The value range is all integers.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## oecf

```TypeScript
oecf?: ArrayBuffer
```

Opto-Electric Conversion Function (OECF) specified in ISO 14524.

**Type:** ArrayBuffer

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## offsetTime

```TypeScript
offsetTime?: string
```

Geographical time zone of the device.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## offsetTimeDigitized

```TypeScript
offsetTimeDigitized?: string
```

Coordinated Universal Time (UTC) offset at the time of image digitization, which helps to precisely adjust the timestamp.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## offsetTimeOriginal

```TypeScript
offsetTimeOriginal?: string
```

Geographical time zone of the device.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## orientation

```TypeScript
orientation?: Orientation
```

Image orientation.

**Type:** [Orientation](arkts-image-image-orientation-e.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## photographicSensitivity

```TypeScript
photographicSensitivity?: number[]
```

Sensitivity of the camera or input device during image capture.

**Type:** number[]

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## photometricInterpretation

```TypeScript
photometricInterpretation?: number
```

Pixel composition, such as RGB (Red, Green, Blue) and YCbCr (Luma, Blue-difference Chroma, Red-difference Chroma). The value range is all integers.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## photoMode

```TypeScript
photoMode?: number
```

Image mode. The value range is all integers.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## pixelXDimension

```TypeScript
pixelXDimension?: number
```

Image size on the X axis (horizontal axis in a two-dimensional coordinate system). The value range is all integers.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## pixelYDimension

```TypeScript
pixelYDimension?: number
```

Image size on the Y axis (vertical axis in a two-dimensional coordinate system). The value range is all integers.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## planarConfiguration

```TypeScript
planarConfiguration?: number
```

Whether the pixel components are recorded in chunked or planar format. The value range is all integers.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## primaryChromaticities

```TypeScript
primaryChromaticities?: number[]
```

Chromaticity of the image primaries.

**Type:** number[]

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## recommendedExposureIndex

```TypeScript
recommendedExposureIndex?: number
```

GPS measurement mode. The value range is all integers.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## referenceBlackWhite

```TypeScript
referenceBlackWhite?: number[]
```

Reference black point value and white point value.

**Type:** number[]

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## relatedSoundFile

```TypeScript
relatedSoundFile?: string
```

Name of the audio file related to the image data.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## resolutionUnit

```TypeScript
resolutionUnit?: number
```

Unit of the image resolution in the width and height directions. The value range is all integers.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## rowsPerStrip

```TypeScript
rowsPerStrip?: number
```

Number of rows per image strip. The value range is all integers.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## samplesPerPixel

```TypeScript
samplesPerPixel?: number
```

Number of color components per pixel, applicable to RGB and YCbCr color models. Since both the models are three-component models (three color channels, or one luminance component plus two chroma components), the standard value for this property is 3. For JPEG-compressed images, this property will be replaced by the corresponding JPEG marker. The value range is all integers.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## saturation

```TypeScript
saturation?: number
```

Color saturation adjustment policy applied by the camera. For example, standard processing and saturation reduction. The value range is all integers.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## sceneCaptureType

```TypeScript
sceneCaptureType?: number
```

Type of the scene that is captured. The value range is all integers.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## sceneType

```TypeScript
sceneType?: ArrayBuffer
```

Scene type.

**Type:** ArrayBuffer

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## sensingMethod

```TypeScript
sensingMethod?: number
```

Type of the image sensor on the camera. The value range is all integers.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## sensitivityType

```TypeScript
sensitivityType?: number
```

Sensitivity type. The value range is all integers.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## sharpness

```TypeScript
sharpness?: number
```

Edge enhancement processing method applied by the camera. For example, weak sharpening and standard sharpening. The value range is all integers.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## shutterSpeedValue

```TypeScript
shutterSpeedValue?: number
```

Shutter speed, expressed as an Additive System of Photographic Exposure (APEX) value.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## software

```TypeScript
software?: string
```

Name and version number of the software used to create the image.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## sourceExposureTimesOfCompositeImage

```TypeScript
sourceExposureTimesOfCompositeImage?: ArrayBuffer
```

Exposure time of source images for the composite image, for example, 1/33 s.

**Type:** ArrayBuffer

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## sourceImageNumberOfCompositeImage

```TypeScript
sourceImageNumberOfCompositeImage?: number[]
```

Number of source images of the composite image.

**Type:** number[]

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## spatialFrequencyResponse

```TypeScript
spatialFrequencyResponse?: ArrayBuffer
```

Spatial frequency table of the camera or input device.

**Type:** ArrayBuffer

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## spectralSensitivity

```TypeScript
spectralSensitivity?: string
```

Spectral sensitivity of each channel of the camera.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## standardOutputSensitivity

```TypeScript
standardOutputSensitivity?: number
```

Standard output sensitivity. The value range is all integers.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## stripByteCounts

```TypeScript
stripByteCounts?: number[]
```

Number of bytes in each strip after compression.

**Type:** number[]

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## stripOffsets

```TypeScript
stripOffsets?: number[]
```

Strip storage offset of the image data, in bytes. To improve the efficiency of large image access, the original pixel data is divided into multiple contiguous blocks (called strips). This property stores the starting offset of each strip in the file sequentially.

**Type:** number[]

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## subfileType

```TypeScript
subfileType?: number
```

Data type of a subfile. It has been deprecated. Use **newSubfileType** instead. The value range is all integers.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## subjectArea

```TypeScript
subjectArea?: number[]
```

Location and area of the main object in the entire scene.

**Type:** number[]

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## subjectDistance

```TypeScript
subjectDistance?: number
```

Distance from the capture device to the photographed object, in meters.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## subjectDistanceRange

```TypeScript
subjectDistanceRange?: number
```

Distance range to the object. The value range is all integers.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## subjectLocation

```TypeScript
subjectLocation?: number[]
```

Pixel coordinates of the primary object in the image (based on the origin in the upper left corner).

**Type:** number[]

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## subsecTime

```TypeScript
subsecTime?: string
```

Second fraction of **DateTime**.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## subsecTimeDigitized

```TypeScript
subsecTimeDigitized?: string
```

Second of **DateTimeDigitized**.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## subsecTimeOriginal

```TypeScript
subsecTimeOriginal?: string
```

Second of **DateTimeOriginal**.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## transferFunction

```TypeScript
transferFunction?: string
```

Transfer function for the image, which is usually used for color correction.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## userComment

```TypeScript
userComment?: string
```

User comments.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## whiteBalance

```TypeScript
whiteBalance?: number
```

White balance. The value range is all integers.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## whitePoint

```TypeScript
whitePoint?: number[]
```

Chromaticity of the image white point.

**Type:** number[]

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## xResolution

```TypeScript
xResolution?: number
```

Image resolution in the width direction.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## yCbCrCoefficients

```TypeScript
yCbCrCoefficients?: number[]
```

Transformation matrix coefficients for converting RGB image data to YCbCr image data.

**Type:** number[]

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## yCbCrPositioning

```TypeScript
yCbCrPositioning?: number
```

Position of chroma components relative to the luminance component. The value range is all integers.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## yCbCrSubSampling

```TypeScript
yCbCrSubSampling?: number[]
```

Sampling ratios of the chroma components and luminance component.

**Type:** number[]

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

## yResolution

```TypeScript
yResolution?: number
```

Image resolution in the height direction.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core
