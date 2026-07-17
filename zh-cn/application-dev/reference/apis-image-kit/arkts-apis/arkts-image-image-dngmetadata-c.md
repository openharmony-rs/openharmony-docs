# DngMetadata

Dng图像元数据类，用于存储图像的元数据。

**起始版本：** 24

<!--Device-image-class DngMetadata--><!--Device-image-class DngMetadata-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## 导入模块

```TypeScript
import { image } from '@kit.ImageKit';
```

## activeArea

```TypeScript
readonly activeArea?: number[]
```

有效图像区域。

**类型：** number[]

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly activeArea?: int[]--><!--Device-DngMetadata-readonly activeArea?: int[]-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## analogBalance

```TypeScript
readonly analogBalance?: number[]
```

模拟增益平衡系数。

**类型：** number[]

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly analogBalance?: double[]--><!--Device-DngMetadata-readonly analogBalance?: double[]-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## antiAliasStrength

```TypeScript
readonly antiAliasStrength?: number
```

抗锯齿滤波器强度。

**类型：** number

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly antiAliasStrength?: double--><!--Device-DngMetadata-readonly antiAliasStrength?: double-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## asShotICCProfile

```TypeScript
readonly asShotICCProfile?: ArrayBuffer
```

拍摄时使用的ICC色彩配置文件。

**类型：** ArrayBuffer

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly asShotICCProfile?: ArrayBuffer--><!--Device-DngMetadata-readonly asShotICCProfile?: ArrayBuffer-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## asShotNeutral

```TypeScript
readonly asShotNeutral?: number[]
```

拍摄时的中性白点。

**类型：** number[]

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly asShotNeutral?: double[]--><!--Device-DngMetadata-readonly asShotNeutral?: double[]-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## asShotPreProfileMatrix

```TypeScript
readonly asShotPreProfileMatrix?: number[]
```

应用ICC配置文件前的预变换矩阵。

**类型：** number[]

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly asShotPreProfileMatrix?: double[]--><!--Device-DngMetadata-readonly asShotPreProfileMatrix?: double[]-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## asShotProfileName

```TypeScript
readonly asShotProfileName?: string
```

拍摄时使用的配置文件名称。

**类型：** string

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly asShotProfileName?: string--><!--Device-DngMetadata-readonly asShotProfileName?: string-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## asShotWhiteXY

```TypeScript
readonly asShotWhiteXY?: number[]
```

拍摄时白点的CIE（1931色彩空间） x-y色度坐标。

**类型：** number[]

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly asShotWhiteXY?: double[]--><!--Device-DngMetadata-readonly asShotWhiteXY?: double[]-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## baselineExposure

```TypeScript
readonly baselineExposure?: number
```

基准曝光补偿值，单位：EV。

**类型：** number

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly baselineExposure?: double--><!--Device-DngMetadata-readonly baselineExposure?: double-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## baselineExposureOffset

```TypeScript
readonly baselineExposureOffset?: number
```

基准曝光偏移量，单位：EV。

**类型：** number

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly baselineExposureOffset?: double--><!--Device-DngMetadata-readonly baselineExposureOffset?: double-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## baselineNoise

```TypeScript
readonly baselineNoise?: number
```

基准噪声水平。

**类型：** number

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly baselineNoise?: double--><!--Device-DngMetadata-readonly baselineNoise?: double-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## baselineSharpness

```TypeScript
readonly baselineSharpness?: number
```

基准锐度增益。

**类型：** number

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly baselineSharpness?: double--><!--Device-DngMetadata-readonly baselineSharpness?: double-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## bayerGreenSplit

```TypeScript
readonly bayerGreenSplit?: number
```

Bayer图像中两个绿色通道的分离程度。

**类型：** number

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly bayerGreenSplit?: int--><!--Device-DngMetadata-readonly bayerGreenSplit?: int-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## bestQualityScale

```TypeScript
readonly bestQualityScale?: number
```

最佳画质缩放比例。

