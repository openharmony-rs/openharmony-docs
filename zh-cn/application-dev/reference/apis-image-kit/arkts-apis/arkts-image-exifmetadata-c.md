# ExifMetadata

ExifMetadata implements Metadata

Exif（Exchangeable image file format）元数据。

**继承/实现关系：** ExifMetadata implements [Metadata](arkts-image-metadata-i.md)

**起始版本：** 23

**系统能力：** SystemCapability.Multimedia.Image.Core

## clone

```TypeScript
clone(): Promise<ExifMetadata>
```

对Exif元数据进行克隆。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;ExifMetadata&gt; | Promise对象，成功返回Exif元数据实例。 |

## createInstance

```TypeScript
static createInstance(): ExifMetadata
```

创建一个空的[ExifMetadata](arkts-image-exifmetadata-c.md)实例。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ExifMetadata | 返回ExifMetadata的空实例。 |

## getAllProperties

```TypeScript
getAllProperties(): Promise<Record<string, string | null>>
```

获取图片中所有元数据的属性和值。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Record&lt;string, string \| null&gt;&gt; | Promise对象，返回元数据拥有的所有属性的值。 |

## getBlob

```TypeScript
getBlob(): Promise<ArrayBuffer>
```

以二进制数据的形式获取元数据。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;ArrayBuffer&gt; | Promise对象，返回元数据的二进制数据。 |

## getProperties

```TypeScript
getProperties(key: Array<string>): Promise<Record<string, string | null>>
```

获取图像的元数据属性值。使用Promise异步回调。