**类型：** number

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly bestQualityScale?: double--><!--Device-DngMetadata-readonly bestQualityScale?: double-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## blackLevel

```TypeScript
readonly blackLevel?: number[]
```

零光照下的编码电平。

**类型：** number[]

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly blackLevel?: double[]--><!--Device-DngMetadata-readonly blackLevel?: double[]-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## blackLevelDeltaH

```TypeScript
readonly blackLevelDeltaH?: number[]
```

水平方向黑电平校正增量。

**类型：** number[]

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly blackLevelDeltaH?: double[]--><!--Device-DngMetadata-readonly blackLevelDeltaH?: double[]-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## blackLevelDeltaV

```TypeScript
readonly blackLevelDeltaV?: number[]
```

垂直方向黑电平校正增量。

**类型：** number[]

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly blackLevelDeltaV?: double[]--><!--Device-DngMetadata-readonly blackLevelDeltaV?: double[]-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## blackLevelRepeatDim

```TypeScript
readonly blackLevelRepeatDim?: number[]
```

黑电平重复维度。

**类型：** number[]

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly blackLevelRepeatDim?: int[]--><!--Device-DngMetadata-readonly blackLevelRepeatDim?: int[]-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## calibrationIlluminant1

```TypeScript
readonly calibrationIlluminant1?: number
```

第一校准光源类型。

**类型：** number

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly calibrationIlluminant1?: int--><!--Device-DngMetadata-readonly calibrationIlluminant1?: int-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## calibrationIlluminant2

```TypeScript
readonly calibrationIlluminant2?: number
```

第二校准光源类型。

**类型：** number

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly calibrationIlluminant2?: int--><!--Device-DngMetadata-readonly calibrationIlluminant2?: int-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## cameraCalibration1

```TypeScript
readonly cameraCalibration1?: number[]
```

第一校准光源下的相机校准矩阵。

**类型：** number[]

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly cameraCalibration1?: double[]--><!--Device-DngMetadata-readonly cameraCalibration1?: double[]-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## cameraCalibration2

```TypeScript
readonly cameraCalibration2?: number[]
```

第二校准光源下的相机校准矩阵。

**类型：** number[]

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly cameraCalibration2?: double[]--><!--Device-DngMetadata-readonly cameraCalibration2?: double[]-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## cameraCalibrationSignature

```TypeScript
readonly cameraCalibrationSignature?: string
```

相机校准签名。

**类型：** string

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly cameraCalibrationSignature?: string--><!--Device-DngMetadata-readonly cameraCalibrationSignature?: string-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## cameraSerialNumber

```TypeScript
readonly cameraSerialNumber?: string
```

相机序列号。

**类型：** string

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly cameraSerialNumber?: string--><!--Device-DngMetadata-readonly cameraSerialNumber?: string-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## cfaLayout

```TypeScript
readonly cfaLayout?: number
```

CFA（Color Filter Array）布局类型。

**类型：** number

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly cfaLayout?: int--><!--Device-DngMetadata-readonly cfaLayout?: int-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## cfaPlaneColor

```TypeScript
readonly cfaPlaneColor?: number[]
```

CFA（Color Filter Array）各平面的颜色通道定义。

**类型：** number[]

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly cfaPlaneColor?: int[]--><!--Device-DngMetadata-readonly cfaPlaneColor?: int[]-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## chromaBlurRadius

```TypeScript
readonly chromaBlurRadius?: number
```

色度模糊半径。单位：像素（px）。

**类型：** number

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly chromaBlurRadius?: double--><!--Device-DngMetadata-readonly chromaBlurRadius?: double-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## colorMatrix1

```TypeScript
readonly colorMatrix1?: number[]
```

第一校准光源下的色彩变换矩阵。

**类型：** number[]

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly colorMatrix1?: double[]--><!--Device-DngMetadata-readonly colorMatrix1?: double[]-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## colorMatrix2

```TypeScript
readonly colorMatrix2?: number[]
```

第二校准光源下的色彩变换矩阵。

**类型：** number[]

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly colorMatrix2?: double[]--><!--Device-DngMetadata-readonly colorMatrix2?: double[]-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## colorimetricReference

```TypeScript
readonly colorimetricReference?: number
```

色度参考标准。

**类型：** number

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly colorimetricReference?: int--><!--Device-DngMetadata-readonly colorimetricReference?: int-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## currentICCProfile

```TypeScript
readonly currentICCProfile?: ArrayBuffer
```

当前使用的ICC色彩配置文件。

**类型：** ArrayBuffer

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly currentICCProfile?: ArrayBuffer--><!--Device-DngMetadata-readonly currentICCProfile?: ArrayBuffer-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## currentPreProfileMatrix

```TypeScript
readonly currentPreProfileMatrix?: number[]
```

当前ICC配置文件前的预变换矩阵。

**类型：** number[]

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly currentPreProfileMatrix?: double[]--><!--Device-DngMetadata-readonly currentPreProfileMatrix?: double[]-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## defaultBlackRender

```TypeScript
readonly defaultBlackRender?: number
```

默认黑场渲染方式。

**类型：** number

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly defaultBlackRender?: int--><!--Device-DngMetadata-readonly defaultBlackRender?: int-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## defaultCropOrigin

```TypeScript
readonly defaultCropOrigin?: number[]
```

默认裁剪区域的左上角坐标（x, y）。

**类型：** number[]

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly defaultCropOrigin?: double[]--><!--Device-DngMetadata-readonly defaultCropOrigin?: double[]-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## defaultCropSize

```TypeScript
readonly defaultCropSize?: number[]
```

默认裁剪区域的宽度和高度。

**类型：** number[]

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly defaultCropSize?: int[]--><!--Device-DngMetadata-readonly defaultCropSize?: int[]-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## defaultScale

```TypeScript
readonly defaultScale?: number[]
```

默认缩放比例。格式为[水平缩放比例, 垂直缩放比例]。

**类型：** number[]

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly defaultScale?: double[]--><!--Device-DngMetadata-readonly defaultScale?: double[]-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## defaultUserCrop

```TypeScript
readonly defaultUserCrop?: number[]
```

默认用户裁剪区域。

**类型：** number[]

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly defaultUserCrop?: int[]--><!--Device-DngMetadata-readonly defaultUserCrop?: int[]-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## dngBackwardVersion

```TypeScript
readonly dngBackwardVersion?: number[]
```

DNG文件向后兼容的最低版本号。

**类型：** number[]

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly dngBackwardVersion?: int[]--><!--Device-DngMetadata-readonly dngBackwardVersion?: int[]-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## dngPrivateData

```TypeScript
readonly dngPrivateData?: ArrayBuffer
```

厂商私有数据块。

**类型：** ArrayBuffer

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly dngPrivateData?: ArrayBuffer--><!--Device-DngMetadata-readonly dngPrivateData?: ArrayBuffer-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## dngVersion

```TypeScript
readonly dngVersion?: number[]
```

DNG图片的版本号。

**类型：** number[]

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly dngVersion?: int[]--><!--Device-DngMetadata-readonly dngVersion?: int[]-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## extraCameraProfiles

```TypeScript
readonly extraCameraProfiles?: number[]
```

额外相机配置文件索引列表。

**类型：** number[]

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly extraCameraProfiles?: int[]--><!--Device-DngMetadata-readonly extraCameraProfiles?: int[]-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## forwardMatrix1

```TypeScript
readonly forwardMatrix1?: number[]
```

第一前向变换矩阵。

**类型：** number[]

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly forwardMatrix1?: double[]--><!--Device-DngMetadata-readonly forwardMatrix1?: double[]-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## forwardMatrix2

```TypeScript
readonly forwardMatrix2?: number[]
```

第二前向变换矩阵。

**类型：** number[]

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly forwardMatrix2?: double[]--><!--Device-DngMetadata-readonly forwardMatrix2?: double[]-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## lensInfo