要查询的属性的具体信息请参考[PropertyKey](arkts-image-propertykey-e.md)。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | Array&lt;string&gt; | 是 | 要获取的值的属性名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Record&lt;string, string \| null&gt;&gt; | Promise对象，返回获取到的图像元数据属性值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600202](../errorcode-image.md#7600202-不支持的元数据读写) | Unsupported metadata. Possible causes: unsupported metadata type. |

## setBlob

```TypeScript
setBlob(blob: ArrayBuffer): Promise<void>
```

使用二进制数据替换当前元数据。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| blob | ArrayBuffer | 是 | 要替换的二进制数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600206](../errorcode-image.md#7600206-无效参数) | Invalid parameter. Possible causes: The blob is empty or has a length of 0. |

## setProperties

```TypeScript
setProperties(records: Record<string, string | null>): Promise<void>
```

批量设置图片元数据中的指定属性的值。使用Promise异步回调。

要查询的属性的具体信息请参考[PropertyKey](arkts-image-propertykey-e.md)。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| records | Record&lt;string, string \| null&gt; | 是 | 用户要修改的ExifMetadata对象的属性和键值对的集合。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600202](../errorcode-image.md#7600202-不支持的元数据读写) | Unsupported metadata. Possible causes: unsupported metadata type. |

## apertureValue

```TypeScript
apertureValue?: number
```

镜头光圈。单位为APEX。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## artist

```TypeScript
artist?: string
```

创建图像的人的姓名。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## bitsPerSample

```TypeScript
bitsPerSample?: number[]
```

像素各分量的位数。如RGB是3分量，格式是8，8，8。

**类型：** number[]

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## bodySerialNumber

```TypeScript
bodySerialNumber?: string
```

相机机身的序列号。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## brightnessValue

```TypeScript
brightnessValue?: number
```

图像的亮度值。单位为APEX。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## cameraOwnerName

```TypeScript
cameraOwnerName?: string
```

相机所有者的姓名。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## cfaPattern

```TypeScript
cfaPattern?: ArrayBuffer
```

图像传感器的滤色器阵列CFA（Color Filter Array）几何图案。

**类型：** ArrayBuffer

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## colorSpace

```TypeScript
colorSpace?: number
```

颜色空间信息标签，通常记录为颜色空间说明符。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## componentsConfiguration

```TypeScript
componentsConfiguration?: string
```

压缩数据的信息。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## compositeImage

```TypeScript
compositeImage?: number
```

指示图像是否为合成图像。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## compressedBitsPerPixel

```TypeScript
compressedBitsPerPixel?: number
```

图像压缩方案。单位为每像素比特。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## compression

```TypeScript
compression?: number
```

用于图像压缩的算法标准。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## contrast

```TypeScript
contrast?: number
```

相机应用的对比度优化策略。例如：标准处理、弱化对比度等。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## copyright

```TypeScript
copyright?: string
```

图像的版权信息。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## customRendered

```TypeScript
customRendered?: number
```

表示对图像数据的特殊处理，如HDR合成、AI场景增强。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## dateTime

```TypeScript
dateTime?: string
```

图像创建的日期和时间。

在本标准中，指文件更改的日期和时间。格式为：“YYYY:MM:DD HH:MM:SS”，时间以24小时格式显示。例如：“2025:12:15 18:44:59”。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## dateTimeDigitized

```TypeScript
dateTimeDigitized?: string
```

将图像作为数字数据存储的日期和时间。

例如，如果DSC捕获了图像，并同时记录了文件，则DateTimeOriginal和DateTimeDigitized将具有相同的内容。格式为“YYYY:MM:DD HH:MM:SS”，时间以24小时格式显示。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## dateTimeOriginal

```TypeScript
dateTimeOriginal?: string
```

生成原始图像数据的日期和时间。

对于DSC（Digital Still Camera 数码静态相机），会记录拍摄照片的日期和时间。格式为“YYYY:MM:DD HH:MM:SS”，时间以24小时格式显示。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## deviceSettingDescription

```TypeScript
deviceSettingDescription?: ArrayBuffer
```

特定相机型号的拍照条件信息。

**类型：** ArrayBuffer

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## digitalZoomRatio

```TypeScript
digitalZoomRatio?: number
```

拍摄时的数字变焦比。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## exifVersion

```TypeScript
exifVersion?: string
```

支持的Exif标准的版本。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## exposureBiasValue

```TypeScript
exposureBiasValue?: number
```

曝光偏差值。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## exposureIndex

```TypeScript
exposureIndex?: number
```

拍摄时选定的曝光指数。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## exposureMode

```TypeScript
exposureMode?: number
```

曝光模式。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## exposureProgram

```TypeScript
exposureProgram?: number
```

相机在拍摄照片时用于设置曝光的程序类。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## exposureTime

```TypeScript
exposureTime?: number
```

曝光时间。单位为秒（s）。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## fNumber

```TypeScript
fNumber?: number
```

光圈值，如f/1.8。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## fileSource

```TypeScript
fileSource?: ArrayBuffer
```

指示图像源。

**类型：** ArrayBuffer

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## flash

```TypeScript
flash?: number
```

闪光。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## flashEnergy

```TypeScript
flashEnergy?: number
```

图像捕获时的闪光灯能量。单位为光束烛光秒（BCPS，Beam Candlepower Seconds）。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## flashpixVersion

```TypeScript
flashpixVersion?: string
```

FPXR（FlashPix Extension Resource）支持的FlashPix格式版本，用于增强设备兼容性。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## focalLength

```TypeScript
focalLength?: number
```

焦距。单位为毫米（mm）。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## focalLengthIn35mmFilm

```TypeScript
focalLengthIn35mmFilm?: number
```

换算成35mm等效焦距。单位为毫米（mm）。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## focalPlaneResolutionUnit

```TypeScript
focalPlaneResolutionUnit?: number
```

FocalPlaneXResolution和FocalPlaneYResolution的测量单位。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## focalPlaneXResolution

```TypeScript
focalPlaneXResolution?: number
```

传感器物理平面X轴方向上每单位物理长度的像素数量。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## focalPlaneYResolution

```TypeScript
focalPlaneYResolution?: number
```

传感器物理平面Y轴方向上每单位物理长度的像素数量。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## gainControl

```TypeScript
gainControl?: number
```

整体图像增益调整程度。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## gamma

```TypeScript
gamma?: number
```

每个组件的伽玛值。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## gpsAltitude

```TypeScript
gpsAltitude?: number
```

基于GPSAltitudeRef中的参考高度。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## gpsAltitudeRef

```TypeScript
gpsAltitudeRef?: number
```

用于GPS的参考高度。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## gpsAreaInformation

```TypeScript
gpsAreaInformation?: string
```

GPS区域名称的字符串。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## gpsDateStamp

```TypeScript
gpsDateStamp?: string
```

GPS日期戳。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## gpsDestBearing

```TypeScript
gpsDestBearing?: number
```

到达目的地的方位。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## gpsDestBearingRef

```TypeScript
gpsDestBearingRef?: string
```

指向目的地的方位参考。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## gpsDestDistance

```TypeScript
gpsDestDistance?: number
```

到目的地的距离。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## gpsDestDistanceRef

```TypeScript
gpsDestDistanceRef?: string
```

到目标点距离的测量单位。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## gpsDestLatitude

```TypeScript
gpsDestLatitude?: number[]
```

目的地的纬度。

**类型：** number[]

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## gpsDestLatitudeRef

```TypeScript
gpsDestLatitudeRef?: string
```

指示目标点的纬度参考。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## gpsDestLongitude

```TypeScript
gpsDestLongitude?: number[]
```

目的地的经度。

**类型：** number[]

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## gpsDestLongitudeRef

```TypeScript
gpsDestLongitudeRef?: string
```

指示目标点的经度参考。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## gpsDifferential

```TypeScript
gpsDifferential?: number
```

是否对GPS数据应用了差分校正，这对精确定位精度至关重要。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## gpsDop

```TypeScript
gpsDop?: number
```

GPS数据精度DOP精度衰减因子（Dilution of Precision）。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## gpsHPositioningError

```TypeScript
gpsHPositioningError?: number
```

水平定位误差。单位为米（m）。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## gpsImgDirection

```TypeScript
gpsImgDirection?: number
```

拍摄时图像的方向。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## gpsImgDirectionRef

```TypeScript
gpsImgDirectionRef?: string
```

图像方向的参考。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## gpsLatitude

```TypeScript
gpsLatitude?: number[]
```

GPS纬度。

纬度用三个RATIONAL（分数形式存储的数值）值表示，分别是度、分和秒，格式为dd/1、mm/1、ss/1。

当使用度数和分钟时，分钟分数最多保留两位小数，格式为dd/1，mmmm/100,0/1。

**类型：** number[]

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## gpsLatitudeRef

```TypeScript
gpsLatitudeRef?: string
```

GPS纬度参考。例如，N表示北纬，S表示南纬。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## gpsLongitude

```TypeScript
gpsLongitude?: number[]
```

GPS经度。

经度用三个RATIONAL（分数形式存储的数值）值表示，分别是度、分和秒，格式为dd/1、mm/1、ss/1。

当使用度数和分钟时，分钟分数最多保留两位小数，格式为dd/1，mmmm/100，0/1。

**类型：** number[]

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## gpsLongitudeRef

```TypeScript
gpsLongitudeRef?: string
```

GPS经度参考。例如，E表示东经，W表示西经。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## gpsMapDatum

```TypeScript
gpsMapDatum?: string
```

GPS接收机使用的大地测量数据。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## gpsMeasureMode

```TypeScript
gpsMeasureMode?: string
```

GPS测量模式。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## gpsProcessingMethod

```TypeScript
gpsProcessingMethod?: string
```

记录定位方法的名称。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## gpsSatellites

```TypeScript
gpsSatellites?: string
```

用于测量的GPS卫星。通常是它的伪随机噪声码（PRN）编号。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## gpsSpeed

```TypeScript
gpsSpeed?: number
```

GPS接收器移动的速度。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## gpsSpeedRef

```TypeScript
gpsSpeedRef?: string
```

GPS接收器移动速度的单位。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## gpsStatus

```TypeScript
gpsStatus?: string
```

记录图像时GPS接收器的状态。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## gpsTimestamp

```TypeScript
gpsTimestamp?: number[]
```

GPS时间戳。

**类型：** number[]

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## gpsTrack

```TypeScript
gpsTrack?: number
```

GPS接收器移动的方向。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## gpsTrackRef

```TypeScript
gpsTrackRef?: string
```

提供GPS接收机运动方向的参考。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## gpsVersionID

```TypeScript
gpsVersionID?: number[]
```

GPS信息的格式版本标识符。

**类型：** number[]

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## imageDescription

```TypeScript
imageDescription?: string
```

图像描述。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## imageLength

```TypeScript
imageLength?: number
```

图像长度。单位为像素（px）。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## imageUniqueId

```TypeScript
imageUniqueId?: string
```

为每个图像分配的唯一标识符。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## imageWidth

```TypeScript
imageWidth?: number
```

图像宽度。单位为像素（px）。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## isoSpeedLatitudeyyy

```TypeScript
isoSpeedLatitudeyyy?: number
```

表示相机传感器在单次曝光中可记录的最大动态范围。单位为EV。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## isoSpeedLatitudezzz

```TypeScript
isoSpeedLatitudezzz?: number
```

表示相机传感器在过曝方向保护高光细节的能力边界。单位为EV。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## isoSpeedRatings

```TypeScript
isoSpeedRatings?: number
```

ISO 12232中指定的相机或输入设备的ISO速度和ISO纬度。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## jpegInterchangeFormat

```TypeScript
jpegInterchangeFormat?: number
```

JPEG交换格式比特流的SOI（Start of Image）标记。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## jpegInterchangeFormatLength

```TypeScript
jpegInterchangeFormatLength?: number
```

JPEG流的字节数。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## lensMake

```TypeScript
lensMake?: string
```

镜头的制造商。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## lensModel

```TypeScript
lensModel?: string
```

镜头的型号名称。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## lensSerialNumber

```TypeScript
lensSerialNumber?: string
```

镜头的序列号。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## lensSpecification

```TypeScript
lensSpecification?: number[]
```

所用镜头的规格。

**类型：** number[]

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## lightSource

```TypeScript
lightSource?: number
```

光源。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## make

```TypeScript
make?: string
```

拍摄设备的品牌制造商名称。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## makerNote

```TypeScript
makerNote?: ArrayBuffer
```

Exif/相机文件系统设计规则DCF（Design rule for Camera File system）写入器制造商记录所需信息的标签。

**类型：** ArrayBuffer

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## maxApertureValue

```TypeScript
maxApertureValue?: number
```

镜头的最小光圈值。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## meteringMode

```TypeScript
meteringMode?: number
```

测光模式。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## model

```TypeScript
model?: string
```

相机型号。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## newSubfileType

```TypeScript
newSubfileType?: number
```

表示该子文件的数据类型（例如文本/图像等基本类型，而非具体存储格式）。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## oecf

```TypeScript
oecf?: ArrayBuffer
```

ISO 14524中规定的光电转换函数（OECF）。

**类型：** ArrayBuffer

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## offsetTime

```TypeScript
offsetTime?: string
```

作为DateTime标签的补充元数据，解决因地理时区变化导致的时间戳歧义问题。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## offsetTimeDigitized

```TypeScript
offsetTimeDigitized?: string
```

记录图像数字化时的UTC协调世界时（Coordinated Universal Time）偏移，有助于精确调整时间戳。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## offsetTimeOriginal

```TypeScript
offsetTimeOriginal?: string
```

设备的地理时区位置。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## orientation

```TypeScript
orientation?: Orientation
```

图像方向。

**类型：** Orientation

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## photoMode

```TypeScript
photoMode?: number
```

照片模式。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## photographicSensitivity

```TypeScript
photographicSensitivity?: number[]
```

拍摄图像时相机或输入设备的灵敏度。

**类型：** number[]

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## photometricInterpretation

```TypeScript
photometricInterpretation?: number
```

像素组成，如RGB（红绿蓝，Red Green Blue）和YCbCr（亮度-蓝色色差-红色色差，Luma-Chrominance）。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## pixelXDimension

```TypeScript
pixelXDimension?: number
```

图像在X轴上的（二维坐标系中的Horizontal Axis）尺寸。单位为像素（px）。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## pixelYDimension

```TypeScript
pixelYDimension?: number
```

图像在Y轴上的（二维坐标系中的Vertical Axis）尺寸。单位为像素（px）。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## planarConfiguration

```TypeScript
planarConfiguration?: number
```

指示像素分量是以块状或平面格式记录。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## primaryChromaticities

```TypeScript
primaryChromaticities?: number[]
```

图像原色的色度。

**类型：** number[]

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## recommendedExposureIndex

```TypeScript
recommendedExposureIndex?: number
```

推荐曝光指数。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## referenceBlackWhite

```TypeScript
referenceBlackWhite?: number[]
```

参考黑点值和白点值。

**类型：** number[]

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## relatedSoundFile

```TypeScript
relatedSoundFile?: string
```

与图像数据相关的音频文件的名称。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## resolutionUnit

```TypeScript
resolutionUnit?: number
```

用于测量宽度方向上的图像分辨率和高度方向上的图像分辨率的单位。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## rowsPerStrip

```TypeScript
rowsPerStrip?: number
```

每条图像数据的行数。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## samplesPerPixel

```TypeScript
samplesPerPixel?: number
```

记录每个像素的颜色分量数量，适用于RGB（红绿蓝，Red Green Blue）和YCbCr（亮度-蓝色色差-红色色差，Luma-Chrominance）色彩模型。

由于这两种模型都是三分量模型（一个亮度分量加两个色度分量，或三个颜色通道），因此该标签的标准值为3。

对于JPEG压缩图像，此标签将会被对应的JPEG标记替换。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## saturation

```TypeScript
saturation?: number
```

相机应用的色彩饱和度调节策略。例如：标准、降饱和模式等。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## sceneCaptureType

```TypeScript
sceneCaptureType?: number
```

拍摄的场景类型。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## sceneType

```TypeScript
sceneType?: ArrayBuffer
```

场景类型。

**类型：** ArrayBuffer

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## sensingMethod

```TypeScript
sensingMethod?: number
```

摄像头的图像传感器类型。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## sensitivityType

```TypeScript
sensitivityType?: number
```

灵敏度类型。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## sharpness

```TypeScript
sharpness?: number
```

相机应用的边缘增强处理方式。例如：弱锐化、标准锐化等。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## shutterSpeedValue

```TypeScript
shutterSpeedValue?: number
```

快门速度，表示为摄影曝光相加系统值APEX（Additive System of Photographic Exposure）。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## software

```TypeScript
software?: string
```

用于生成图像的软件名称和版本。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## sourceExposureTimesOfCompositeImage

```TypeScript
sourceExposureTimesOfCompositeImage?: ArrayBuffer
```

合成图像的源图像的曝光时间，例如1/33秒。

**类型：** ArrayBuffer

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## sourceImageNumberOfCompositeImage

```TypeScript
sourceImageNumberOfCompositeImage?: number[]
```

用于合成图像的源图像数量。

**类型：** number[]

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## spatialFrequencyResponse

```TypeScript
spatialFrequencyResponse?: ArrayBuffer
```

相机或输入设备空间频率表。

**类型：** ArrayBuffer

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## spectralSensitivity

```TypeScript
spectralSensitivity?: string
```

指示相机每个通道的光谱灵敏度。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## standardOutputSensitivity

```TypeScript
standardOutputSensitivity?: number
```

标准输出灵敏度。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## stripByteCounts

```TypeScript
stripByteCounts?: number[]
```

压缩后每个条带中的字节数。

**类型：** number[]

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## stripOffsets

```TypeScript
stripOffsets?: number[]
```

图像数据的分块存储偏移量，单位为字节（Byte）。

为提高大图像访问效率，原始像素数据被分割为多个连续区块（称为条带）。

此标签按顺序存储每个条带在文件中的起始位置偏移量。

**类型：** number[]

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## subfileType

```TypeScript
subfileType?: number
```

已弃用标签，表示该子文件中的数据类型。请使用newSubfileType替代。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## subjectArea

```TypeScript
subjectArea?: number[]
```

用于指示主要对象在整个场景中的位置和区域。

**类型：** number[]

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## subjectDistance

```TypeScript
subjectDistance?: number
```

拍照设备到被摄体的距离。单位为米（m）。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## subjectDistanceRange

```TypeScript
subjectDistanceRange?: number
```

指示到对象的距离范围。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## subjectLocation

```TypeScript
subjectLocation?: number[]
```

图像中主体的像素坐标（基于左上角原点）。

**类型：** number[]

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## subsecTime

```TypeScript
subsecTime?: string
```

记录DateTime标记的秒分数的标记。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## subsecTimeDigitized

```TypeScript
subsecTimeDigitized?: string
```

记录DateTimeDigitized标记的秒数。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## subsecTimeOriginal

```TypeScript
subsecTimeOriginal?: string
```

记录DateTimeOriginal标记的秒数。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## transferFunction

```TypeScript
transferFunction?: string
```

图像的传递函数，通常用于颜色校正。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## userComment

```TypeScript
userComment?: string
```

用户评论。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## whiteBalance

```TypeScript
whiteBalance?: number
```

白平衡。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## whitePoint

```TypeScript
whitePoint?: number[]
```

图像白点的色度。

**类型：** number[]

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## xResolution

```TypeScript
xResolution?: number
```

宽度方向上的图像分辨率。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## yCbCrCoefficients

```TypeScript
yCbCrCoefficients?: number[]
```

用于将RGB图像数据转换为YCbCr图像数据的变换矩阵系数。

**类型：** number[]

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## yCbCrPositioning

```TypeScript
yCbCrPositioning?: number
```

色度分量相对于亮度分量的位置。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## yCbCrSubSampling

```TypeScript
yCbCrSubSampling?: number[]
```

色度分量与亮度分量的采样比。

**类型：** number[]

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

## yResolution

```TypeScript
yResolution?: number
```

高度方向上的图像分辨率。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