```TypeScript
readonly lensInfo?: number[]
```

镜头信息。

**类型：** number[]

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly lensInfo?: double[]--><!--Device-DngMetadata-readonly lensInfo?: double[]-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## linearResponseLimit

```TypeScript
readonly linearResponseLimit?: number
```

线性响应上限。

**类型：** number

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly linearResponseLimit?: double--><!--Device-DngMetadata-readonly linearResponseLimit?: double-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## linearizationTable

```TypeScript
readonly linearizationTable?: number[]
```

线性化查找表，用于将原始传感器值映射为线性光强度。

**类型：** number[]

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly linearizationTable?: int[]--><!--Device-DngMetadata-readonly linearizationTable?: int[]-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## localizedCameraModel

```TypeScript
readonly localizedCameraModel?: string
```

本地化后的相机型号名称。

**类型：** string

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly localizedCameraModel?: string--><!--Device-DngMetadata-readonly localizedCameraModel?: string-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## makerNoteSafety

```TypeScript
readonly makerNoteSafety?: boolean
```

EXIF MakerNote是否安全可保留。true表示安全，false表示不安全。

**类型：** boolean

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly makerNoteSafety?: boolean--><!--Device-DngMetadata-readonly makerNoteSafety?: boolean-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## maskedAreas

```TypeScript
readonly maskedAreas?: number[]
```

被遮蔽区域列表。

**类型：** number[]

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly maskedAreas?: int[]--><!--Device-DngMetadata-readonly maskedAreas?: int[]-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## newRawImageDigest

```TypeScript
readonly newRawImageDigest?: string
```

修改后原始图像数据的新MD5摘要。

**类型：** string

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly newRawImageDigest?: string--><!--Device-DngMetadata-readonly newRawImageDigest?: string-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## noiseProfile

```TypeScript
readonly noiseProfile?: number[]
```

噪声剖面参数。

**类型：** number[]

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly noiseProfile?: double[]--><!--Device-DngMetadata-readonly noiseProfile?: double[]-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## noiseReductionApplied

```TypeScript
readonly noiseReductionApplied?: number
```

已应用的降噪强度级别。

**类型：** number

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly noiseReductionApplied?: double--><!--Device-DngMetadata-readonly noiseReductionApplied?: double-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## opcodeList1

```TypeScript
readonly opcodeList1?: ArrayBuffer
```

第一操作码列表。

**类型：** ArrayBuffer

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly opcodeList1?: ArrayBuffer--><!--Device-DngMetadata-readonly opcodeList1?: ArrayBuffer-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## opcodeList2

```TypeScript
readonly opcodeList2?: ArrayBuffer
```

第二操作码列表。

**类型：** ArrayBuffer

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly opcodeList2?: ArrayBuffer--><!--Device-DngMetadata-readonly opcodeList2?: ArrayBuffer-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## opcodeList3

```TypeScript
readonly opcodeList3?: ArrayBuffer
```

第三操作码列表。

**类型：** ArrayBuffer

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly opcodeList3?: ArrayBuffer--><!--Device-DngMetadata-readonly opcodeList3?: ArrayBuffer-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## originalBestQualityFinalSize

```TypeScript
readonly originalBestQualityFinalSize?: number[]
```

原始最佳画质输出尺寸。

**类型：** number[]

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly originalBestQualityFinalSize?: int[]--><!--Device-DngMetadata-readonly originalBestQualityFinalSize?: int[]-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## originalDefaultCropSize

```TypeScript
readonly originalDefaultCropSize?: number[]
```

原始默认裁剪尺寸。

**类型：** number[]

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly originalDefaultCropSize?: double[]--><!--Device-DngMetadata-readonly originalDefaultCropSize?: double[]-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## originalDefaultFinalSize

```TypeScript
readonly originalDefaultFinalSize?: number[]
```

原始默认最终输出尺寸。

**类型：** number[]

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly originalDefaultFinalSize?: int[]--><!--Device-DngMetadata-readonly originalDefaultFinalSize?: int[]-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## originalRawFileData

```TypeScript
readonly originalRawFileData?: ArrayBuffer
```

原始RAW文件的完整数据。

**类型：** ArrayBuffer

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly originalRawFileData?: ArrayBuffer--><!--Device-DngMetadata-readonly originalRawFileData?: ArrayBuffer-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## originalRawFileDigest

```TypeScript
readonly originalRawFileDigest?: string
```

原始RAW文件数据的MD5摘要。

**类型：** string

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly originalRawFileDigest?: string--><!--Device-DngMetadata-readonly originalRawFileDigest?: string-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## originalRawFileName

```TypeScript
readonly originalRawFileName?: string
```

原始RAW文件名。

**类型：** string

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly originalRawFileName?: string--><!--Device-DngMetadata-readonly originalRawFileName?: string-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## previewApplicationName

```TypeScript
readonly previewApplicationName?: string
```

预览图生成应用程序名称。

**类型：** string

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly previewApplicationName?: string--><!--Device-DngMetadata-readonly previewApplicationName?: string-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## previewApplicationVersion

```TypeScript
readonly previewApplicationVersion?: string
```

预览图生成应用程序版本。

**类型：** string

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly previewApplicationVersion?: string--><!--Device-DngMetadata-readonly previewApplicationVersion?: string-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## previewColorSpace

```TypeScript
readonly previewColorSpace?: number
```

预览图色彩空间。

**类型：** number

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly previewColorSpace?: int--><!--Device-DngMetadata-readonly previewColorSpace?: int-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## previewDateTime

```TypeScript
readonly previewDateTime?: string
```

预览图生成时间。

**类型：** string

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly previewDateTime?: string--><!--Device-DngMetadata-readonly previewDateTime?: string-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## previewSettingsDigest

```TypeScript
readonly previewSettingsDigest?: string
```

预览图设置的MD5摘要。

**类型：** string

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly previewSettingsDigest?: string--><!--Device-DngMetadata-readonly previewSettingsDigest?: string-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## previewSettingsName

```TypeScript
readonly previewSettingsName?: string
```

预览图处理设置名称。

**类型：** string

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly previewSettingsName?: string--><!--Device-DngMetadata-readonly previewSettingsName?: string-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## profileCalibrationSignature

```TypeScript
readonly profileCalibrationSignature?: string
```

配置文件校准签名。

**类型：** string

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly profileCalibrationSignature?: string--><!--Device-DngMetadata-readonly profileCalibrationSignature?: string-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## profileCopyright

```TypeScript
readonly profileCopyright?: string
```

配置文件版权信息。

**类型：** string

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly profileCopyright?: string--><!--Device-DngMetadata-readonly profileCopyright?: string-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## profileEmbedPolicy

```TypeScript
readonly profileEmbedPolicy?: number
```

配置文件嵌入策略。

**类型：** number

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly profileEmbedPolicy?: int--><!--Device-DngMetadata-readonly profileEmbedPolicy?: int-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## profileHueSatMapData1

```TypeScript
readonly profileHueSatMapData1?: number[]
```

第一组色调/饱和度映射表数据。

**类型：** number[]

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly profileHueSatMapData1?: double[]--><!--Device-DngMetadata-readonly profileHueSatMapData1?: double[]-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## profileHueSatMapData2

```TypeScript
readonly profileHueSatMapData2?: number[]
```

第二组色调/饱和度映射表数据。

**类型：** number[]

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly profileHueSatMapData2?: double[]--><!--Device-DngMetadata-readonly profileHueSatMapData2?: double[]-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## profileHueSatMapDims

```TypeScript
readonly profileHueSatMapDims?: number[]
```

色调/饱和度映射表维度。

**类型：** number[]

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly profileHueSatMapDims?: int[]--><!--Device-DngMetadata-readonly profileHueSatMapDims?: int[]-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## profileHueSatMapEncoding

```TypeScript
readonly profileHueSatMapEncoding?: number
```

色调/饱和度映射表编码方式。

**类型：** number

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly profileHueSatMapEncoding?: int--><!--Device-DngMetadata-readonly profileHueSatMapEncoding?: int-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## profileLookTableData

```TypeScript
readonly profileLookTableData?: number[]
```

色彩表数据。

**类型：** number[]

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly profileLookTableData?: double[]--><!--Device-DngMetadata-readonly profileLookTableData?: double[]-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## profileLookTableDims

```TypeScript
readonly profileLookTableDims?: number[]
```

ProfileLookTableData的维度。

**类型：** number[]

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly profileLookTableDims?: int[]--><!--Device-DngMetadata-readonly profileLookTableDims?: int[]-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## profileLookTableEncoding

```TypeScript
readonly profileLookTableEncoding?: number
```

色彩表编码方式。

**类型：** number

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly profileLookTableEncoding?: int--><!--Device-DngMetadata-readonly profileLookTableEncoding?: int-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## profileName

```TypeScript
readonly profileName?: string
```

色彩配置文件名称。

**类型：** string

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly profileName?: string--><!--Device-DngMetadata-readonly profileName?: string-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## profileToneCurve

```TypeScript
readonly profileToneCurve?: number[]
```

配置文件色调曲线。

**类型：** number[]

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly profileToneCurve?: double[]--><!--Device-DngMetadata-readonly profileToneCurve?: double[]-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## rawDataUniqueID

```TypeScript
readonly rawDataUniqueID?: string
```

原始图像数据的唯一标识符。

**类型：** string

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly rawDataUniqueID?: string--><!--Device-DngMetadata-readonly rawDataUniqueID?: string-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## rawImageDigest

```TypeScript
readonly rawImageDigest?: string
```

原始图像数据的MD5摘要。

**类型：** string

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly rawImageDigest?: string--><!--Device-DngMetadata-readonly rawImageDigest?: string-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## rawToPreviewGain

```TypeScript
readonly rawToPreviewGain?: number
```

主RAW图与预览图之间的增益比。

**类型：** number

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly rawToPreviewGain?: double--><!--Device-DngMetadata-readonly rawToPreviewGain?: double-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## reductionMatrix1

```TypeScript
readonly reductionMatrix1?: number[]
```

第一校准光源下的降维矩阵。

**类型：** number[]

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly reductionMatrix1?: double[]--><!--Device-DngMetadata-readonly reductionMatrix1?: double[]-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## reductionMatrix2

```TypeScript
readonly reductionMatrix2?: number[]
```

第二校准光源下的降维矩阵。

**类型：** number[]

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly reductionMatrix2?: double[]--><!--Device-DngMetadata-readonly reductionMatrix2?: double[]-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## rowInterleaveFactor

```TypeScript
readonly rowInterleaveFactor?: number
```

行交织因子。

**类型：** number

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly rowInterleaveFactor?: int--><!--Device-DngMetadata-readonly rowInterleaveFactor?: int-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## shadowScale

```TypeScript
readonly shadowScale?: number
```

阴影区域缩放因子。

**类型：** number

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly shadowScale?: double--><!--Device-DngMetadata-readonly shadowScale?: double-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## subTileBlockSize

```TypeScript
readonly subTileBlockSize?: number[]
```

图像分块存储，定义块的长和宽。

**类型：** number[]

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly subTileBlockSize?: int[]--><!--Device-DngMetadata-readonly subTileBlockSize?: int[]-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## uniqueCameraModel

```TypeScript
readonly uniqueCameraModel?: string
```

相机的唯一型号标识，用于区分不同设备。

**类型：** string

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly uniqueCameraModel?: string--><!--Device-DngMetadata-readonly uniqueCameraModel?: string-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## whiteLevel

```TypeScript
readonly whiteLevel?: number[]
```

白电平，表示传感器最大有效输出。

**类型：** number[]

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DngMetadata-readonly whiteLevel?: double[]--><!--Device-DngMetadata-readonly whiteLevel?: double[]-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

